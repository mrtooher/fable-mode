SPEC (the question the memo answers):
Our head of growth presented a customer lifetime value of $15,000, calculated by dividing our $180 average monthly revenue per customer by our 1.2% monthly churn rate, and wants to raise what we're willing to spend to win a new customer to $5,000. We've only been selling for three years, so no customer has actually stayed with us longer than 36 months. How far should I trust that $15,000, and what would a more honest estimate look like?

MEMO:
## Recommendation

Trust the arithmetic ($180 ÷ 1.2% = $15,000), not the decision it's being used for: the formula bets on 47 of its 83 assumed months of customer life with zero customers behind them, prices in revenue instead of profit, and ignores the time value of money. Don't set the CAC ceiling at $5,000 off this number. Set it near what a 24-month, margin-adjusted payback actually supports — roughly $2,800–3,000 at a plausible 75–80% gross margin — and revisit within weeks once you've pulled the cohort data the company already has.

## Why

$180 ÷ 1.2% is correct arithmetic, but it's the mean of a model, not a measurement. Dividing revenue by a monthly churn rate assumes every customer carries the same 1.2% chance of leaving every month, forever — mathematically identical to assuming an average customer lifetime of 1/0.012 = 83 months, nearly seven years. The company has sold for 36 months total, so no customer has had the chance to reach even half that assumed lifetime.

That gap is not, by itself, proof the number is too high. "No customer has passed 36 months" would be true of a three-year-old company at any real retention rate, good or bad — it doesn't say which way the true curve bends. What it does mean: roughly 47 of the formula's 83 assumed months are extrapolation with no customer behind them, and an unproven extrapolation should not be spent against, whether or not it later turns out to be right.

Two other effects push in a direction that isn't in doubt, because they can only shrink the number, never grow it: the formula compares a hard cash outlay (the $5,000 CAC) to gross revenue rather than gross profit, and it applies no discount for time, so a dollar collected in year six counts the same as a dollar collected next month.

What the company's own history actually supports, using only the given numbers: applying the same 1.2% rate to the 36 months that have actually elapsed, instead of running it to infinity, gives cumulative revenue per customer of about $5,300 — roughly a third of $15,000, before any cost to serve. That's close to a ceiling on what's demonstrated, not a floor — capping value at zero beyond month 36 is also an assumption (it says nobody who has paid for three straight years will pay a fourth), just a more conservative one than assuming 1.2% holds for 83 months. Against a $5,000 CAC: no customer relationship this company has ever had has generated enough revenue, let alone enough profit, to fully repay it. Worth noting: $5,000 is exactly $15,000 ÷ 3 — a standard 3:1 LTV:CAC guardrail applied on top of the uncorrected, revenue-basis, infinite-horizon number. The same guardrail applied to the bounded $5,300 figure would put the ceiling in the low thousands, not $5,000.

## What to do

A more honest estimate, in order of rigor:

1. **Cheapest bound, available now:** cap the churn projection at the 36 months actually observed instead of running it to infinity. On the given numbers that's about $5,300 in cumulative revenue per customer, before cost to serve. Treat it as a ceiling on what's proven, not a target.
2. **Best return on effort:** pull existing billing data and build a cohort (signup-month) retention curve — the share of each monthly cohort still paying at months 1 through 36, by acquisition channel — and compare it to what flat 1.2% churn predicts (about 86% active at 12 months, 75% at 24, 65% at 36). One analyst, roughly 1–5 days, no new data collection. If the actual curve tracks the prediction and holds or improves in the most recent observed months, that's a real point in favor of trusting the longer-run number; if churn rises with tenure or recent cohorts run hotter than 1.2%, that's a point against it. Have finance, or whoever doesn't benefit from a higher ceiling, run this — not the team proposing it.
3. **Reprice on margin:** swap revenue for gross profit, and discount anything projected past month 36. Real margin isn't given here; for calibration, at a representative 75–80% margin the 36-month-capped figure becomes roughly $4,000–4,200 rather than $5,300, and discounting trims it further. Replace the illustrative margin with the real one as soon as you have it.
4. **Set the ceiling from a payback test, not a lifetime-value guess:** the cost recoverable, in gross profit, within a horizon you're willing to wait — 18–24 months is a common bar for a three-year-old company. On these numbers that lands near $2,800–3,000, using the 75–80% margin assumption above. Start there and raise it, channel by channel, as each cohort's real payback clears the bar.

Run step 2 before the next round where the CAC ceiling gets decided. It's days of work against data already owned, and it's the one step that moves this from "somewhere between a third and a half of $15,000" to an actual, company-specific number.

## Risks of this plan

Holding the ceiling near $2,800–3,000 while the retention curve gets pulled has a real cost if the underlying retention is as good as 1.2% implies: competitors may win durable customers this company would otherwise have captured, and that loss won't appear in any report the way an overspend would — invisible, not absent. The 36-month cap used to get there is itself an assumption, not a measurement — it values every customer who's paid for three straight years at zero for a fourth, which is arbitrary in the opposite direction from assuming 1.2% holds for 83 months. The 75–80% margin used throughout is illustrative, not this company's real number; if true margin is lower, even $2,800–3,000 is too generous, and if churn is falling with tenure or older cohorts show revenue expansion, the evidence-based ceiling could clear $5,000 faster than this plan assumes. If the 1.2% figure is blended across annual contracts, or is a net number offset by expansion revenue from survivors, true monthly churn for a typical customer could run higher than 1.2%, which would make even the $5,300 bound too generous.

Cost of being wrong: this plan is cheap and fully reversible — a few analyst-days, and at worst a few months of slower-than-optimal growth while the data comes in, with the ceiling free to move either direction once real cohort data lands. Approving $5,000 now on the uncorrected number is the harder position to unwind: it commits real cash per customer for years before any cohort will have lived long enough to confirm or deny the assumption it rests on.

## Strongest counter-position

The case against this caution: leaning on "no customer has stayed longer than 36 months" as the reason to distrust $15,000 is weaker than it sounds. That fact "doesn't show that customers leave. It just means the company is three years old, and it would be equally true if every customer you ever signed were still paying." If the oldest cohorts, once actually pulled, show churn flat or falling in months 25–36 with margins holding up, the long lifetime behind the growth head's number is the most defensible part of the $15,000, not the weakest — and freezing the ceiling at $2,800–3,000 is itself an unforced, costly error: the same mistake being corrected here, pointed the other way, and one that never shows up on a P&L the way overspending does. On this view the fix isn't a lower ceiling, it's who sets it and on what evidence: put the retention analysis under finance rather than growth, and let each channel's own payback data set its own number instead of applying either figure company-wide.

This wins if the retention pull (What to do, step 2) comes back with hazard flat or declining by tenure and margins intact — at that point the evidence should set the ceiling, and it could reasonably clear $3,000 sooner than this memo's default assumes.

## Confidence

High — the arithmetic ($180 ÷ 1.2% = $15,000, its implied ~83-month lifetime, and the ~$5,300 36-month-capped figure) and the direction of the margin and discounting corrections: both follow from the given numbers and standard math, independent of what the true churn curve turns out to be, since margin is always below 100% and future cash is always worth less than cash today.

Medium — the specific recommended ceiling (~$2,800–3,000): it rests on an illustrative, unconfirmed margin (75–80%) and an 18–24 month payback bar that's a reasonable default, not a given fact. It moves once real cost-to-serve and the business's actual tolerance for payback time are plugged in.

Low / open — whether the true churn hazard rises, falls, or stays flat with tenure, and whether 1.2% is a clean, like-for-like monthly figure. Nothing in the question resolves either, and both are exactly what the retention-curve pull would settle.
