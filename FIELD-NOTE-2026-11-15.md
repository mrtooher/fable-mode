# Field note — Fable Mode Pro vs. an unaided run, one real session — 2026-11-15

**This is not a benchmark.** It is one working session, n=1, with no control arm. It
records what the Pro loop caught on a real task that the same model, working without the
skill earlier in the same session, did not. Read the "What this does not show" section
before quoting it.

**Short version: the run logged 14 failed checks, four of them
material overstatements in the final write-up that the main thread's own self-review had
passed. The checker panel cost about 421k subagent tokens and the run took roughly
20 minutes.**

## Setup

- Model on the main thread: Claude Fable 5.2 (frontier calibration; workers and checkers
  capped at Opus, per family v6.4).
- Skills: `fable-mode-pro` Pro v1.3 on family v6.4, with `fable-checks`, `fable-audit`,
  `double-check` and `execution-guardrails`. (The Pro add-on skills are not in this repo
  as of this note.)
- Task domain: financial analysis. Five monthly department P&L reports (PDF), two
  earlier reconciliation files, a spreadsheet deliverable and a written set of findings
  on a specific accounting question.
- The underlying documents are confidential. Every organization name, dollar figure and
  event name has been removed from this note. Counts of checks, tokens and errors are
  exact.

| | Unaided phase | Pro phase |
|---|---|---|
| Trigger | plain requests, no fable skill named | `/fable-mode-pro` |
| Deliverable | reasoning + an email draft, then a 4-tab spreadsheet | 12-tab source workbook, findings, `VERIFY.md` |
| Checks written down | none (ad hoc: formulas read back, arithmetic run in a script) | 44 rows in `VERIFY.md` |
| Fresh-agent checks | none | 1 Haiku + 1 Sonnet panel, 1 Sonnet re-check round |
| Checker tokens | 0 | 421,098 (154,893 + 131,065 + 135,140) |
| Wall time | a few minutes per answer | roughly 20 minutes |

## What the Pro phase caught

44 logged checks: 30 PASS, 14 FAIL, 0 UNVERIFIABLE. Every FAIL row has a later row that
fixes or re-runs it.

| Caught by | What | Count |
|---|---|---|
| Stage 1 reconciliation recipe (printed subtotals recomputed from their lines) | A discrepancy **in the source documents**: one expense line is printed but not added into its subtotal. Logged as a finding, not a data error, after a second check isolated it. | 1 |
| `recalc.py` on the built workbook | A text label beginning with `=` was being read as a formula (`#VALUE!`). | 1 |
| Read-back of the workbook's own check tab | A check whose tolerance was wider than the value it tested, so it reported the wrong result on small amounts. | 1 |
| Fresh Sonnet, errors-first, on the findings | **Four material errors** and five minor ones (below), logged as 8 rows. | 8 |
| Dissent check | The findings recommended a test without saying how that test could mislead. | 1 |
| Sonnet re-check round | One remaining wording problem: a source's own "verified" flag had been reported as "unconfirmed". | 1 |
| Main thread re-reading its own log | A re-check `grep` whose pattern was too broad, first logged as PASS (see below). | 1 |

The four material errors, described generically:

1. A percentage stated as fact that rested on an inferred posting the source only marked
   as likely.
2. A figure for *all* items generalized to the *subgroup* the question was actually
   about, when the same document showed the subgroup behaving differently.
3. A proposed test whose stated conclusion did not follow: the source data showed two
   other causes that produce the same result.
4. A premise ("no change happened in this period") that no source established.

The main thread had run step 4 (self-critique) on that draft immediately before the
panel and listed none of the four.

### Two things that cut the other way

- **The Haiku mechanical panel found nothing.** 20 claims, 20 confirmed, 0 refuted, for
  154,893 tokens. Either the stage checks had already done its job, or the claims were
  easy. This run cannot say which.
- **The main thread broke the audit rule once.** One check-log row was written as PASS
  in the same command that ran the check, before its output was read. The output showed
  a (benign) match. The row was corrected in place from the real output and re-run as a
  new row. "Log as you go" is easy to turn into "log as you launch".

### One gap in the unaided phase, found afterward

An unaided answer asked for a prior-year document "for a like-for-like comparison",
which assumed an annual event fell in the same month the year before. Nothing on file
established that, and nothing checked it. It was noticed and neutralized later, during
the Pro phase's rebuild.

## What this does not show

- **Not controlled.** The Pro phase had a broader request ("more info"), more source
  files, and came second, after the model had already worked the material. Depth of
  output cannot be credited to the skill.
- **Not Pro vs. regular fable-mode.** Regular `fable-mode` was not run. The fresh-checker
  panel that caught the write-up errors is step 5 of regular fable-mode too. What
  Pro adds on top is named recipes for each stage check and the `VERIFY.md` record.
  Of the 14 failures, the three workbook and source-document catches came from recipe
  checks; whether an improvised check would have caught them is untested.
- **Not a correctness score.** There was no answer key. "14 failed checks" counts problems
  found, not problems that exist.
- **One model, one task, one session.**

## Read

Consistent with the benchmark rounds in this repo: on a frontier model the loop does not
obviously change what the model *can* produce. Here it changed what got *shipped*,
because a reader with no stake in the draft re-derived its claims. The cost was real:
about 421k checker tokens for one deliverable. Worth it for work that goes to someone
else to act on. Not for a quick answer.
