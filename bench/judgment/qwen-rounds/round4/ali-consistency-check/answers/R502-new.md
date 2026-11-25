# arm: wise-men-flash (working tree, SKILL.md 0.2.0 candidate) | question: R502 | orchestrator: general-purpose/sonnet | run: 2026-10-22 (consistency check, PLAN.md rules)

## Recommendation

The freeze is moving risk into January and concentrating it. It stops deploys but not merging, so two weeks of changes from 60 engineers reach production together as one batch. That batch has never run together under production conditions, and it is hard to diagnose or roll back. Keep the freeze, which may protect December, but change how it ends: release the backlog in small, ordered, separately revertible slices once authors and on-call are back. First, have one engineer spend one to three days checking this against your last three Januaries' incident records. The facts you gave do not separate the batch from other causes that also recur on the calendar.

## Why

The freeze stops the part of the process that gives feedback and leaves the part that creates risk running. Deploy, observe and revert is how a team learns a change is bad while it is still small. Merging continues, so changes keep arriving with no production feedback for two weeks. They are usually tested against main, not against production's config, data and flag state. Some are reviewed against a main that kept moving underneath them.

Then the whole batch hits production at once, and three things get worse in a way individual changes would not cause:
- **Interactions:** the number of pairs of changes that could interact grows with the square of the number of changes, and nobody tested those combinations together.
- **Diagnosis and rollback:** a bad release of 3 changes bisects in minutes. A bad release of dozens or hundreds has many candidate causes, and rollback is all-or-nothing. Good changes get reverted with the bad one and reshipped as a second risky event.
- **Attention:** authors merged weeks ago, some are typically on leave, and on-call is typically thin in the first days of January. Your own roster will show whether that holds.

This is why every review blames a different bug. Each review finds a real proximate cause. The shared cause is one level up: why did that bug reach production inside a batch too big to attribute? A review that stops at the triggering bug cannot see that, and a large batch produces many unrelated surface bugs. Lower January traffic fits this too. It makes load an unlikely driver, and Google's SRE book reports that roughly 70% of outages are due to changes in a live system (sre.google/sre-book/introduction).

Is the freeze protecting you? Possibly in December, when traffic is higher and staffing thinner, but you have not said what December looks like. Moving risk from a high-traffic month to a low-traffic one can be a good trade even if January incidents rise. So judge the freeze by what outages cost (revenue, users affected), not by January's count. What you have is the moved risk plus a concentration that makes it harder to attribute and slower to fix.

The batch is the leading explanation, not a proven one. The facts given cannot separate it from three others that also recur on the calendar:
- **Year-boundary faults:** January 1 partition rollovers, annual certificate, token or licence expiry, annual jobs, "current year" assumptions.
- **Drift in the first post-freeze build:** unpinned base images and transitive dependencies, plus infrastructure work, migrations and patches held back until after the freeze.
- **Slower response:** thin on-call and lost context lengthen outages without adding faults.

## What to do

1. **Now, one engineer, one to three days, finished before the freeze starts.**
   - For every incident in the last three Januaries, record:
     - the merge date of the change that caused it;
     - its first production deploy date;
     - the trigger type (code, date or expiry, dependency or infrastructure, other);
     - time to restore against that year's median;
     - the size of the first post-freeze deploy against a normal week.
   - Check whether incidents begin at the first post-freeze release and taper in the days after it. Check whether the cluster moved in any year the freeze lift date moved.
   - Decision test: if a clear majority are freeze-window merges first shipped in the post-freeze release and cluster in the days after it, the batch diagnosis stands. If most predate the freeze or are date-, dependency- or response-driven, leave the freeze policy alone and fix those instead.
2. **Permanently, starting now.** Add merge date, deploy date, trigger type and deploy size as required fields in every incident review. Have someone read a whole year's reviews together each quarter, so a pattern like this shows up in one year, not three.
3. **Whatever the test shows, before the freeze.**
   - Run a year-boundary check in early December (expiries, partitions, annual jobs, date logic).
   - Pin dependencies and base images through the freeze and the first January builds.
   - Audit what the freeze actually covers, since config, infrastructure changes, flag flips and migrations may still be changing or piling up.
4. **If the test supports the batch diagnosis, decide these changes at least a month before the freeze starts.**
   - Do not let the pile sit untested. Either hold non-urgent merges in a queue and land them in ordered slices at the thaw, or keep merging but deploy main continuously to a production-like environment with production config and replayed or synthetic traffic. Urgent fixes keep your existing emergency-change path. Moving the pile from main into long-lived branches only relabels it and stores up merge conflicts.
   - Thaw in slices: lowest risk first, each independently revertible, each with a soak period, sized like a normal week's deploy. Start only when authors and on-call are back. Ship database schema changes as their own slices with a rollback plan, since stacked migrations can make rollback impossible. Ship held-back infrastructure work and patches as their own slices, not alongside code.
   - Because January traffic is low, canary releases have few requests to judge by. Alert on absolute error counts or add synthetic traffic.
5. **Stop or escalate.** After the first season with a staged thaw, compare early-January incident count and time to restore with the previous three years. If the cluster is unchanged with small slices, the batch was not the main cause. Move to the year-boundary, drift and staffing causes and stop reworking the freeze.

## Risks of this plan

- Loosening the freeze would move change risk into December's peak traffic and thin staffing. If calendar-triggered faults dominate, it would leave January untouched, so both months could get worse. This plan adds no December deploys. Its December changes (queued merges or a production-like environment, pinning, an audit) add checks, not releases.
- Queuing merges and thawing in slices delays freeze-period work reaching customers by days and can add merge conflicts. A staged thaw also puts more release events in the week people return.
- Incident records may be too thin to link causes to merge dates, so the check could be inconclusive. If so, run one staged thaw anyway with the new fields recorded. It is cheap and reversible.
- Waiting has a cost: three Januaries in a row make a fourth likely if nothing changes, and the records check costs only days.
- Cost of being wrong: the checks, record fields, pinning and staged thaw can all be dropped next year at the price of a few days' delay on freeze-period work. Two outcomes are hard to undo. One is a customer-facing December outage, which the plan avoids by adding no December deploys. The other is a schema migration that cannot be rolled back, which is why migrations ship as their own slices with a rollback plan. If the counter-position below is right, you lose days of delay and some process effort, and the same records point you to the date, dependency or staffing fixes.

## Strongest counter-position

The batch is not the main cause, and the freeze is not what is hurting you. The popular answer, that two weeks of merged code ships at once, is plausible and fits the general finding that outages follow change. But none of the stated facts prove it. A recurring window on the calendar is just as well explained by faults that fire whether or not there is a freeze: year-boundary expiries and annual jobs, drift in the first post-freeze build, and a thinned-out, out-of-context on-call that lengthens outages without adding faults. A big batch predicts "a different bug each time", and so does every one of those. If these dominate, restructuring the freeze buys nothing in January and adds change risk in December's peak traffic and thin staffing, so both months get worse. This wins if most blamed changes were merged before the freeze or were already running in December. It also wins if the bugs are date-, expiry- or dependency-triggered, if incidents do not start at the post-freeze release and taper off, or if January time to restore rather than incident count is what is unusual. The records check in step 1 is the evidence that would show it.

## Confidence

- **High:** the freeze stops deploys but not change, so the backlog ships together unless you intervene. Large batches are harder to diagnose and roll back and carry untested interactions (mechanics, and your own description).
- **Medium:** the batch is the main cause of your Januaries. It fits every stated fact, but so do the calendar-driven alternatives. One check, merge date against deploy date, settles most of it.
- **Medium:** a staged thaw reduces January incidents. It helps under the batch and drift explanations, not under year-boundary faults or staffing.
- **Low:** the freeze nets out as a protection for December, since December's outage cost is not given.
- **Material unknowns:**
  - what the freeze covers beyond application deploys (config, infrastructure, flags, migrations);
  - how the post-freeze release is staged today;
  - early-January staffing;
  - whether "worst" means incident count or minutes down;
  - December's outage record.
