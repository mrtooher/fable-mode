# Worked example: the loop catching what one-shot misses

A small, real-shaped task, done two ways. The point is step 3: the failable check
catches the error before it ships.

## Task

"Add a `/api/usage` endpoint that returns this month's API call count for the
authenticated user."

## One-shot attempt (no loop)

The model reads the request, writes the handler, returns it:

```js
// looks correct, ships
export async function GET(req) {
  const user = await getUser(req);
  const count = await db.calls.count({
    where: { userId: user.id, createdAt: { gte: startOfMonth() } }
  });
  return Response.json({ count });
}
```

It compiles and a reviewer would nod. It is wrong: `getUser` returns `null` for an
unauthenticated request, so `user.id` throws and the endpoint 500s instead of 401-ing.
The happy path was the only path tested, by eye, which is not a test. The bug surfaces
in production the first time an expired session hits it.

## Same task through the loop

**Step 1 — stage map**
```
Stage 1: Read auth middleware + db schema → confirm getUser contract, call table shape
Stage 2: Write handler → endpoint returns count for authed user
Stage 3: Write tests → authed returns count; unauthed returns 401; month boundary correct
```

**Step 2 — delegation check**
Single coherent change, no independent sub-work. No subagents. Sequential.

**Step 3 — the failable check (this is where it's caught)**
Tests written before calling it done:

```js
test('unauthenticated request returns 401', async () => {
  const res = await GET(mockReq({ session: null }));
  expect(res.status).toBe(401);   // FAILS on the one-shot version — it 500s
});
```

The test fails. The model reads `getUser`, sees it returns `null`, adds the guard:

```js
const user = await getUser(req);
if (!user) return new Response('Unauthorized', { status: 401 });
```

Test passes. Now it ships.

## Why the loop caught it

The stage map alone would not have caught the null. The test could fail, so it found the
case the eye missed. A self-reflective "does this look right?" would have answered "yes"
and shipped the 500, because the code *does* look right.

Step 3 being a check that can fail, rather than a question the model asks itself, is the
entire point.

---

# Worked example 2: research claim that "looks right" but isn't

Same structure. Different domain. The failable check here is tracing a claim to a source
actually read, not assumed.

## Task

"Write a summary of when to use connection pooling vs. single connections in PostgreSQL."

## One-shot attempt (no loop)

The model writes from training data:

> Connection pooling is essential for high-throughput applications. The PostgreSQL
> documentation recommends using PgBouncer for production deployments with more than
> 100 concurrent connections, noting that each connection consumes approximately 10 MB
> of memory.

It reads well and sounds authoritative. Two problems: PostgreSQL's documentation does not
recommend PgBouncer specifically (PgBouncer is a third-party tool), and the "10 MB per
connection" figure is a rough community estimate that varies widely by workload. It is
not a number the official docs state. The model presented community knowledge as
official documentation. A reviewer skimming this would nod and move on.

## Same task through the loop

**Step 1 — stage map**
```
Stage 1: Read PostgreSQL official docs on connection handling → confirmed facts only
Stage 2: Read PgBouncer docs separately → what it claims about itself
Stage 3: Write summary → distinguish official guidance from community practice
```

**Step 2 — delegation check**
Stages 1 and 2 are independent reads. If subagent tooling available, run concurrently.
Otherwise sequential.

**Step 3 — the failable check (this is where it's caught)**
Each load-bearing claim must trace to a source actually read:

- "PostgreSQL documentation recommends PgBouncer" → search PostgreSQL docs for
  "PgBouncer." Not found. Claim fails. PgBouncer is third-party. PostgreSQL docs
  discuss `max_connections` but do not recommend a specific pooler.
- "10 MB per connection" → search PostgreSQL docs for memory per connection. No specific
  figure given. The number comes from community blog posts and varies by
  `work_mem`, `shared_buffers`, and query complexity. Must be flagged as estimate, not
  official.

The model rewrites:

> PostgreSQL allocates a backend process per connection. The official documentation
> does not prescribe a specific pooler, but notes that `max_connections` defaults to 100.
> Community estimates for per-connection memory range from 5–15 MB depending on workload
> configuration. PgBouncer is a widely-used third-party pooler but is not part of
> PostgreSQL itself.

Now every claim traces to a real source. Shipped.

## Why the loop caught it

The stage map did not catch the bad attribution. Actually searching the docs for the
specific claims found that the source did not say what the model said it said.

Research verification reduces to one question: did you read the source, or assume it?

---

# Worked example 3: data analysis with hidden nulls

## Task

"Calculate the average response time per region from the API logs table."

## One-shot attempt (no loop)

```sql
SELECT region, AVG(response_time_ms) as avg_ms
FROM api_logs
GROUP BY region
ORDER BY avg_ms DESC;
```

It returns clean numbers and ships into the report. Problem: 12% of rows have
`response_time_ms = NULL` because timeout requests never recorded a duration. `AVG`
silently skips nulls. The "average" for the US-East region is actually the average of
*successful* requests only. The slowest region looks like the fastest because its
timeouts disappeared from the calculation.

## Same task through the loop

**Step 1 — stage map**
```
Stage 1: Profile the data → row counts, null rates, outliers per column
Stage 2: Write query → average response time, accounting for data quality findings
Stage 3: Validate → compare row counts in vs. rows used in AVG
```

**Step 3 — the failable check**
Data quality assertion before computing:

```sql
SELECT region,
       COUNT(*) as total,
       COUNT(response_time_ms) as has_value,
       COUNT(*) - COUNT(response_time_ms) as nulls,
       ROUND(100.0 * (COUNT(*) - COUNT(response_time_ms)) / COUNT(*), 1) as null_pct
FROM api_logs
GROUP BY region;
```

Result shows US-East has 23% nulls. Check fails. Cannot report an average that silently
drops a quarter of requests. The model adds a `COALESCE` approach or reports the null
rate alongside the average so the reader knows what the number actually means.

## Why the loop caught it

The query was syntactically correct. The data quality assertion, a check that runs
against the actual data, exposed that a correct query and a correct answer are not the
same thing.

---

# Worked example 4: long-running task with no done criteria

## Task

"Refactor the notification system to support multiple channels (email, SMS, push).
This will take multiple sessions."

## One-shot attempt (no loop)

Session 1: Model refactors the email sender into a base class, adds an SMS subclass.
Commits. Stops.

Session 2: User returns. Model does not remember what was done or what remains. Reads
the code, guesses where it left off. Adds push notifications. Duplicates some work from
session 1. Misses that the retry logic was only wired to email, not the new channels.
Ships with SMS and push silently dropping failed sends.

## Same task through the loop

**Step 1 — stage map with done criteria**
```
Stage 1: Define channel interface → base class + method contract documented
Stage 2: Email channel → existing sender implements interface, tests pass
Stage 3: SMS channel → new sender implements interface, tests pass
Stage 4: Push channel → new sender implements interface, tests pass
Stage 5: Retry logic → all channels retry on failure, tests cover retry for each
Done: all five stages pass their checks. Each channel sends, fails, and retries.
```

**Work log (maintained across sessions)**
```
Session 1: Completed stages 1-2. Email refactored. Interface defined.
           Decision: retry logic stays as its own stage, not per-channel.
           Open: SMS provider SDK not yet chosen.
```

**Session 2 start — re-read work log before touching anything.**
Model knows exactly what is done, what remains, and what decisions were made. Picks up
at stage 3. No duplicated work. No guessing.

**Step 3 — the failable check**
Stage 5 check: "tests cover retry for each channel." Test for SMS retry fails. Retry
was only wired to the email channel. Caught before shipping.

## Why the loop caught it

The work log prevented wasted effort in session 2. The done criteria prevented shipping
when retry was missing. Without written done criteria, "is it done?" is a feeling. The
checklist that says "retry test for SMS: not passing" does not care how the model feels.
