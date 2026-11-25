# Round 4 packet for Qwen, part 1: the 8 memos and the reference key

These are 8 decision memos written by another AI skill (wise-men-flash). Each answers the question in its SPEC.
The REFERENCE KEY below is the list of internal contradictions found by that skill author's own two blind judges (both Claude Opus). A contradiction = a sentence that contradicts another part of the same memo, the question's stated facts, or the memo's own numbers. j1 and j2 are the two judges. Some contradictions were found by both judges.


---

## Memo 1

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

---

## Memo 2

SPEC (the question the memo answers):
We freeze production deploys for the last two weeks of December, and three years in a row, the first two weeks of January have been our worst stretch for outages, even though January traffic is lower than December's. Our 60 engineers keep merging code during the freeze and it all ships once the freeze lifts, but each incident review blames a different specific bug, so nobody treats it as one pattern. What is actually going wrong, and is the freeze protecting us or just moving the risk to January?

MEMO:
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

---

## Memo 3

SPEC (the question the memo answers):
My boss is retiring next year and has offered to sell me the landscaping business I've worked at for eight years, which would take most of our savings plus a bank loan, and my partner is supportive but nervous. I'm leaning toward yes because I already run the crews and know most of the clients by name, but I've never handled the books, the bidding, or the cash flow, and I can't tell whether clients are loyal to the business or to him. Is my leaning reasonable, and what would make you tell me to walk away?

MEMO:
## Recommendation

Your leaning is reasonable as a reason to pursue this deal. It is not yet a reason to sign. Don't answer the offer with a flat yes or no. Turn it into a staged purchase. Take over the bidding and the books under him for the coming season. Have an outside accountant rebuild the real earnings. Tie part of the price to the revenue that stays after he leaves. Write your walk-away conditions down before you see the final numbers.

## Why

Running the crews and knowing clients by name shows you can operate this business. It does not show the business is worth what you would pay for it. That depends on the owner's side of the work: bid pricing, collecting money and managing cash through the seasons, and whether clients stay when he no longer picks up the phone. You named those gaps yourself. They are the parts you can't see from the field, and they decide whether the business can pay its debt.

Three things raise the stakes.

- **You stop being the crew lead.** Someone has to be paid to do that job, and someone has to do his bidding, sales and admin. The profit that matters is what is left after paying market wages for both, not what he takes home today.
- **His returns may flatter the picture.** That happens if some work is paid in cash, if personal costs run through the company, or if his unpaid long hours are the margin.
- **Client loyalty can't be fully tested before you pay.** It only shows once he is gone, so the price has to carry part of that risk. Part of what you would pay for is goodwill, and your own eight years helped build it.

A bank loan on a deal like this will almost certainly carry your personal guarantee. A bad stretch then becomes a household loss, not just a business one.

Loan rules shape the structure. Suppose the loan is SBA-backed. A seller note that counts toward your required down payment has to stay unpaid for the whole loan term, often around ten years. It can cover at most half of that down payment. I got this from law-firm and lender summaries of the SBA's current rules in October 2026, not from the rulebook itself, so confirm it with your lender. Whether such a loan allows an earn-out at all is (unverified — ask the lender before designing the structure). That is why the client test should happen before closing wherever you can arrange it. He introduces you to the top accounts this season, and they renew in your name before you sign.

Your partner's nervousness is useful information. They share the savings and probably the guarantee. Their tolerance should set the size of the bet, not be argued down.

## What to do

1. **This week, ask him in writing for the records.** You need three years of tax returns, bank statements, the year-to-date profit and loss, revenue by client, and an equipment list with ages. Hire an accountant who does small-business acquisitions. They rebuild the earnings from the returns and bank statements, not from his summary. The fee is small next to the deal. Allow two to four weeks. Before they report, agree with them what coverage and stress test you will require, and write it down.
2. **Take over next season's bidding.** Let him coach you, but have your accountant check each bid against the actual labour hours and costs of comparable past jobs in his records. Have the accountant also walk you through the cash calendar: when payroll and materials go out in spring versus when clients pay.
3. **Sit down with your partner and fix three numbers before you see the final figures.**
   - The most you can afford to lose.
   - The minimum cash left after closing, at least about six months of household expenses plus the loan payments.
   - Whether the house can be pledged.
4. **Propose terms on paper.**
   - He stays through at least one full season and introduces you to the top accounts. They renew in your name before closing.
   - A meaningful share of the price is tied to revenue retained at 12 and 24 months, enough that he loses real money if clients leave. Use an earn-out, or a holdback if the lender won't allow one.
   - Before you sign anything binding, including exclusivity, have a lawyer who handles business sales review it.
5. **Set a decision date in writing at the start, about three months out, and don't sign before it.** The first walk-away condition that trips ends the deal. You may tighten the conditions after you see the numbers, never loosen them.

Walk away if any of these hold:
- He won't share the three years of returns, the bank statements and revenue by client. The same applies if he won't let your accountant review them.
- After a market wage for you, a paid replacement crew lead and a paid replacement for his bidding and admin, profit covers the loan payments by less than about 1.25 times. Treat 1.5 times as the comfortable target.
- You take out the 20% of revenue most tied to him and let costs fall only as fast as crew hours do. If the loan payments are then no longer covered, and he won't restructure so that he carries that risk, walk.
- He refuses to tie a meaningful share of the price to retained revenue, or won't stay through a transition. The same applies if his top accounts won't renew in your name.
- The top ten clients are more than about half of revenue and deal only with him, or the contracts can't be assigned to you.
- Closing would leave you below the cash reserve you and your partner set, or with no working-capital line for spring payroll. The same applies if the trucks and equipment need heavy replacement that the price ignores.
- Your partner, having seen the same numbers, won't accept the guarantee or the collateral.

## Risks of this plan

Staging has costs. He may sell to a competitor or an outside buyer in the meantime. He may also take your requests as distrust, or prefer a cleaner exit that pays more. You will do two jobs for a season, and the accountant's fee is gone if the deal dies.

Rushing costs more. If you sign on what you know today, the first sign of trouble is a thin spring and a fixed loan payment with your savings already spent. The advice would flip toward a plainer, more cash-heavy deal if the records show mostly multi-year recurring contracts and no dominant client. Coverage would also have to be 1.5 times or better after the stress test.

Cost of being wrong: everything short of signing is cheap and reversible. It costs a fee, some awkwardness and a few months. Exclusivity or other binding terms can lock you in before closing, which is why a lawyer reviews them first. Closing itself is not reversible. Your savings are in the business, and the guarantee stays until the loan is repaid or the bank releases you. If the counter-position below is right, the recovery path is to stop before closing. That costs the fee and some goodwill with him. You can then stay on under the new owner, or compete once you have checked any non-compete you signed.

## Strongest counter-position

Position: do not buy the client goodwill at all. "'Do diligence, then decide' assumes diligence can settle whether clients are loyal, and it cannot: loyalty shows itself only after he stops answering the phone, which is after you have paid. An ordinary seller note does not fix that either, because you owe it whether clients stay or leave, and the bank's guarantee runs through you regardless."

Your boss knows the real margins, which clients are personal friends, and whether anyone else would pay more. Selling to the employee often means the buyer has the least information, the most loyalty and the strongest fear of losing the job. The goodwill is partly your own eight years sold back to you. If it is really yours, starting your own outfit may cost little more than equipment.

This position wins in three cases. He won't tie a meaningful share of the price to retained revenue. The price sits well above the value of the trucks, equipment and assignable contracts. The top accounts deal only with him. The evidence would be his refusal, top accounts that won't renew in your name, or a price the equipment and contracts don't support. If the price is close to asset value, most of this case falls away.

## Confidence

- **High:** the decision should not be made on what you know today, and refusing to open the books is a reason to walk.
- **Medium:** a staged deal with a retention-linked price moves enough client-loyalty risk onto him. That depends on whether he agrees and on what the lender allows.
- **Medium:** the 1.25 and 1.5 coverage figures and the 20% stress test are rules of thumb. Your accountant and lender may set them differently, which is why you fix them before the final numbers arrive.
- **Medium:** the seller-note rule above. **Low:** whether an earn-out is allowed, which I have not checked.

Material unknowns: the price, and the loan terms including whether it is SBA-backed. Also the true profit after replacing his work, the client mix and contract terms, any non-compete you signed, whether the house is collateral, and how far your partner will go.

---

## Memo 4

SPEC (the question the memo answers):
My boss is retiring next year and has offered to sell me the landscaping business I've worked at for eight years, which would take most of our savings plus a bank loan, and my partner is supportive but nervous. I'm leaning toward yes because I already run the crews and know most of the clients by name, but I've never handled the books, the bidding, or the cash flow, and I can't tell whether clients are loyal to the business or to him. Is my leaning reasonable, and what would make you tell me to walk away?

MEMO:
## Recommendation

Your leaning is reasonable as a starting instinct, not yet as grounds to sign what you've described — most of your savings plus a bank loan, paid to him in full at closing. Restructure the deal around a transition year you lead, and price the goodwill portion on what actually survives the handover rather than paying it up front. Proceed only if that clears a real cash-flow test with room to spare; otherwise walk away.

## Why

Eight years running crews is real, earned evidence — you know the work, the crews, and the client list, which is exactly what makes you a better buyer than any outsider, and what an outsider would otherwise spend years learning. That part of your confidence holds up.

It's also the wrong evidence for this particular decision. Whether the purchase pays for itself turns on three things you've never done: whether revenue survives once he's gone, whether you can price bids at a profit, and whether you can carry a seasonal cash cycle against a fixed loan payment. Running crews well doesn't touch any of the three, and by your own account you have no track record on any of them yet.

Follow where the money and the risk actually sit in the deal as described. He gets paid in full at closing and walks away with no further stake in whether clients stay. A loan for buying an existing small business is typically backed by a personal guarantee — often secured against major personal assets, a house included if you own one outright or jointly, in which case your partner would need to sign too. The loan gets sized on his historical cash flow, earned with him running the relationships you can't yet evaluate; your eight years reads to a lender as management experience, which is not the same claim as "clients will stay." None of that is independent confirmation that the loyalty question resolves in your favor — it only means that if it resolves against you, your household absorbs the loss and he doesn't. That asymmetry, more than your missing bookkeeping experience, is the center of this decision.

The bidding and cash-flow gaps are real but fixable on an ordinary timeline: a bookkeeper and a line of credit cover the books and the seasonal dip from day one, and bidding is a skill you can learn under supervision before you're the one signing checks. The client-loyalty question is different. It can't be bought, and reading his numbers won't resolve it, because those numbers describe what the business earned with him still in it.

A seller genuinely confident that clients will stay loses little by accepting a price that pays him for that outcome rather than in advance of it — part in cash for the hard assets (equipment, vehicles, booked work), part as a note or earn-out paid from revenue still there a year or two after he's gone. A seller who insists on all cash at closing and won't stand behind his own claim about client loyalty is answering your question for you.

## What to do

This week, at no cost: ask him for three years of tax returns, 12–24 months of bank statements, and revenue by client. Separately, build your own list of every account tagged by who actually deals with it — you, him, or whoever wins the work on price. That second list is the single most informative thing you can produce, and you already have the access to build it.

Then use his last working year as a structured transition, not a countdown to closing: a non-binding letter of intent now; you shadow him on live bids and run a full season's books and cash-flow forecast alongside his bookkeeper; he introduces you to every significant client personally as his successor; you lead the next renewal round under your own name before any final price is set. Bring in an accountant to normalize his numbers — subtract a market salary for you as owner, the cost of replacing whatever he or unpaid family currently does that you'd have to pay someone else for, and normal equipment replacement — and structure the price as appraised equipment and booked work in cash, with the goodwill portion carried as a note paid from revenue that actually persists after he leaves.

Go to closing only if the normalized numbers cover the loan payment with real room to spare. Stall or walk away if: he won't open the books or let you run a real bid-and-renewal cycle before you commit; a handful of clients who deal only with him make up a large share of revenue and he won't personally hand them to you; he refuses to tie any part of the price to what actually stays; or after the down payment you wouldn't have both a household cushion and separate working capital for the business's first slow stretch. Get a lawyer experienced with small-business acquisitions to put the note or earn-out and any personal guarantee in writing before you sign anything.

## Risks of this plan

Waiting costs you something real: this only works if it fits inside his last year, and a seller in a hurry, or one who bristles at being asked to share risk, may not agree to it — you could end up choosing between a worse structure and no deal at all. Testing yourself on bids and books for a season also means learning on the job, on top of the job you already have.

The larger risk runs the other way. If you sign close to what's described — most of your savings plus a personally-guaranteed loan, paid to him in full at closing — and the loyalty assumption turns out wrong, the damage won't be gradual: a fixed loan payment against falling revenue erodes your earnings far faster than revenue itself falls, and your household absorbs it directly. That outcome is hard to reverse — the guarantee and any lien survive even if the business doesn't, and unwinding it means selling or winding down at a loss while the debt remains. Walking away, by contrast, costs you an opportunity and nothing else; your savings and your job stay intact, and the option to revisit this deal on better terms, or find a different one, stays open. That asymmetry is the real argument for testing before you commit rather than after.

## Strongest counter-position

The recommendation assumes a middle path is available — that the seller will cooperate with a plan that shifts real risk onto him, and that a year spent testing bids, books, and client renewals will actually happen rather than stall. Nothing obligates him to accept that. If the loyalty risk is real, his rational move is to avoid pricing it in: hold out for cash at closing, and if this buyer won't pay it, sell to whoever will, or simply keep running the business another year rather than accept a structure that makes his own exit riskier. On that view: "The person who knows most about client loyalty carries none of that risk, and the person who knows least, you, carries all of it" — and he has no reason to change that arrangement voluntarily. If he declines to restructure, the year spent proposing and testing it isn't free: it costs the relationship's goodwill, the calendar (he retires on his timeline, not a diligence schedule), and the real chance he sells to someone else or closes the doors instead. On this reading, the actual choice was never "restructure or walk away" — it's close to the original one: accept terms close to what he's already offered, using price, not structure, as your only real lever, and decide in weeks, not a year; or walk away now. This view wins if he has other realistic buyers, if he needs the proceeds on a fixed timeline a year of testing would jeopardize, or if asking for a note or earn-out this early reads as distrust and costs more goodwill than it buys in protection — in which case watch how he responds to the very first ask (the tax returns, the client list), not to the full restructuring proposal: a fast, open response argues for moving quicker on close-to-original terms; stalling or defensiveness argues for the slower path above.

## Confidence

High: that your operational experience is real and relevant, but by itself answers none of the three things that decide whether this purchase pays for itself.

High: that client concentration — who each relationship actually belongs to — is the single fact most likely to move this decision, since it's the gap you already named and the one this keeps coming back to.

Medium: that a restructured, tested deal is worth pursuing at all — this turns on numbers the question doesn't include: his asking price against the value of the equipment alone, his real margins, and how concentrated his client list is.

Low: that he'll agree to share any of the risk at all — a note, an earn-out, a genuine transition period. You don't yet know how he'll respond, and his response is itself diagnostic.

Material unknowns: the asking price and how much of it is goodwill versus hard assets; his normalized cash flow against the proposed loan terms; how concentrated his client base is and who the primary contact is on the largest accounts; whether he would accept any structure that shares risk with you at all.

---

## Memo 5

SPEC (the question the memo answers):
We freeze production deploys for the last two weeks of December, and three years in a row, the first two weeks of January have been our worst stretch for outages, even though January traffic is lower than December's. Our 60 engineers keep merging code during the freeze and it all ships once the freeze lifts, but each incident review blames a different specific bug, so nobody treats it as one pattern. What is actually going wrong, and is the freeze protecting us or just moving the risk to January?

MEMO:
## Recommendation

Run the cheap diagnostic before committing to the expensive fix: tag three years of January incidents (and this year's) by what actually triggered them — code merged during the freeze, code merged after the freeze lifted, or no deploy trigger at all (calendar rollover, certificate/secret expiry, restarted annual jobs, thin post-holiday staffing). In parallel, because it's low-cost and net-positive regardless of what that tagging shows, start building a metered thaw — the freeze stays, but the backlog ships back out in normal-sized, staggered, canaried slices instead of one big-bang release the day the freeze lifts.

## Why

The freeze controls exactly one variable: when code reaches production. It does nothing to slow how fast code accumulates behind the gate, because merging never stops. Sixty engineers merging for two weeks produces a backlog several times the size of a normal release, written by people who by thaw day are weeks removed from their own code and reviewed, on both ends of the freeze, under the kind of time pressure that thins out review quality. Nothing in the policy discourages the batch from forming, either: the engineers merging code during the freeze aren't the ones carrying the January on-call pager, so there's no feedback loop pushing back on how much accumulates behind the gate. When that backlog ships as one release, previously-untested combinations of changes land together, mask each other's symptoms, and break the assumption that a bad deploy has one bisectable cause — a small deploy gets reverted in minutes, a big one gets fixed forward under pressure, and the fix-forward often becomes the next incident. That mechanism alone would produce exactly what's observed: a different named bug in every postmortem, because the postmortems are diagnosing symptoms of a shared structural cause — deploy size and code staleness — that no incident-review template records.

But that isn't proof the freeze itself is the problem, and treating "the freeze causes January" and "the freeze protects December" as opposite answers is a false choice — moving risk from a high-traffic fortnight run by a skeleton crew to a lower-traffic, fully-staffed one is what the freeze is designed to do, and a January spike is consistent with a freeze that's working as intended, not only with one that's failing. The same two weeks also concentrate risk that has nothing to do with batch size: year-rollover date logic, annual certificate and secret expiries, restarting scheduled jobs, capacity scaled back down after the December peak, and staff returning rusty or new. Every one of those produces its own distinct bug too, so a different root cause in each postmortem doesn't by itself distinguish "one big batch broke in many places" from "the turn of the year always breaks things, freeze or not." Nothing in the current process — no field for deploy size, trigger source, or days-since-merge in the incident template — lets anyone tell those two explanations apart, which is the actual, more basic thing going wrong: three years of postmortems have been diagnosing individual bugs without ever recording the one variable that would show whether they share a cause.

## What to do

Add a required field to the incident-review template — trigger source: merged during the freeze, merged after the thaw, or no deploy trigger (rollover, expiry, restarted job, capacity, vendor) — and backfill it for the last three Januaries plus every freeze-period incident, using existing postmortems, deploy logs, and git history; a few engineer-days of work. That answers the actual question: if most January impact traces back to freeze-period merges and scales with the size of each service's backlog, the batching mechanism is confirmed and worth the bigger investment below; if most of it has no deploy trigger or doesn't track backlog size, the real fix is a turn-of-year hardening pass instead (pre-freeze rollover tests with the clock set forward, an audit of certificates/secrets/annual jobs due in the window, and a staffed re-entry plan), not thaw engineering.

Because it costs little and makes things strictly safer either way, build the metered thaw in parallel rather than waiting on the audit: ship the freeze backlog back out in normal-sized, staggered slices in commit order, with canary and bake time per slice, owned by release management rather than first-merged-first-shipped; where possible, land freeze-period merges dark behind flags so the release and the flag-flip are separate decisions; and build deploy artifacts at merge time so January releases aren't also pulling freshly-rebuilt base images and dependencies nobody has run since mid-December. Before slicing the backlog, check that the commits in it are independently deployable — forward-only migrations or cross-service API sequencing can make a staggered thaw impossible without reordering work first. Track the result by incident-minutes and failures-per-deploy, not incident count, since the mechanism under test changes how bad each failure is, not just how many happen. Longer-term, once the audit data exists, check whether every frozen system actually needs the freeze for December's peak — a narrower freeze reduces how much backlog accumulates in the first place.

## Risks of this plan

A metered thaw that doesn't also shrink the backlog just stretches the risky window across more of January and stacks new work behind it, growing next year's batch. Staggering by service without checking cross-service sequencing or migration order can turn a controlled thaw into a broken one. None of this touches the calendar-driven risks — rollover bugs, expiries, restarting jobs, thin staffing — that recur in the same window regardless of batch size, so if the audit shows those dominate, shipping thaw tooling without also doing the turn-of-year hardening pass leaves the pattern intact for a fourth year. The cost of waiting on the audit before building anything would be small but real — a few engineer-days — which is why the audit and the thaw build run in parallel rather than in sequence. Everything proposed here is additive and reversible: tagging incidents costs nothing to undo, and staged, canaried delivery is strictly safer than today's big-bang release even if the audit later shows calendar effects were the bigger driver — in that case the thaw tooling isn't wasted, effort simply redirects toward the turn-of-year hardening pass instead. The one move this memo does not make, and that would be harder to reverse, is dropping or shrinking the freeze itself — that puts change back into the highest-traffic, thinnest-staffed weeks of the year, and should wait until canary and rollback are proven reliable on small deploys first.

## Strongest counter-position

The case that the freeze is not the problem: a freeze exists specifically to move risk out of a bad window into a better one, so "the freeze moves risk to January" isn't a finding, it's the freeze doing its job — the real test is whether it's a good trade, and on the facts given, nothing shows it isn't. Lower January traffic cuts the other way from how the question frames it: fewer users are exposed to each failure, which argues for the freeze rather than against it. And the same fortnight carries risk that has nothing to do with the freeze at all — year-rollover logic, annual expiries, restarting jobs, returning or thin staff — each of which produces its own distinctly-named bug, so a different root cause in every postmortem is equally consistent with "the calendar breaks things every January" as with "one big batch broke in many places." Neither explanation is ruled out by anything in the question as posed. This wins if the trigger-source audit shows most January impact has no deploy trigger, doesn't scale with backlog size, or would have happened at the same severity with a small daily deploy — in which case the fix is turn-of-year hardening and staffing, and building thaw tooling would be solving a problem the org doesn't actually have.

## Confidence

High that large, infrequent batches of change are inherently riskier to ship than small, frequent ones — bigger batches create untested combinations, mask co-occurring failures, and break single-cause bisection; this holds independent of anything specific to this org. Medium that this mechanism is the dominant driver of these three particular Januaries, as opposed to calendar and staffing effects that would recur regardless of batch size — the facts given are consistent with both, and no one has the data yet to separate them. Low on how much the freeze is currently net-protective versus net-harmful overall — that also depends on the missing data. The material unknown behind all three: what actually triggered each of the last three Januaries' incidents, which the recommended audit is built to answer directly.

---

## Memo 6

SPEC (the question the memo answers):
Our head of growth presented a customer lifetime value of $15,000, calculated by dividing our $180 average monthly revenue per customer by our 1.2% monthly churn rate, and wants to raise what we're willing to spend to win a new customer to $5,000. We've only been selling for three years, so no customer has actually stayed with us longer than 36 months. How far should I trust that $15,000, and what would a more honest estimate look like?

MEMO:
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

---

## Memo 7

SPEC (the question the memo answers):
Three months ago I wrote the analysis our executives used to justify closing our smallest regional office, and I've just found a formula error that overstated that office's losses by about 40%. The office is already closed and its staff were laid off. I can't decide whether my correction to the executive team should read as a plain technical fix or a personal apology, or whether it should say anything about how the decision might have gone with the right numbers. What tone is right for a message like this, and how do these usually go wrong?

MEMO:
## Recommendation

Write the correction as a short, first-person, factual note — one sentence owning the error, the corrected figures for every office in the original review, and confirmation you've independently re-verified the whole model — and leave out any sentence that says or implies whether the decision would have gone differently. Tell your manager in person before the note goes anywhere wider, and handle "does this change anything, and what do we owe the people affected" as a separate, verbal conversation with your manager and the decision-owner, not as content in the memo itself.

## Why

Prompt, complete, self-initiated correction is generally read far better than the same news arriving late, partial, or from someone else first — voluntarily surfacing your own error typically costs less than having it surface another way later. That argues strongly against sitting on this or softening it into a vague "model update."

An executed, irreversible decision like this one is rarely reopened by a later correction. Once staff, budgets, and announcements have moved, organizations generally update the forward-looking numbers and controls rather than reverse the action — and people who approved a hard call tend to defend it, not revisit it, when the challenge to it arrives from inside and in writing after the fact. The note should not be written to try to change the decision, because it almost certainly won't, and that shouldn't be its job.

A single error you've found is weak evidence that it's the only one. Before anything goes out, the whole model needs independent re-verification, including whether the same formula or allocation touched any other office or any number still in current use — because a second correction to the same analysis costs far more credibility than the first, and because if the error isn't isolated to the closed office, this stops being one analyst's note to send and becomes a formal restatement someone more senior should own.

You cannot know, from your analysis alone, whether the executive team would have decided differently with the correct numbers — real closure decisions usually weigh more than one model's output. Writing that claim, in either direction, substitutes your guess for their judgment, and it's exactly the kind of overreach — or, in the other direction, the defensive "the conclusion still holds" — that turns a correction into an argument about the decision instead of a fix to the record.

What you may owe the people who lost their jobs is a real question, and a separate one. They aren't the audience of this memo, and nothing addressed to the executive team reaches them. If that's part of what's driving the pull toward an apology, act on it directly and privately — for instance, raising rehire priority or references with whoever now owns that relationship — rather than folding it into the memo's tone.

## What to do

The note itself: plain first-person register, not a bare "formula corrected" notice and not a message built around how you feel. One sentence naming what broke and roughly how. One short line of apology for the error itself — not for the closure, which you didn't decide alone and can't fully explain in hindsight. Then the corrected numbers for every office from the original review, in the original format, so readers can see where things stand without you supplying the verdict. State plainly that the whole model has been independently re-checked. Close with what else is still being checked, and by when.

Leave out entirely: any sentence saying or implying the decision would or wouldn't have gone differently. That's the line that turns a correction into a verdict.

Before it goes anywhere: re-verify the whole model independently, not just the one figure, and check specifically whether the error reached any other office or any number still in use today — this determines who should actually own and send the correction. Once you're confident in the numbers, tell your manager in person, the same day, before the written note reaches anyone else — they should hear about a flaw behind a layoff decision from you, not from a cold email. Separately and verbally, walk your manager and whoever owns the closure decision through where the office now sits against the original criteria, and let them decide — with HR or legal if they think it's warranted — whether that comparison belongs in writing at all, and who should be the one to send it. Then send the written correction to exactly the people who received the original analysis, promptly once the numbers are confirmed — not faster than you can verify them, not so slow it starts to look like sitting on it.

If you want to act on what you may feel you owe the people who lost their jobs, do it as a separate, concrete, private step — for example asking whoever manages that relationship now about rehire priority or references — not as content or tone inside the executive correction.

## Risks of this plan

Written too sparely, even a fully factual note can still get filed as routine — numbers corrected, nothing more to see — and the question of whether it mattered quietly dies with it. The mitigation is making sure the verbal conversation with the decision-owner is a real conversation and not optional: if nobody who can act on "does this change anything" ever actually hears the question asked, factual-only was the wrong call.

Written too fully — including an explicit comparison against the original closure criteria, even stated as neutral data rather than a verdict — a note to the full executive distribution can still read as the analyst's own judgment on whether the layoffs were justified. That can carry real exposure for you personally and for the company, doesn't reopen a decision that in practice won't be reopened, and doesn't actually help the people who lost their jobs. That's the case for keeping the criteria comparison out of the wide note entirely and confining it to the narrower, verbal, legal-aware channel.

Waiting to verify properly costs a few days; that's cheap insurance against a second, worse correction. Waiting for a "better moment" to send it costs much more — if the error surfaces another way first, the same delay reads as concealment regardless of why you waited.

Cost of being wrong: nothing about the tone of this note is itself irreversible. The closure and the layoffs already happened, and no wording here changes that. If it later turns out more should have gone in writing to more people, that's a recoverable follow-up conversation, not a crisis — the irreversible decision this all traces back to was made three months ago, not in this note.

## Strongest counter-position

The case against keeping the decision-relevance out of the written note: "A correction that fixes the number but withholds its implication for the actual decision isn't neutral or professional — it's a second omission stacked on the first." On this view, the rerun against the original review's threshold belongs in the written note as mandatory content, stated plainly — "under the corrected figure, the decision would/would not have cleared the bar you applied" — not deferred to a private conversation that may or may not happen. Confined to a verbal channel with just the manager and decision-owner, the implication is too easy to let quietly die: a 40% error in the number that ended people's jobs gets filed as routine, "with nothing forcing anyone to ask whether the harm was necessary." This view treats "what tone keeps me safest" as the wrong question, and prioritizes what's owed to the people who paid for the error over what's comfortable for the writer or the executive team.

This wins if the verbal, narrower channel is where accountability goes to die: if weeks later nothing has changed in how the model or the decision are treated, nothing is added to the record, and nothing still reversible (a lease, a rehire decision, an open budget line) gets revisited — that's the sign the quieter path failed and the correction needed to be written and wide after all.

## Confidence

High — plain, ownership-first register beats both a bare technical notice and an apology-centered message, and manager-first sequencing with independent re-verification before anything goes out. These hold regardless of how the harder judgment calls below resolve.

Medium — whether the criteria/ranking comparison for the closed office belongs in the written note at all, or should stay strictly verbal. The evidence cuts both ways: written, it risks reading as a verdict with real personal and legal exposure; unwritten, it risks the implication being quietly dropped. This is a genuine judgment call that should involve your manager and, if either of you is unsure, legal or HR — not a first-line call to make alone.

Low — how much legal exposure a written comparison would actually carry. That depends on jurisdiction and on exactly how the layoffs were carried out, neither of which is stated here.

Material unknowns: whether the corrected figures actually change the office's ranking under the original criteria at all (if they don't, most of this tension dissolves and the note can simply be complete); whether the formula error reached any other office or any number still driving current decisions (this changes who should own and send the correction); and this organization's actual track record with self-reported errors, which shapes how much personal risk any of this genuinely carries for you.

---

## Memo 8

SPEC (the question the memo answers):
Three months ago I wrote the analysis our executives used to justify closing our smallest regional office, and I've just found a formula error that overstated that office's losses by about 40%. The office is already closed and its staff were laid off. I can't decide whether my correction to the executive team should read as a plain technical fix or a personal apology, or whether it should say anything about how the decision might have gone with the right numbers. What tone is right for a message like this, and how do these usually go wrong?

MEMO:
## Recommendation

Send neither a bare technical fix nor a personal apology. Send a plain, owned correction. Put the corrected numbers first, then one sentence of first-person ownership ("the error was mine"). Follow with a short factual statement of where the corrected figures sit against the criteria the original analysis used. Do not give a verdict on whether the closure was right. Have a second person check the fix, and show the draft to your manager or the decision's sponsor before it goes to the group.

## Why

Anyone reading a correction to a closure analysis will want to know first whether it changes the decision. If the message doesn't say, they will answer it themselves, usually in whichever direction suits them. So a factual line on where the corrected figures stand against the original criteria is part of the correction. A verdict is different. "It would have stayed open" or "it wouldn't have changed anything" claims knowledge of lease, strategy and headcount factors you don't hold. Where people were laid off, it also becomes a quotable sentence about the rationale.

The two options in the question fail for specific reasons:

- **Passive technical fix.** "A discrepancy was identified" reads as evasion on a 40% error in a decision that cost people their jobs. It reads that way as soon as anyone does the dollar arithmetic.
- **Personal apology.** It makes the executives manage your feelings. It implies the closure was your decision, when they made it with inputs beyond your spreadsheet. It may also put an admission of fault in writing (unverified — check with HR or legal, as treatment varies by jurisdiction).

One sentence of ownership is enough.

Give dollar figures, not "about 40%", because the phrase is ambiguous:

- If the reported loss was 40% above the true loss, the true loss is about 71% of what was reported (29% lower).
- If the reported figure was 40% too high measured against itself, the true loss is 60% of what was reported (40% lower).

Executives will work out which, and a vague number reads as minimizing.

Order matters because of what each shortcut costs:

- A fix that wasn't independently checked and needs a second correction does more damage than the first error.
- A sponsor who learns of this from a group email stops being an ally.
- The clock on "when did you know?" started the day you found the error, and each extra day makes it harder to answer.
- Corrections an author volunteers typically cost less than ones someone else discovers (a general pattern, unverified here).
- Because staff were laid off, HR or legal may want to review it.

The usual ways these go wrong:

- passive or minimizing wording
- grovelling that turns a group decision into your personal fault
- a counterfactual verdict in either direction
- silence on whether the numbers change anything
- emailing the group before the sponsor has heard
- an unchecked fix that forces a second correction
- not checking whether the same formula sits in other models, so one error looks like a pattern
- hinting at reinstatement or compensation in writing

## What to do

Here is a starting draft of the message. Replace the brackets with exact figures.

> Subject: Correction to the [Office] closure analysis of [date]
>
> I found an error in the analysis I wrote on [date] for the [Office] closure decision. The error was mine: a formula in [the loss calculation] [one-line cause].
>
> Corrected: [Office]'s operating loss for [period] is $[X], not the $[Y] in the original. [Any other figures that changed.]
>
> Against the criteria the original analysis used: [Office] [ranks n of N on operating margin / sits $A above or below the $B threshold]. The original showed [rank or gap]. I have not assessed non-financial factors or whether the decision stands; that is yours to judge.
>
> [Name] independently checked the corrected figures. I also checked [the other analyses or models that use the same formula] and found [none / these]. I have added [check] so this cannot recur. The corrected file is attached and filed beside the original. I found the error on [date]. I am raising it now so you can decide whether anything else needs to review it, including HR or legal. I can walk you through it whenever suits.

Preparation, in order:

1. Spend one to two days having a colleague independently re-check the corrected figures. Re-run the original decision criteria with them, and scan your other analyses and models for the same formula.
2. Tell your manager or the decision's sponsor, in person or by call, with the draft in hand. Do this the same day the check finishes or earlier. Raise anything about the affected staff (recall, severance, references) in that private conversation, not in the message. The sponsor, HR and legal can advise on framing. The corrected figures and the ownership sentence are not theirs to cut. Set a date by which the correction goes out.
3. Scale the criteria line to the result:
   - If the office is still clearly worst on every original criterion, one line saying the ranking is unchanged is enough. Send the correction to everyone who received the original, within days of step 2.
   - If the corrected figures move it across the threshold or near breakeven, take that to your manager as an escalation with HR and legal involved before anything is sent. The written correction still goes to every original recipient on the date set in that conversation.
4. File the corrected analysis with the original in the decision record.
5. If the check turns up a second error, stop, fix it, and restart the check before anything is sent.

## Risks of this plan

- **Delay.** One to two days of checking and briefing add to a clock that is already running. If a recipient hears of the error elsewhere in that window, the delay becomes the story.
- **The criteria line.** It can still be read as a verdict. If the corrected figures flip the office across the threshold, it gives anyone contesting the layoffs a document to cite.
- **No numeric criterion.** If the original analysis had none, the line has nothing to test against.
- **HR or legal review.** It can slow or soften the message, which is why the send date is fixed in advance.

Cost of being wrong:

- **What can't be undone.** The closure and the layoffs can't be undone, and a sent message can't be recalled.
- **What the plan commits to.** The plan commits you to the least you can later add to. You can shorten, add detail or narrow a claim in a follow-up. You can't unsay an apology or a verdict. The draft contains no apology and no verdict, though the criteria line can be read as one, as noted above.
- **Recovery if the counter-position below is right.** Cutting the criteria line is cheap. Send the corrected figures and the ownership sentence, and let the sponsor carry the conversation about the decision.

## Strongest counter-position

The criteria line is the trap. In a case with layoffs, there is no stable line between "here is where the corrected figures sit against the criteria" and "here is whether the closure stands". Every reader will take the first as the second, and whatever the number shows, it will be quoted back in any dispute over the layoffs. The analyst's job is to deliver correct figures and own the error. Whether those figures change the decision is the executives' judgment.

If the closure was a strategic decision that the analysis was used to support after the fact, there may be no numeric criterion at all. A criteria line would then be an invented test. On this view, the plain corrected-figures message with an ownership sentence wins outright.

It wins in two cases:

- The original memo shows no numeric closure threshold.
- HR or legal advise that no written commentary on decision impact should come from the analyst.

The evidence would be the original decision record and that advice.

## Confidence

- **High:** one sentence of first-person ownership beats both a passive technical fix and a personal apology. That follows from how each of them fails.
- **Medium:** a factual criteria line belongs in the message. It depends on whether a numeric closure criterion existed, and on whether the error is specific to this office or affected every office in the comparison.
- **Medium:** the order of steps and the time boxes. They depend on your company's HR and legal process.

Material unknowns:

- whether the corrected figures cross the closure threshold
- whether other models share the formula
- the legal position
- which reading of "40%" applies

---

# REFERENCE KEY (judges' internal contradictions, by memo)

Memo 1: 
- (j1) "no customer repaid $5,000" contradicts the question's figures and its own $5,300
- (j2) "no customer repaid $5,000" false on the question's $180/month

Memo 2: 
- (j1) "settled fact" claim contradicted by its own later hedge

Memo 3: 
- (j1) salary double-count contradicts its own "both roles" Why section

Memo 4: 
- (j1) "costs nothing else" ignores stated retirement and its own counter-position
- (j2) "job stays intact" ignores the stated retirement

Memo 5: 
- (j1) "fully-staffed" January contradicts its own thin-staffing mention
- (j1) "strictly safer" contradicts its own risks section
- (j1) "commit order" conflicts with "rather than first-merged-first-shipped"
- (j2) "fully-staffed" January contradicts its own thin post-holiday staffing
- (j2) "strictly safer" contradicts its own sequencing-risk warning

Memo 6: 
- (j1) "rests entirely on tail" contradicts its own $5,287 covering $5,000
- (j1) net-churn "too high" claim conflicts with its "omits expansion" remark
- (j2) "rests entirely on tail" contradicts the sentence just before

Memo 7: 
- (j1) "nothing irreversible" contradicts its own written-exposure risk section
- (j1) "nothing reaches" laid-off staff contradicts its own leak/discovery point
- (j1) puts figures in writing yet calls explicit comparison too risky
- (j2) "nothing irreversible" overstated; it warns of written exposure
- (j2) "nothing reaches" staff, at odds with its own legal-exposure concern

Memo 8: 
- (j2) rejects written admission but its own draft says "error was mine"
