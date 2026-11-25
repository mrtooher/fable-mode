# arm: wise-men-flash (working tree, SKILL.md 0.2.0 candidate) | question: R504 | orchestrator: general-purpose/sonnet | run: 2026-10-22 (consistency check, PLAN.md rules)

## Recommendation

Treat the $15,000 as a best-case, revenue-based model output, not a measured value. Don't raise the acquisition ceiling to $5,000 on it. Replace it with an estimate built from your own cohort billing records, on gross margin, in three labelled parts. The first is what has actually been observed to month 36. The second is a separately labelled tail, capped at 3 to 5 years and discounted. The third is the value of the marginal customer the extra spend would buy. On illustrative placeholders (75% gross margin, 10% annual discount rate), the discounted margin value runs from about $3,500 (first 36 months) to about $6,800 (an endless tail), against $15,000.

## Why

Revenue ÷ churn is a legitimate shortcut, but it is only right if four things hold at once:
- Every customer pays $180 for life.
- 1.2% is a constant exit rate at every tenure and for every future customer.
- Revenue is as good as profit.
- A dollar in year seven equals a dollar today.

Your own numbers show how much rides on that. At constant 1.2% churn the average customer stays 83 months (6.9 years), which is 2.3 times the longest tenure you have seen. About 65% of the $15,000 (roughly $9,700) comes from month 37 onward. Only about $5,300 (35%) falls inside the first 36 months, and even that is the formula's own prediction rather than a measurement. What you have actually observed sits in your billing records.

"Nobody past 36 months" tells you how old the company is, not how long customers stay. If 1.2% held, about 65% of your oldest customers would still be paying at month 36. So the right tool is survival analysis, which treats still-active customers as unfinished rather than churned. A hard cut-off at month 36 is the wrong tool.

Per acquired customer, with the formula's constant 1.2% churn (margin and discount rate are placeholders, not your numbers; 75% gross margin is unverified for your business):

| Basis | 36 months | 5 years | Endless |
|---|---|---|---|
| Revenue, undiscounted (the $15,000 basis) | $5,287 | $7,730 | $15,000 |
| 75% margin, undiscounted | $3,965 | $5,798 | $11,250 |
| 75% margin, 10% discount | $3,498 | $4,763 | $6,813 |

Against a $5,000 spend, LTV:CAC is:
- 3.0 on the endless revenue figure.
- 2.25 on undiscounted margin.
- 1.36 on discounted margin.
- 0.70 on discounted margin over the observed 36 months.

The 3.0 needs revenue-as-profit, an infinite horizon, no discounting and constant churn all at once. Payback tells the same story. After churn, $5,000 takes about 34 months to recover on revenue and about 49 months at 75% margin, and only about 40% of it ($2,023) comes back in revenue in the first year. Recovering $5,000 within the 36 months you have watched would need roughly 95% margin on these numbers.

Two more things make the $15,000 flatter this particular decision. It describes the average customer, while a higher ceiling buys the marginal one, from pricier, lower-intent channels whose churn and revenue are likely worse than the blend (unverified for your channels; step 2 below checks it). And an allowable-CAC number can act like a price: once $5,000 is allowed, bids, agency fees and commissions may drift toward it, including on customers you win today for far less. The benefit of a higher ceiling shows up in this year's customer count, while the cash is tied up for years. So whoever wants the higher ceiling should not be the only one who builds the number.

## What to do

1. This week, hold the ceiling where it is. Don't announce $5,000 to channel owners or agencies.
2. Have someone who does not report to growth (finance or an analyst) spend 2 to 3 days on the existing billing records. They should produce:
   - How the 1.2% was computed (logo or revenue churn, blended or by cohort, over what window, monthly or annual contracts).
   - A survival curve for each monthly signup cohort and each acquisition channel, with still-active customers counted as unfinished.
   - Cumulative gross margin per acquired customer by month, by cohort and channel.
   - Churn by tenure band (months 1-3, 4-12, 13-24, 25-36), to see whether it falls, rises or stays flat with tenure.
3. Restate LTV as three lines. First, realized margin to month 36. Second, a tail extrapolated from the fitted curve, capped at 3 to 5 years and discounted, shown as low, base and high. Third, the marginal value of the channels the extra spend would reach. Quote it as a range with the gross-margin input stated.
4. Set the ceiling per channel by margin payback inside the observed window. On the placeholders, two rules of thumb put a blended ceiling at roughly $1,200 to $2,800. A 3:1 ratio on discounted margin LTV gives about $1,200 to $2,300. Recovering CAC from margin in 24 months gives about $2,800. Compare these with what you spend today.
5. Raise in capped steps, channel by channel, not straight to $5,000. Compare each step's new cohorts, at the same age, with earlier cohorts on retention and cumulative margin. Stop a step if they churn faster or accumulate margin slower.
6. $5,000 becomes defensible for a channel when its cohorts show at least $5,000 of cumulative gross margin per acquired customer by month 36. Accepting a longer payback is a separate bet that needs the curve to justify it. That means churn clearly falling below 1% after month 12, later cohorts matching earlier ones, and cash to carry the wait.
7. Time box: analysis in one week, ceiling decision two weeks from now. Revisit each quarter as the oldest cohorts age.

## Risks of this plan

Cost of waiting: if the tail is better than the formula assumes (see below), holding the ceiling forgoes customers on channels that would have paid back, and a competitor may win them. Capping and discounting the tail biases the estimate low, so present it as a low/base/high range rather than one haircut.

The 75% margin is a placeholder. Even at 100% margin and no discounting, revenue through month 36 ($5,287) only just covers $5,000. So payback rests entirely on the unobserved tail, whatever the margin.

The churn input itself could be off in either direction:
- If the 1.2% is net revenue churn (expansion hiding lost customers), or is flattered by annual-contract customers who can only leave at months 12, 24 and 36, customers are being lost faster than 1.2%. Every figure built on it, the $15,000 included, is then too high. Expansion revenue, which the formula omits, pushes the other way, which is one more reason to measure by cohort.
- If churn rises with tenure (renewal cliffs, customers outgrowing the product), the tail is worse than the formula says.

At $5,000, the average customer takes about 49 months to repay on margin at 75%. Scaling spend therefore scales burn before the tail is proven.

Cost of being wrong: holding and stepping up is reversible in spend terms within a quarter, because the ceiling can be raised any month. A $5,000 ceiling is hard to undo. The cash is spent, commissions and agency terms ratchet up, and you would only learn the truth about months 37 and beyond one to three years later. If the counter-position is right, the cost is a few weeks to a quarter of slower growth on channels that pay back. Raising those channels' ceilings once the cohort curves show it recovers the spend going forward. Customers a competitor wins in the meantime are not recovered.

## Strongest counter-position

Position: the tail is unobserved, not bad.

"Nobody past 36 months tells you how old the company is, not how long customers stay. About 65% of your oldest cohort should still be paying if 1.2% holds. Subscription survival curves typically flatten with tenure, because early churners leave first and the survivors are stickier (unverified for your base; check the tenure-band churn above). A constant-churn formula therefore often understates the tail, and expansion revenue is not in it at all. On revenue alone $15,000 could be about right or even low. A capped, discounted, margin-based figure will be biased low and hand growth a fair rebuttal. It also turns the argument onto a tail nobody can measure for years, while you under-invest in channels that do pay back."

It wins if the cohort data show three things:
- Monthly churn falling clearly below 1% after month 12.
- Later cohorts retaining as well as earlier ones.
- Gross margin around 80% or better, including expansion.

In that case a payback longer than 36 months becomes defensible and the ceiling can rise for those channels. The evidence is the churn by tenure band in months 13 to 36, which your billing records can show in days.

## Confidence

- High: the $15,000 is a best-case figure, about 65% of it beyond any observed tenure, and revenue payback on $5,000 is about 34 months after churn. This is arithmetic on your own numbers.
- Medium: the $3,500 to $6,800 range and the roughly 49-month margin payback. They move with gross margin, discount rate and how the 1.2% was measured.
- Low: whether the real tail is better or worse than constant 1.2%. Your cohort data can answer it.

Material unknowns: gross margin, how the 1.2% was measured, contract terms, current CAC, churn by tenure and channel, expansion revenue.
