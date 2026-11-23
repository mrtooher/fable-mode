# Round 2 checker outputs: 12 blind checkers, 3 memos
Each checker saw one memo (with its SPEC block) and one rule set. Rule-set assignment is withheld.

---

## Checker 1 (Memo Z)

VERIFICATION REPORT: Premium Whiskey Lockers Program

Checks run against the SPEC block only.

PROBLEMS (confirmed by direct check against the SPEC)

1. "After subtracting the $15,000 renovation and $1,200 annual maintenance, the first-year net profit is $1,200."
Wrong. $13,000 - $15,000 - $1,200 = -$3,200. Year one is a loss of $3,200, not a profit of $1,200. This is the memo's central financial claim, and its sign is reversed.

2. "The financials support the initial capital investment."
Not supported. With the correct year-one figure (-$3,200), the financials do not show the initial investment paying back in year one.

3. "Because the space is already available, members can purchase a single bottle of their choice to initially stock their locker, allowing for immediate rollout without capital delays."
Contradicts the SPEC in two ways. (a) SPEC says "Minimum bottle purchase to fill locker: 3 bottles." A single-bottle stock-up does not meet that minimum. (b) SPEC says "Room renovation cost: $15,000" and "Lockers require a dedicated 10x10 ft room," so rollout is not free of capital delay.

4. "Operationally, we have identified a 10x10 ft room currently used for dry storage. Because the space is already available..."
Not supported. SPEC says the room is "currently used for dry storage" and that lockers require a "dedicated" room. The room is therefore not available as is. The dry storage must be relocated, and no cost or plan for that is given.

5. "By year two, with the renovation cost fully amortized, the program will generate $11,800 in pure annual profit, providing a strong return on investment."
The arithmetic ($13,000 - $1,200) is right, but it rests on an assumption the SPEC does not give: that every locker buys 3 bottles again in year two. SPEC gives 3 bottles only as the minimum to fill a locker, with no repeat purchase. Also, "amortized" is the wrong term for a one-time $15,000 cost that is simply not repeated. "Strong return on investment" is asserted with no ROI or payback figure computed.

6. "some members may find the $500 annual fee too steep ... To mitigate this, we will offer a founding member discount of 10% for the first year to those who commit during the launch month."
The discount is not in the SPEC and is not modelled. At 10% of $500 across 20 lockers it costs $1,000 in year-one fee revenue, which would make year one about -$4,200 and not the figure in the memo.

7. "The strongest case against the program is that some members may find the $500 annual fee too steep..."
Weak as the strongest case against. The memo's own numbers show a year-one loss and dependence on repeat bottle purchases for year-two profit. Neither is named as the case against. The chosen objection is one the memo then offsets with an unmodelled discount.

8. "The exclusivity of the program will clearly ensure high retention among our top-tier members, making it a strategic win for the club's long-term membership goals."
Unsupported. SPEC contains no retention data or member-tier information. "Clearly ensure" overstates a claim the spec cannot back.

9. "The room will feature a keypad entry system tied to the member's account" vs. "a secure access system integrated with our existing member ID fobs."
Internally inconsistent about the access mechanism (keypad or fob). Not a SPEC conflict, but the memo describes two different systems.

10. Demand is not tested against the SPEC's member base. SPEC gives "Club has 400 active members," and the target is 20 lockers (5% of members). The memo never uses the 400 figure or explains how 20 lockers are expected to sell.

CLAIMS NOT IN THE SPEC (UNVERIFIABLE against the spec; not confirmed wrong)

- "Over the past year, several members have requested a secure location to store their personal spirits."
- "The $150 average bottle price point was selected based on our current top-selling premium spirits, ensuring the inventory will turn quickly and remain fresh." (SPEC gives the $150 figure only; the rationale and turnover claim are not in it.)
- "From: Jim, Beverage Director" (no title given in the SPEC.)
- "The renovation will include custom mahogany lockers, dedicated ambient lighting, and a secure access system..." (scope details not in the SPEC.)
- "all access will be logged" and the weekly audit process (not in the SPEC.)

CHECKS THAT PASSED

- "20 lockers at $500 each, the annual fee revenue is $10,000." Correct.
- "20 lockers x 3 bottles x $50 margin" = $3,000. Correct ($150 - $100 = $50 margin).
- "first-year gross program profit is $13,000." Correct ($10,000 + $3,000).

OVERALL VERDICT: FAIL

The recommendation rests on a year-one net profit figure that is arithmetically wrong (-$3,200, reported as +$1,200). The memo also contradicts the SPEC's 3-bottle minimum and dedicated-room requirement, and its stated "strongest case against" does not engage the year-one loss it shows.

---

## Checker 2 (Memo Z)

VERDICT: FAIL

ERRORS (quoted sentence, then what is wrong)

1. "After subtracting the $15,000 renovation and $1,200 annual maintenance, the first-year net profit is $1,200." Material. $13,000 - $15,000 - $1,200 = -$3,200, a first-year loss. The memo reports a profit of the wrong sign and size.

2. "The financials support the initial capital investment." Material. The spec's own figures give a year-one loss of $3,200 (or $4,200 with the discount in item 7), so the financials do not support the investment in year one.

3. "Because the space is already available, members can purchase a single bottle of their choice to initially stock their locker, allowing for immediate rollout without capital delays." Material, three contradictions: (a) the spec sets a minimum of 3 bottles to fill a locker, and the memo's own financials use 3; (b) the spec says the lockers require a dedicated 10x10 room with a $15,000 renovation, so "without capital delays" is false; (c) the spec says the room is currently used for dry storage, so "already available" does not follow and the memo gives no plan for relocating that storage.

4. "The exclusivity of the program will clearly ensure high retention among our top-tier members, making it a strategic win for the club's long-term membership goals." Material. Overstated: the spec contains no retention data, and "clearly ensure" supports at most "may help." This is a main reason offered for the recommendation.

5. "By year two, with the renovation cost fully amortized, the program will generate $11,800 in pure annual profit, providing a strong return on investment." Material, in part. The $3,000 bottle margin in this figure assumes 3 bottles per locker are bought again every year. The spec gives 3 bottles only as the minimum to fill a locker and does not say the purchase recurs. Without that margin, year two is $8,800 ($10,000 fees - $1,200). The $11,800 sum is correct only under the unstated assumption. Minor: "fully amortized" is the wrong term, because no amortization appears in the model; the full $15,000 is charged in year one. Minor: "strong return on investment" is overstated and not supported by any stated payback or return calculation.

6. "To mitigate this, we will offer a founding member discount of 10% for the first year to those who commit during the launch month." Material. The discount is not in the financials. At $450 per locker, 20 lockers give $9,000 in fee revenue, not $10,000, so year one becomes -$4,200 if all 20 take the discount. The memo does not report this.

7. "The lockers will solve this pain point while generating a new, high-margin revenue stream." Minor. "Solve" is overstated. "High-margin" is judgment: $50 on $150 is a 33% margin, and the memo does not argue that this is high.

8. "The $150 average bottle price point was selected based on our current top-selling premium spirits, ensuring the inventory will turn quickly and remain fresh." Minor. "Ensuring" overstates; no turnover or freshness data is given. The top-seller basis is not in the spec (see unverifiable list).

COVERAGE AGAINST SPEC (omissions, checked separately)
- Active membership of 400 is never mentioned. The memo gives no demand test, and 20 lockers is only 5% of members.
- The dedicated-room requirement is misapplied (see item 3). The memo has no relocation plan for dry storage.
- The 3-bottle minimum is used in the financials but contradicted in the rollout paragraph (item 3).
- Covered correctly: $500 fee, 20-locker target, $150 price, $100 cost, $50 margin, $15,000 renovation, $1,200 maintenance.

DISSENT CHECK: FAIL
The memo says: "The strongest case against the program is that some members may find the $500 annual fee too steep, which could slow the initial rollout of the 20 lockers." This is a narrow strawman. It omits the case its own numbers make: a year-one loss on $15,000 of capital, the displacement of dry storage, no evidence of demand beyond 20 of 400 members, and reliance on repeat bottle purchases that the spec does not state. The stated objection is also answered by a discount that the memo never costs.

UNVERIFIABLE (not in spec, so not checked as errors)
- "Over the past year, several members have requested a secure location to store their personal spirits."
- "Currently, members must take their bottles home after each visit."
- "The $150 average bottle price point was selected based on our current top-selling premium spirits."
- Keypad entry, access logging, weekly inventory audit, and integration with member ID fobs.
- Whether launching is the right decision is judgment and is not verified.

SELF-CRITIQUE
The real weaknesses are items 1-3 and 6: the headline year-one profit is wrong in sign and size, and the rollout logic contradicts the spec. Fixing them requires restating year one as a loss of $3,200 (or $4,200 with the discount), correcting the rollout paragraph to the 3-bottle minimum and the renovation requirement, removing "clearly ensure," stating the recurring-purchase assumption for year two, and rewriting the dissent section to give the financial case against launch.

---

## Checker 3 (Memo X)

VERIFICATION REPORT: LocalHops tap beer transition memo
Checked cold against the SPEC block only.

ERRORS

1. "Their local sourcing clearly shows our members will prefer the fresher product, driving a measurable increase in tap sales."
Overstated, and not supported by the spec. The spec contains no sales data, no member preference data, and nothing on freshness. "Clearly shows" and "measurable increase" claim evidence the memo does not have. MATERIAL: this is the main stated benefit in the recommendation.

2. "Financially, the move is sound and supports our margin targets."
Contradicted by the memo's own text and by the spec. The spec gives a $20/keg cost increase ($110 to $130), and the memo later calls this a "margin compression." Pour cost rises from about 11.1% ($110/124 pints / $8) to about 13.1% ($130/124 / $8) before rebate. MATERIAL.

3. "At 20 kegs a month, our quarterly spend at the new $130 cost is $2,600, which easily clears LocalHops' $5,000 quarterly rebate threshold."
Arithmetic error. 20 kegs x $130 = $2,600 per MONTH. Quarterly spend is 3 x $2,600 = $7,800. The threshold conclusion ("clears") happens to be right, but the stated basis is wrong by a factor of three and would mislead the reader about spend size. MATERIAL, because the rebate case rests on this figure.

4. "Furthermore, because LocalHops delivers bi-weekly, we will only need to receive 2 kegs per delivery to meet our monthly demand, simplifying our receiving process and reducing the administrative burden on the bar staff."
Contradicts the spec in two ways. (a) Bi-weekly is about 2 deliveries a month, so 20 kegs/month needs about 10 kegs per delivery. Two kegs per delivery gives about 4 kegs a month, not 20. (b) The spec sets a LocalHops minimum of 4 kegs per delivery, so 2 kegs per delivery is not allowed. The "simplifying" conclusion depends on this wrong figure. MATERIAL: it changes the ordering plan.

5. "The rebate structure is particularly attractive. LocalHops applies the 5% rebate as a credit on the following month's invoice, meaning the cash flow benefit is realized immediately."
Overstated and internally inconsistent. The spec says the rebate is on quarterly purchases, so a monthly credit is not in the spec. A credit that arrives on the following month's invoice is not "immediate." The memo also treats the benefit as monthly while the rebate is quarterly. MATERIAL: the cash-flow argument depends on it.

6. "Based on our volume, this credit will effectively reduce the net cost per keg to $123.50, bringing it much closer to our current pricing while delivering a superior product."
(a) "Much closer": the arithmetic is correct ($130 - 5% = $123.50), but $123.50 is still $13.50 above the current $110, which is about 12% higher. The rebate closes $6.50 of the $20 gap, about one third. "Much closer" overstates this. (b) "Superior product" is not in the spec and is unsupported. MINOR to MATERIAL; it shapes how the reader weighs the gap.

7. "Operationally, the transition will be seamless."
Contradicted by the spec. The spec gives a bi-weekly delivery schedule (current is weekly), a 4-keg minimum per delivery, and a 12-keg total cooler capacity. The memo's own ordering plan (2 kegs per delivery) conflicts with the minimum. The memo never addresses the cooler capacity or the change in delivery frequency against the 20-keg monthly need. MATERIAL.

NOT ERRORS, BUT UNVERIFIED (not in the spec, stated as fact)
- "Over the past six months, I have evaluated several regional distributors, and LocalHops has emerged as the clear choice..." (evaluation history, unverifiable).
- "LocalHops provides their own tap lines and faucets at no additional cost, and their technical team will handle the initial installation and calibration." (not in spec).
- "Our bar team has already completed a training session with their representatives..." (not in spec).
- "The reduction in delivery frequency also means fewer interruptions during peak service hours." (inference, not in spec).
- Rebate interpretation: the spec says "5% rebate on total quarterly purchases over $5,000." The memo applies 5% to all spend. The spec wording is ambiguous, and if the rebate applies only to the amount over $5,000 (about $2,800 per quarter at $7,800), the rebate (about $140 per quarter) is far smaller than the memo's implied figure (about $390 per quarter). Open item: confirm with LocalHops.

DISSENT CHECK: FAIL
"The strongest case against switching is the $20 per keg price increase, which slightly compresses our pour cost margin compared to our current distributor."
The case is stated, but it is weakened. "Slightly" understates the cost: a $20 increase is about 18% per keg, about $400 a month before rebate, and it moves pour cost by about two points. The dissent omits the strongest objections the memo's own facts raise: the 4-keg minimum conflicting with the bi-weekly 2-keg plan, the reduced delivery frequency against a 20-keg monthly need, the 12-keg cooler limit, and the dependence of the net-cost claim on an ambiguous rebate term. It then dismisses the cost case with "marketing value" and "enhanced member experience," which are not supported by any spec fact. Judgment: this reads as a weak case, not the strongest one.

COVERAGE (omissions, checked separately from errors)
Not addressed: 124 pints per keg and the $8/pint price (so the memo never computes the pour cost it claims is "sound"); the 12-keg cooler capacity; the current weekly delivery schedule as a comparison; the total dollar effect of the price change per month or quarter.

OVERALL VERDICT: FAIL
Material errors: items 1, 2, 3, 4, 5, 7 (item 6 is material to the net-cost claim). The memo's financial and operational case rests on a wrong quarterly spend figure, an ordering plan that breaks the 4-keg minimum and volume math, a non-spec "immediate" cash benefit, and a claim of seamless operation that the spec contradicts. The dissent check also fails. The recommendation itself (switch or not) is judgment and is not verified here.

Re-run needed after fixes: correct quarterly spend to $7,800; correct kegs per delivery to about 10 (or show how a bi-weekly schedule meets 20 kegs/month with a 4-keg minimum and 12-keg cooler); remove "clearly shows," "supports our margin targets," "immediately," "superior," "seamless"; state the strongest dissent with the delivery and minimum constraints and the full pour-cost impact; flag the rebate term as an open item.

---

## Checker 4 (Memo X)

VERIFICATION REPORT: LocalHops keg-distributor recommendation

VERDICT: FAIL. Several material errors. The recommendation depends on a delivery plan that breaks the SPEC's 4-keg minimum and does not meet demand, and the quarterly spend figure is wrong by a factor of three.

ERRORS (quoted sentence, then what is wrong). Items marked material would change what the reader does or believes.

1. "Their local sourcing clearly shows our members will prefer the fresher product, driving a measurable increase in tap sales." MATERIAL. Overstated and unsupported. The SPEC has no sales, member preference, or freshness data. This is the memo's main stated reason.

2. "Financially, the move is sound and supports our margin targets." MATERIAL. Contradicts the memo's own final paragraph ("slightly compresses our pour cost margin"). Margin targets are not in the SPEC.

3. "At 20 kegs a month, our quarterly spend at the new $130 cost is $2,600, which easily clears LocalHops' $5,000 quarterly rebate threshold." MATERIAL. Arithmetic error. 20 kegs x 3 months = 60 kegs; 60 x $130 = $7,800. $2,600 is one month's spend. The threshold conclusion still holds, but the stated figure is wrong by 3x.

4. "because LocalHops delivers bi-weekly, we will only need to receive 2 kegs per delivery to meet our monthly demand" MATERIAL. Two failures. (a) The SPEC says LocalHops requires a minimum of 4 kegs per delivery; 2 violates it. (b) 2 kegs x 2 deliveries per month = 4 kegs per month, not the 20 the SPEC requires. About 10 kegs per delivery would be needed. The step does not follow.

5. "LocalHops applies the 5% rebate as a credit on the following month's invoice, meaning the cash flow benefit is realized immediately." MATERIAL. The credit timing is not in the SPEC. The sentence is also internally inconsistent: a credit on the following month's invoice is not immediate, and a rebate measured on quarterly purchases cannot be known until quarter-end.

6. "Based on our volume, this credit will effectively reduce the net cost per keg to $123.50, bringing it much closer to our current pricing while delivering a superior product." MINOR. The $123.50 is arithmetically correct (130 x 0.95). "Much closer" overstates it: the gap to $110 falls from $20 to $13.50, about a third. "Superior product" is unsupported.

7. "The reduction in delivery frequency also means fewer interruptions during peak service hours." MINOR. Unsupported by the SPEC.

8. "...the anticipated increase in volume outweigh this minor margin compression." MATERIAL. The volume increase is not in the SPEC and no figure is given. "Outweigh" is asserted without support.

9. "I am confident that the enhanced member experience will more than justify the slight increase in cost." MATERIAL. Overstated. No member data is given. The cost increase is $20 on $110, about 18% per keg, which is not "slight".

10. "The strongest case against switching is the $20 per keg price increase, which slightly compresses our pour cost margin compared to our current distributor." MATERIAL (feeds the dissent check). It understates the case. Using the SPEC figures (124 pints per keg at $8), pour cost moves from about 11.1% ($110/124 = $0.89 per pint) to about 13.1% ($130/124 = $1.05 per pint) gross, and about 12.4% at the $123.50 net. The memo also omits the 4-keg minimum problem.

OMISSIONS VERSUS SPEC (coverage, not errors)
- The 4-keg minimum per delivery is never mentioned, and the memo's plan contradicts it (item 4).
- The 12-keg tap cooler capacity is not addressed.
- The current distributor's weekly delivery schedule is not compared.
- No pour-cost calculation is given, although the SPEC supplies pints per keg and the price per pint, and the memo claims margin effects.

DISSENT CHECK: FAIL. The memo names a strongest case, but it is a strawman. It calls an 18% per-keg increase "slight" and "minor", and it dismisses the case with unsupported volume and marketing claims. It omits the delivery-minimum mismatch, which by itself makes the plan unworkable as written.

UNVERIFIABLE (claims not in the SPEC; no check possible)
- "Over the past six months, I have evaluated several regional distributors"
- "LocalHops provides their own tap lines and faucets at no additional cost"
- "their technical team will handle the initial installation and calibration"
- "Our bar team has already completed a training session with their representatives"
- The rebate credit timing (item 5) and any volume or sales increase (items 1, 8)

JUDGMENT (not verified): whether switching is the right business decision. The arithmetic above shows the case as written fails, but the broader trade-off between local-brand value and a higher cost is a judgment call the checks cannot settle.

FIXES NEEDED BEFORE RESUBMISSION: correct the quarterly spend to $7,800; restate the delivery plan at about 10 kegs per bi-weekly delivery (at or above the 4-keg minimum, and within the 12-keg cooler); remove or source the unsupported claims; rewrite the dissent to state the cost increase at its true size and include the delivery-minimum issue; and add the pour-cost numbers.

---

## Checker 5 (Memo Y)

VERIFICATION REPORT: Main Bar Premium Coffee Service Upgrade, checked against the SPEC block. I checked each number in the memo against SPEC and recomputed every derived figure cold.

ARITHMETIC: All derived figures are correct.
- "costing the club $75 per day" (150 x $0.50) is correct.
- "$240 in daily revenue", "$64 in daily bean costs", "$176 in daily gross profit", "$5,280", and "$4,880" are correct.
- "$40 per day" and "$1,200 per month" are correct.
- "$6,080" is correct. An independent check of the total coffee P&L against status quo gives $3,830 minus (-$2,250) = $6,080.

PROBLEMS FOUND:

1. Payback claim contradicted by the memo's own mitigation. Line 18: "The $1,200 one-time installation cost will be recovered in the first week of operation." This holds only at full $3.00 pricing ($6,080 / 30 = $202.67 per day; $1,200 / $202.67 = about 5.9 days). Line 22 says: "To address this, we will run a two-week promotional period offering the premium coffee at $2.00 to encourage trial and build the habit before transitioning to the full $3.00 price." At $2.00, daily benefit is 80 x ($2.00 - $0.80) = $96, plus $40 savings, less $13.33 daily lease = $122.67. Payback is then about 9.8 days, past the first week. The memo also never states the promotion's forgone revenue: 80 x $1.00 x 14 days = $1,120, close to the $1,200 installation it is meant to offset.

2. Scope inconsistency. Line 15: "I recommend we upgrade our main bar coffee service to a premium automated machine, replacing our current complimentary drip coffee setup." Line 16: "Under the proposed model, we expect 80 members to switch to the premium coffee at $3.00 per cup, while 70 cups remain complimentary for those who prefer the standard offering." If 70 complimentary cups continue as the standard offering, the drip setup is not fully replaced. The memo does not say which description is correct.

3. Cups treated as members. Line 16: "we expect 80 members to switch to the premium coffee." SPEC gives "Expected daily premium cup sales: 80 cups", not 80 members. A member may buy more or fewer than one cup per day. The savings math assumes exactly 80 of the 150 free cups convert.

4. Claims not in SPEC and given no source. Each is a factual assertion the recommendation relies on:
- Line 15: "This upgrade addresses member feedback regarding coffee quality while improving the department's overall financial performance."
- Line 19: "Recent surveys indicated that while our food and cocktail programs score highly, the coffee service is perceived as dated."
- Line 19: "By introducing a premium bean sourced from a local roaster, we elevate the morning and post-dinner experience."
- Line 19: "The $3.00 price point was benchmarked against local cafes and is well within the range our members are accustomed to paying for quality coffee."
- Line 20: "The proposed machine is a fully automated super-automatic espresso system, which requires minimal barista training and ensures consistent quality across all shifts."
- Line 20: "The 24-month contract includes all maintenance and parts, eliminating unexpected repair costs."
- Line 20: "Our current bar layout has adequate counter space and existing plumbing within 10 feet of the proposed location, which keeps the installation scope minimal."
- Line 21: "The transition will take place over a single weekend to minimize disruption."
- Line 21: "The beverage team has already identified the specific bean blend and conducted taste tests with a sample group of members, who responded very positively."
- Line 21: "improving service speed during the busy morning rush" (no source for the speed claim).
The line 20 plumbing claim also sits awkwardly with the $1,200 installation cost, which the memo later presents as its main downside, and the memo does not reconcile the two.

5. Case against is incomplete and not quantified. Line 22: "The strongest case against the upgrade is the $1,200 upfront plumbing cost and the risk that fewer than 80 members switch to the paid option, which would delay the payback period and reduce the projected monthly benefit."
- It omits the 24-month lease commitment given in SPEC. $400 x 24 = $9,600, plus $1,200 installation, is a $10,800 total commitment. The memo never states this total and never lists the lock-in as a risk.
- It calls the $1,200 cost the strongest case against, yet line 18 says that cost is recovered in the first week. The two statements conflict.
- It says fewer switches would "delay the payback period" but gives no sensitivity figure or break-even for the 80-cup assumption on which the entire $6,080 projection rests.

WHAT IS CORRECT: The recommendation is stated clearly ("I recommend we upgrade..."), reasons are given, and a case against is present. The arithmetic matches SPEC.

OVERALL VERDICT: FAIL. The arithmetic is sound, but the payback claim in line 18 is contradicted by the memo's own promotion in line 22, the scope in lines 15 and 16 conflicts, several load-bearing facts are unsourced and absent from SPEC, and the case against omits the 24-month commitment that SPEC states.

---

## Checker 6 (Memo Z)

VERIFICATION REPORT: Premium Whiskey Lockers Program

ERRORS (checked by recomputing against SPEC figures)

1. "After subtracting the $15,000 renovation and $1,200 annual maintenance, the first-year net profit is $1,200."
   Wrong sign and value. $13,000 - $15,000 - $1,200 = -$3,200, a first-year net loss. Material: it reverses the year-one result the committee is asked to approve.

2. "The financials support the initial capital investment."
   Contradicted by the memo's own arithmetic, which gives a year-one loss of $3,200 on the $15,000 outlay. Material.

3. "Because the space is already available, members can purchase a single bottle of their choice to initially stock their locker, allowing for immediate rollout without capital delays."
   Contradicts SPEC. SPEC says the room is "currently used for dry storage", so it is not available as stated, and it also requires a $15,000 renovation before lockers exist. "Without capital delays" is false. Material: it misstates feasibility and timing.

4. "members can purchase a single bottle of their choice to initially stock their locker"
   Contradicts SPEC line "Minimum bottle purchase to fill locker: 3 bottles." The memo's own bottle-margin figure (20 x 3 x $50 = $3,000) assumes three bottles per locker, so the memo is internally inconsistent. Material: it changes initial stock, cash and margin.

5. "By year two, with the renovation cost fully amortized, the program will generate $11,800 in pure annual profit, providing a strong return on investment."
   The $11,800 (= $13,000 - $1,200) assumes the 20 lockers renew at $500 and are restocked with 3 bottles each year. Neither assumption is in SPEC or stated in the memo. "Fully amortized" is also a misused term for a one-time cash outlay. "Strong return" is an overstated judgment, and on the memo's own figures the two-year cumulative result is only +$8,600 against $15,000 of renovation. Minor to material.

6. "The exclusivity of the program will clearly ensure high retention among our top-tier members, making it a strategic win for the club's long-term membership goals."
   Overstated. "clearly ensure" is not supported by any SPEC fact or cited data. Material as a basis for the recommendation.

7. "The $150 average bottle price point was selected based on our current top-selling premium spirits, ensuring the inventory will turn quickly and remain fresh."
   Overstated and a non-sequitur. A price point does not ensure turnover or freshness. The "top-selling" basis is not in SPEC. Minor.

8. "To mitigate this, we will offer a founding member discount of 10% for the first year to those who commit during the launch month."
   The step does not follow through the financials. A 10% discount on 20 lockers cuts year-one fee revenue by $1,000, so on the memo's own figures year-one net becomes about -$4,200. The memo does not reflect this. Material.

DISSENT CHECK (the memo recommends, so this applies)

9. "The strongest case against the program is that some members may find the $500 annual fee too steep, which could slow the initial rollout of the 20 lockers."
   Strawman, so the check FAILs. The strongest case against is the financials in items 1 to 5: a year-one loss, dependence on repeat renewals and restocking, the unstated demand, and the displaced dry storage. The memo's chosen objection (fee level) avoids all of these.

COVERAGE GAPS (omissions, not counted as errors under the rules)

- SPEC gives 400 active members. The memo never uses this figure, so there is no uptake or penetration estimate (20 lockers is 5%).
- SPEC's $100 club cost is used only through the margin. No cash-flow timing is given for bottle purchases.

OPEN ITEMS (not in SPEC, cannot be verified here)

- "Over the past year, several members have requested a secure location..." and "members must take their bottles home after each visit": unsourced claims about member demand.
- "...selected based on our current top-selling premium spirits": sourcing not given.
- "generating a new, high-margin revenue stream": a 33% margin ($50 on $150) is a judgment call.
- The sender's title "Beverage Director" is not in SPEC, so it cannot be checked here.
- Access method is inconsistent: "a secure access system integrated with our existing member ID fobs" versus "a keypad entry system tied to the member's account". Minor; may be intended as two methods.

VERDICT: FAIL

Material errors 1, 2, 3, 4, 6, 8 and the strawman dissent in 9 each change what the committee would believe or decide. The memo's central financial claim is wrong on its own numbers. Recomputed year-one result is a loss of about $3,200, or about $4,200 with the proposed discount. The recommendation is not supported as written. The strategic judgment itself (whether to launch) is labeled judgment and is not verified here.

---

## Checker 7 (Memo Y)

VERIFICATION REPORT: Main Bar Premium Coffee Service Upgrade memo, checked against SPEC only.

ARITHMETIC (all checked, all correct)
- "costing the club $75 per day": 150 x $0.50 = $75. Pass.
- "$240 in daily revenue (80 cups x $3.00)", "$64 in daily bean costs", "$176 in daily gross profit", "$5,280" per 30 days: all correct on a 30-day basis.
- "$4,880 in monthly net profit": 5,280 - 400 = 4,880. Correct arithmetic, but see E3 for the label.
- "saves $40 per day ... or $1,200 per month": 80 x 0.50 = 40; x 30 = 1,200. Correct.
- "total monthly financial benefit is $6,080": 4,880 + 1,200 = 6,080. Correct. No double count (the 80 switching cups were free before and cost $0.50 each).

ERRORS (quoted sentence, then what is wrong)

E1. "The $1,200 one-time installation cost will be recovered in the first week of operation."
Wrong: stated as certain. On the memo's own figures the daily benefit is $6,080 / 30 = $202.67, so $1,200 is covered in about 5.9 days. That holds only if the club trades every day of the week and reaches 80 paid cups from day one. Neither is in SPEC, and the 30-day basis is also not in SPEC. The payback claim should be conditional. Material: payback is the central financial argument.

E2. "The 24-month contract includes all maintenance and parts, eliminating unexpected repair costs."
Wrong: SPEC gives only the $400/month lease and the 24-month term. It says nothing about maintenance or parts. "eliminating" is also an overstatement. Material: it is a cost claim the committee would rely on.

E3. "Subtracting the $400 monthly machine lease leaves $4,880 in monthly net profit from the paid coffee."
Wrong: the label "net profit" overstates. Only bean cost and the lease are deducted. No labor, cups, service or the $1,200 installation (amortized or otherwise) is deducted. The label inflates the figure that feeds the $6,080 headline, which is also called a "financial benefit." Material.

E4. "Recent surveys indicated that while our food and cocktail programs score highly, the coffee service is perceived as dated." and "This upgrade addresses member feedback regarding coffee quality"
Wrong: SPEC contains no survey or member-feedback data. These are presented as established facts that justify the recommendation. "addresses" also asserts the upgrade fixes the problem, which no SPEC fact shows. Material.

E5. "The proposed machine is a fully automated super-automatic espresso system, which requires minimal barista training and ensures consistent quality across all shifts."
Wrong: machine type, training needs and quality consistency are not in SPEC. "ensures" is an overstatement. Material as a stated benefit; the labor point also feeds the missing cost line in E3.

E6. "Our current bar layout has adequate counter space and existing plumbing within 10 feet of the proposed location, which keeps the installation scope minimal."
Wrong: not in SPEC. SPEC lists a $1,200 installation and plumbing cost, so calling the scope "minimal" is an unsupported inference. Minor-to-material.

E7. "The $3.00 price point was benchmarked against local cafes and is well within the range our members are accustomed to paying for quality coffee."
Wrong: no benchmark is in SPEC. The price is given only as the proposed member price. Material: the $3.00 price drives the whole revenue figure.

E8. "The beverage team has already identified the specific bean blend and conducted taste tests with a sample group of members, who responded very positively."
Wrong: not in SPEC. Unsupported evidence for the recommendation.

E9. "By introducing a premium bean sourced from a local roaster"
Wrong: sourcing is not in SPEC. Minor.

E10. "The transition will take place over a single weekend to minimize disruption."
Wrong: not in SPEC. Minor.

Note on E4 to E10: the rules' error types do not list unsourced facts by name, so I list them as confirmed absent from SPEC. They are not confirmed false. Where a memo's justification rests on them, they are material.

COVERAGE AGAINST SPEC
All nine SPEC figures appear in the memo. The 24-month term is mentioned only in the maintenance claim (E2). The total lease commitment of $9,600 (400 x 24) and the net result over the 24 months are never computed or disclosed. This is an omission, so it is not counted as an error, but the memo's financial case covers only one month and one day.

DISSENT CHECK
Present. Not a strawman, but thin:
- It names the $1,200 cost and the risk of fewer than 80 members switching. Both are real.
- It omits the fixed $9,600 commitment over 24 months.
- It does not note that the 80-cup volume and $3.00 price have no source in SPEC.
- The proposed mitigation (two weeks at $2.00) is not quantified. Its effect on the $6,080 figure is not computed.
This is a minor open item, not a FAIL on its own.

JUDGMENT (not verified)
Whether the upgrade is the right decision, whether 80 cups a day is realistic, and whether a $3.00 price will hold are judgment calls. They are not settled by this check.

VERDICT: FAIL
Material errors: E1, E2, E3, E4, E5, E7. Each would change what the committee believes about payback, cost risk, or the quality of the evidence. Fix these (state the payback as conditional on the 30-day and seven-day assumptions, remove or source the unsupported facts, relabel "net profit" as bean-and-lease profit, and add the 24-month lease total) and re-run the check. Minor items: E6, E9, E10, and the dissent gaps.

---

## Checker 8 (Memo X)

VERDICT: FAIL

The memo has the required parts: a recommendation (line 15), reasons (lines 16-18), and a strongest case against (line 19). It still fails on arithmetic, on a plan that breaks the supplier's minimum order, and on several claims the SPEC does not support.

PROBLEMS (each confirmed by checking the quoted sentence against the SPEC or by arithmetic from SPEC values)

1. Line 16: "At 20 kegs a month, our quarterly spend at the new $130 cost is $2,600, which easily clears LocalHops' $5,000 quarterly rebate threshold."
   Wrong figure. 20 kegs x $130 = $2,600 per month. Quarterly spend is 60 kegs x $130 = $7,800. As written, $2,600 does not clear $5,000, so the sentence contradicts its own conclusion. The threshold is met only at $7,800.

2. Line 16: "the 5% rebate on that spend will offset a portion of the increase."
   The SPEC says the rebate is "5% rebate on total quarterly purchases over $5,000." The memo applies 5% to all spend and never states its reading. Under a threshold reading, the rebate is 5% x $7,800 = $390 per quarter, or $6.50 per keg. Under a marginal reading, it is 5% x $2,800 = $140 per quarter, or about $2.33 per keg. The memo's $123.50 net figure (line 17) holds only under the threshold reading, which it does not state.

3. Line 16: "because LocalHops delivers bi-weekly, we will only need to receive 2 kegs per delivery to meet our monthly demand"
   Wrong, and it breaks the SPEC. Two bi-weekly deliveries a month at 20 kegs/month need about 10 kegs per delivery. Two kegs per delivery gives about 4 kegs a month, 16 short. Two kegs also violates the SPEC's "minimum order of 4 kegs per delivery." The memo's core operating plan is therefore infeasible as written.

4. Line 16: "Financially, the move is sound and supports our margin targets."
   "Margin targets" appear nowhere in the SPEC, and the memo gives no margin calculation although the SPEC supplies price ($8/pint) and yield (124 pints/keg). Using those values: current pour cost is $110/124 = $0.89/pint, 11.1% of $8. LocalHops gross is $130/124 = $1.05/pint, 13.1%. Net of the threshold-reading rebate it is $123.50/124 = $1.00/pint, 12.5%. The claim is unsupported, and line 19 contradicts it ("slightly compresses our pour cost margin").

5. Line 16: "The reduction in delivery frequency also means fewer interruptions during peak service hours."
   Not in the SPEC. The SPEC gives only the delivery cadence (bi-weekly vs. weekly), not any effect on service hours. Presented as fact without support.

6. Line 17: "LocalHops applies the 5% rebate as a credit on the following month's invoice, meaning the cash flow benefit is realized immediately."
   Not in the SPEC. The SPEC gives no credit timing. The sentence also contradicts itself: a rebate on quarterly purchases, credited on the following month's invoice, is not "realized immediately."

7. Line 18: "LocalHops provides their own tap lines and faucets at no additional cost, and their technical team will handle the initial installation and calibration." and "Our bar team has already completed a training session with their representatives to ensure proper pour techniques and line maintenance."
   Neither fact appears in the SPEC. Both are stated as established.

8. Line 15: "Their local sourcing clearly shows our members will prefer the fresher product, driving a measurable increase in tap sales." and line 19: "the anticipated increase in volume"
   The SPEC contains no member-preference data, no sales-increase figure, and no volume projection. The claimed increase is unsupported, and "measurable" is asserted with no measurement.

9. Line 15: "Over the past six months, I have evaluated several regional distributors" and "This aligns with our strategic initiative to highlight regional partners"
   Neither appears in the SPEC. Unsupported.

10. Header: "From: Jim, Beverage Director"
    The author's title is not in the SPEC. Minor, but unsupported.

11. Line 19: "The strongest case against switching is the $20 per keg price increase, which slightly compresses our pour cost margin compared to our current distributor."
    The case is weakly argued. "Slightly" is not quantified. The $20 increase costs $400 a month, or $1,200 a quarter before rebate, which the memo never states. The memo also omits the SPEC constraints that cut against its own plan: the 4-keg minimum per delivery (see item 3) and the bi-weekly delivery cadence. Whether those are a stronger case against switching is a judgment, but the memo does not weigh them at all.
    Also unsupported: "the marketing value of local craft beer and the anticipated increase in volume outweigh this minor margin compression." No figures support the weighing.

12. Omission: the SPEC's "Club cellar tap cooler capacity: 12 kegs total" is never mentioned. The memo's delivery plan (item 3) and any corrected plan of about 10 kegs per delivery both depend on cooler capacity, and the memo never checks it.

ITEMS CHECKED AND CORRECT
- Per-keg increase: 130 - 110 = $20. Correct.
- Net per keg under the threshold reading: 130 x 0.95 = $123.50. Arithmetic correct, but depends on the unstated reading in item 2.

Items 1, 3, 4 and 6 are confirmed by direct arithmetic or by the absence of the fact from the SPEC. Items 2 and 11 rest on the rebate's ambiguous wording, so they are flagged as unstated assumptions rather than confirmed errors.

---

## Checker 9 (Memo Y)

VERDICT: FAIL

The core arithmetic matches the SPEC. Daily free-cup cost is 150 x $0.50 = $75. Premium gross profit is 80 x ($3.00 - $0.80) = $176/day, or $5,280 over 30 days, less the $400 lease = $4,880. The free-cup saving is 80 x $0.50 = $40/day, or $1,200/month. The total is $6,080/month. Cross-check: net daily change vs. baseline is 2.70 x 80 - 400/30 = $202.67/day, x 30 = $6,080.

PROBLEMS

1. Line 15: "This upgrade addresses member feedback regarding coffee quality..."
Member feedback is not in the SPEC. This is an unsupported factual claim.

2. Line 19: "Recent surveys indicated that while our food and cocktail programs score highly, the coffee service is perceived as dated."
No survey data appears in the SPEC. Unsupported.

3. Line 19: "By introducing a premium bean sourced from a local roaster..."
The SPEC gives a bean cost ($0.80) but no roaster or sourcing detail. Unsupported.

4. Line 19: "The $3.00 price point was benchmarked against local cafes and is well within the range our members are accustomed to paying..."
The SPEC gives the $3.00 price but no benchmarking against local cafes. Unsupported.

5. Line 20: "The proposed machine is a fully automated super-automatic espresso system, which requires minimal barista training and ensures consistent quality across all shifts."
Machine type and training needs are not in the SPEC. Unsupported.

6. Line 20: "The 24-month contract includes all maintenance and parts, eliminating unexpected repair costs."
The SPEC gives only the 24-month term. Nothing says maintenance or parts are included. Unsupported.

7. Line 20: "Our current bar layout has adequate counter space and existing plumbing within 10 feet of the proposed location, which keeps the installation scope minimal."
Layout, counter space and the 10-foot distance are not in the SPEC. Unsupported.

8. Line 21: "The transition will take place over a single weekend..." and "...taste tests with a sample group of members, who responded very positively..." and "...improving service speed during the busy morning rush."
None of these appear in the SPEC. Unsupported.

9. Line 22: "To address this, we will run a two-week promotional period offering the premium coffee at $2.00..."
The promotion is not in the SPEC, and its cost is never computed. At $2.00 each of 80 cups loses $1.00 against the $3.00 price. Over 14 days that is 80 x $1.00 x 14 = $1,120 of forgone gross profit, almost equal to the $1,200 installation cost. The $6,080 figure and the payback claim do not reflect this.

10. Line 18: "The $1,200 one-time installation cost will be recovered in the first week of operation."
Under the memo's own model this holds only because it assumes a 30-day month (not in the SPEC) and full 80-cup uptake from day one, with no ramp. It is also contradicted if the $2.00 promotion (line 22) runs in the first week. The memo gives no start date for the promotion. At the promotional rate the daily benefit falls to $202.67 - $80 = $122.67. Over 7 days that is about $858.67, which is below $1,200. This is a conditional contradiction. The memo should state the start date and either show payback or drop the claim.

11. Line 22: "The strongest case against the upgrade is the $1,200 upfront plumbing cost..."
This is internally inconsistent. The memo's own figures show payback in about six days, so the installation cost is not the strongest case against. The memo also omits the 24-month commitment entirely. Total lease outlay is $400 x 24 = $9,600, plus $1,200, a total of $10,800. That is the most material cost and the memo never mentions it. The memo also gives no sensitivity figure for uptake. Using the SPEC's own numbers, each switching cup adds $2.70/day (after the $0.50 free-cup saving), and the lease costs about $13.33/day, so break-even is roughly 5 switching cups per day. The memo should state this.

12. Line 17 and line 18: "Over a 30-day month" and "Over a 30-day month, this is $5,280."
The 30-day basis is an assumption not in the SPEC. It should be labeled as one. It drives the $6,080 figure and the payback claim.

CHECKED, NO PROBLEM FOUND
- Lines 16 to 18 arithmetic, given the 30-day assumption noted in item 12.
- The statement that 150 - 80 = 70 free cups matches the SPEC.
- The $1,200 installation figure matches the SPEC.
- The recommendation to upgrade is stated, with reasons and a "strongest case against" section, so the memo's structure meets the brief.
- The "From" title and the date (November 22, 2026) are not in the SPEC and cannot be checked against it. I did not treat them as errors.

WHY FAIL
Several confirmed factual claims (items 1 to 8) appear nowhere in the SPEC. The promotion (item 9) is unpriced, and item 10 is contradicted under a plausible reading. Under the verification rules, these checks fail.

---

## Checker 10 (Memo Z)

VERIFICATION REPORT: Premium Whiskey Lockers memo

Problems found

1. Year-one result is misstated (arithmetic error, the central financial claim).
Sentence: "After subtracting the $15,000 renovation and $1,200 annual maintenance, the first-year net profit is $1,200."
Check: $13,000 gross profit - $15,000 renovation - $1,200 maintenance = -$3,200. Year one is a loss of $3,200, not a profit of $1,200.

2. The financials claim contradicts the memo's own numbers.
Sentence: "The financials support the initial capital investment."
Check: with the correct year-one figure of -$3,200, the first year does not support the investment. Only year two is positive under the memo's assumptions.

3. Year-two profit depends on an assumption that is not in the SPEC, and the renovation is mislabeled.
Sentence: "By year two, with the renovation cost fully amortized, the program will generate $11,800 in pure annual profit, providing a strong return on investment."
Check: The $11,800 arithmetic is correct ($10,000 + $3,000 - $1,200). However, (a) the $3,000 bottle margin assumes every locker buys 3 bottles again in year two, but SPEC gives only a 3-bottle minimum to fill a locker and no repurchase rate; (b) the $15,000 is a one-time cost, so "amortized" is not the right description of how it is treated; (c) "strong return on investment" is not supported, since no payback period or ROI figure is calculated.

4. Rollout claim contradicts the SPEC minimum and the renovation requirement.
Sentence: "Because the space is already available, members can purchase a single bottle of their choice to initially stock their locker, allowing for immediate rollout without capital delays."
Check: SPEC says "Minimum bottle purchase to fill locker: 3 bottles." A single bottle does not fill a locker. SPEC also says lockers "require a dedicated 10x10 ft room" and the room renovation costs $15,000, and the memo itself budgets that renovation, so "without capital delays" is inconsistent with the memo's own plan.

5. The memo does not address the existing use of the room.
Sentence: "Operationally, we have identified a 10x10 ft room currently used for dry storage."
Check: SPEC says the room is "currently used for dry storage." The memo never says where the dry storage goes or what it costs to move it, yet it treats the space as "already available."

6. The strongest case against is weak, and its mitigation is not reflected in the financials.
Sentence: "The strongest case against the program is that some members may find the $500 annual fee too steep, which could slow the initial rollout of the 20 lockers. To mitigate this, we will offer a founding member discount of 10% for the first year..."
Check: (a) The objection omits the financial problem the memo's own figures show (year-one loss, see item 1). (b) The discount is not in the numbers: 10% of $500 is $50 per locker. If all 20 lockers take it, year-one fee revenue falls by $1,000, and year-one net becomes about -$4,200 using the corrected figure. The memo does not recalculate with the discount.

7. Unsupported retention claim.
Sentence: "The exclusivity of the program will clearly ensure high retention among our top-tier members, making it a strategic win for the club's long-term membership goals."
Check: SPEC contains no retention data, member-tier data or membership-goal data. The claim is asserted as certain ("will clearly ensure") without support.

8. Unsupported demand and history claims.
Sentence: "Over the past year, several members have requested a secure location to store their personal spirits. Currently, members must take their bottles home after each visit..."
Check: Neither the member requests nor the current take-home practice appears in SPEC. These cannot be verified from the inputs.

9. Unsupported pricing rationale.
Sentence: "The $150 average bottle price point was selected based on our current top-selling premium spirits, ensuring the inventory will turn quickly and remain fresh."
Check: SPEC gives "Average bottle price for program: $150" but nothing about how the price was chosen, sales velocity, or freshness. The turnover and freshness outcomes are asserted without evidence.

10. Operational and staffing details presented as fact but absent from SPEC.
Sentences: "The room will feature a keypad entry system tied to the member's account, and all access will be logged." / "The beverage staff will conduct a weekly inventory audit of the lockers..." / "...a secure access system integrated with our existing member ID fobs."
Check: None of these appear in SPEC. They may be proposals, but the memo states them as settled facts and does not flag them as assumptions.

11. Demand relative to membership is not analyzed.
Check: SPEC gives "Club has 400 active members" and a target of 20 lockers (5 percent of active members). The memo never uses the membership base or explains why 20 sales is achievable. This is an omission rather than a false statement.

Items checked and found correct
- "$500 each" and "annual fee revenue is $10,000" (20 x $500).
- "$3,000 in bottle margin (20 lockers x 3 bottles x $50 margin)": $50 margin = $150 - $100, and 20 x 3 x $50 = $3,000.
- "first-year gross program profit is $13,000": $10,000 + $3,000.
- "$11,800" year-two figure: $10,000 + $3,000 - $1,200 (arithmetic only; assumptions flagged in item 3).

Overall verdict: FAIL
The memo misstates its own first-year result (a $3,200 loss is presented as a $1,200 profit), so its central financial conclusion is wrong. Its rollout claim contradicts the SPEC minimum of 3 bottles and the required renovation, its counterargument omits the financial problem and does not price the discount, and several factual claims are not in SPEC.

---

## Checker 11 (Memo Y)

VERIFICATION REPORT: Main Bar Premium Coffee Service Upgrade memo, checked against the SPEC block only.

ARITHMETIC CHECK: No arithmetic errors. Verified: 150 x $0.50 = $75/day; 80 x $3.00 = $240; 80 x $0.80 = $64; $176/day gross; x30 = $5,280; minus $400 = $4,880; 80 x $0.50 = $40/day = $1,200/month; $4,880 + $1,200 = $6,080.

ERRORS (quoted sentence, then what is wrong):

1. Material. Line 18: "The $1,200 one-time installation cost will be recovered in the first week of operation."
   This is contradicted by the memo's own plan in its last paragraph, which runs a two-week $2.00 promotion first. At $2.00, the daily benefit is (2.00 - 0.80) x 80 + 40 = $136 before lease, or about $122.67 after the prorated lease ($13.33/day). After 7 days that is at most $952 before lease and about $859 after, both below $1,200. The "first week" claim holds only at $3.00 from day one with all 80 cups sold from the start, and the memo does not state that the payback figure assumes full price from day one.

2. Material. Line 22: "To address this, we will run a two-week promotional period offering the premium coffee at $2.00 to encourage trial and build the habit before transitioning to the full $3.00 price."
   This does not follow. The risk named in the same sentence chain is delayed payback and lower monthly benefit. The promotion lowers revenue by $1.00 per cup on 80 cups, about $80/day or $1,120 over 14 days, and the memo does not quantify or mention that cost. It makes the payback problem worse, not better.

3. Material. Line 22: "The strongest case against the upgrade is the $1,200 upfront plumbing cost and the risk that fewer than 80 members switch to the paid option..."
   This is a partial and weak case. It leaves out the 24-month commitment stated in the SPEC: $400 x 24 = $9,600 in lease, or $10,800 with installation. Line 20 presents the 24-month term only as a benefit. It also leaves out the main member-relations risk: the memo says member satisfaction is "a top priority" (line 19), yet it starts charging 80 of 150 daily cup users for coffee that was complimentary, and never addresses that. The dissent check FAILs on this.

4. Minor (overstated). Line 20: "The 24-month contract includes all maintenance and parts, eliminating unexpected repair costs."
   "Eliminating" overstates the case. Even if coverage were stated in the source (it is not in the SPEC), it would cover only the 24-month term and would not eliminate every repair cost. Fix: limit the claim to the term and to covered items.

5. Minor (overstated). Line 15: "This upgrade addresses member feedback regarding coffee quality..."
   Stated as fact. The SPEC contains no member feedback.

UNSUPPORTED CLAIMS (not in the SPEC; cannot be verified against it; not counted as errors under the rules, but the reader is told them as fact):
- Line 19: "Recent surveys indicated that while our food and cocktail programs score highly, the coffee service is perceived as dated."
- Line 19: "By introducing a premium bean sourced from a local roaster..."
- Line 19: "The $3.00 price point was benchmarked against local cafes and is well within the range our members are accustomed to paying..."
- Line 20: "The proposed machine is a fully automated super-automatic espresso system... ensures consistent quality across all shifts."
- Line 20: "Our current bar layout has adequate counter space and existing plumbing within 10 feet of the proposed location..."
- Line 21: "The transition will take place over a single weekend..."
- Line 21: "The beverage team has already identified the specific bean blend and conducted taste tests with a sample group of members, who responded very positively."
- Line 21: "...improving service speed during the busy morning rush."

COVERAGE GAPS (omissions, checked against the SPEC; not counted as errors):
- The total 24-month financial commitment (lease plus installation, $10,800) is never stated.
- The memo assumes 30 operating days per month (line 17) and that all 80 cups sell from day one; neither is flagged as an assumption or tested against the ramp.

JUDGMENT (not verified, labeled as such): whether upgrading is the right decision, whether $3.00 is the right price, and whether member reaction will be positive. These cannot be settled by a check.

OVERALL VERDICT: FAIL. Three material errors (items 1, 2, 3) are outstanding. The memo needs its payback claim corrected to reflect the promotion, the promotion's cost quantified or its link to the payback risk removed, and a real case against added (24-month lock-in and loss of a free benefit). Items 4 and 5 are minor and should be fixed or logged. The unsupported claims should be sourced or removed.

---

## Checker 12 (Memo X)

VERIFICATION REPORT: LocalHops transition memo

Checked against the SPEC block only. Inputs used: cost $110/keg (124 pints), price $8/pint, 20 kegs/month, LocalHops $130/keg, 4-keg minimum per delivery, bi-weekly delivery (current distributor weekly), 12-keg cooler capacity, 5% rebate on quarterly purchases over $5,000.

PROBLEMS

1. Quarterly spend is misstated.
Quote: "At 20 kegs a month, our quarterly spend at the new $130 cost is $2,600, which easily clears LocalHops' $5,000 quarterly rebate threshold."
Problem: $2,600 is one month (20 x $130). Quarterly spend is 60 kegs x $130 = $7,800. The threshold conclusion still holds, but the figure is wrong by a factor of three.

2. The delivery quantity violates the SPEC minimum and cannot cover demand.
Quote: "Furthermore, because LocalHops delivers bi-weekly, we will only need to receive 2 kegs per delivery to meet our monthly demand, simplifying our receiving process and reducing the administrative burden on the bar staff."
Problem: The SPEC sets a minimum of 4 kegs per delivery, so 2 kegs per delivery is not an allowed order. Bi-weekly deliveries are about 2.17 per month, so 2 kegs each gives about 4 kegs a month, roughly one-fifth of the 20-keg demand. Covering 20 kegs/month needs about 9 to 10 kegs per delivery. The stated receiving simplification and reduced administrative burden rest on this wrong figure.

3. Unsupported and internally inconsistent rebate timing.
Quote: "LocalHops applies the 5% rebate as a credit on the following month's invoice, meaning the cash flow benefit is realized immediately."
Problem: The SPEC gives no credit timing. It states a quarterly rebate on quarterly purchases, which cannot be credited "immediately" or monthly as described. The memo's own quarterly framing contradicts a monthly credit.

4. The per-keg net cost is arithmetically right but overstated.
Quote: "Based on our volume, this credit will effectively reduce the net cost per keg to $123.50, bringing it much closer to our current pricing while delivering a superior product."
Check: 5% x $130 = $6.50, and $130 - $6.50 = $123.50. Correct. But the gap to the current $110 cost is still $13.50 (down from $20). "Much closer" is an overstatement, and "pricing" is the wrong word for a cost comparison.

5. The financial conclusion is asserted without the margin calculation, and the memo's own admission contradicts it.
Quote: "Financially, the move is sound and supports our margin targets."
Problem: No margin target appears in the SPEC, and no pour-cost calculation is shown. Computed from the SPEC at $8/pint: current cost $110/124 = $0.887 per pint, about 11.1% pour cost. New gross $130/124 = $1.048, about 13.1%. New net $123.50/124 = $0.996, about 12.5%. The memo later concedes "this minor margin compression," so "supports our margin targets" is unsupported and conflicts with the memo's own text.

6. Cooler capacity is not addressed.
The SPEC gives a 12-keg tap cooler capacity. The memo never mentions it. Under the bi-weekly schedule with a 4-keg minimum, the memo should show that the order size fits the cooler. This is an omission.

7. Load-bearing claims not supported by the SPEC.
These cannot be verified from the SPEC and are presented as fact. Each is marked UNVERIFIABLE:
- "Over the past six months, I have evaluated several regional distributors..."
- "Their local sourcing clearly shows our members will prefer the fresher product, driving a measurable increase in tap sales."
- "LocalHops provides their own tap lines and faucets at no additional cost, and their technical team will handle the initial installation and calibration."
- "Our bar team has already completed a training session with their representatives to ensure proper pour techniques and line maintenance."
- "This aligns with our strategic initiative to highlight regional partners and elevate the main bar experience."
- "The reduction in delivery frequency also means fewer interruptions during peak service hours."
- "Operationally, the transition will be seamless."

8. The strongest case against is misidentified and then dismissed on unsupported grounds.
Quote: "The strongest case against switching is the $20 per keg price increase... However, the marketing value of local craft beer and the anticipated increase in volume outweigh this minor margin compression. I am confident that the enhanced member experience will more than justify the slight increase in cost."
Problem: The memo's own case against is weaker than the constraints it leaves out: the 4-keg minimum, the bi-weekly schedule needing about 10 kegs per delivery, and the cooler capacity. The rebuttal relies on "marketing value," "anticipated increase in volume," and "enhanced member experience," none of which is quantified or in the SPEC. Its verdict that the increase is "slight" conflicts with its own margin-compression admission.

OVERALL VERDICT: FAIL

The memo's recommendation rests on a false delivery quantity that breaks the 4-keg minimum, a misstated quarterly spend figure, and an unsupported margin claim. The rebate and operational claims are not in the SPEC. The recommendation may still be arguable, but this memo does not support it as written.
