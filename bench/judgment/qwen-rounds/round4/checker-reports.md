# Round 4 packet for Qwen, part 2: 16 checker reports

Each checker saw ONE memo (with its SPEC) and one of two rule sets. Rule-set assignment is withheld.

---

## Checker 1 (Memo 5)

VERIFICATION REPORT

Overall verdict: FAIL

Errors (checked against the spec and the memo's own text):

1. "That mechanism alone would produce exactly what's observed: a different named bug in every postmortem, because the postmortems are diagnosing symptoms of a shared structural cause..." Overstated. "Exactly" and "because" present the batch mechanism as established, while the memo itself later says "that isn't proof" and rates the mechanism only "Medium" as the driver. Material: it changes what the reader believes about the cause.

2. "moving risk from a high-traffic fortnight run by a skeleton crew to a lower-traffic, fully-staffed one is what the freeze is designed to do" Contradicts the memo's own facts. The Recommendation lists "thin post-holiday staffing" as a January trigger, the Counter-position refers to "returning or thin staff," and the Risks section lists "thin staffing" for the same window. Material: this premise carries the freeze-trade argument.

3. "Because it costs little and makes things strictly safer either way, build the metered thaw in parallel rather than waiting on the audit" Overstated, and the memo contradicts it. The Risks section says "Staggering by service without checking cross-service sequencing or migration order can turn a controlled thaw into a broken one," and it also says staged delivery is "strictly safer" as a flat claim. Material: this is the stated reason to build before the audit reports.

4. "because it's low-cost and net-positive regardless of what that tagging shows" conflicts with "the real fix is a turn-of-year hardening pass instead (...), not thaw engineering." The plan says thaw work is worth doing whatever the audit shows. The decision branch says it should not be done if the audit points to calendar causes. Material: the reader cannot tell whether to build the thaw under that outcome.

5. "the batching mechanism is confirmed and worth the bigger investment below" Overstated. The audit is a tagging of backfilled postmortems and deploy logs, which can at most show a correlation. The memo's own Confidence section says "no one has the data yet to separate them." Material: this decides the larger investment.

6. Counter-position: "on the facts given, nothing shows it isn't [a good trade]." The spec states that "the first two weeks of January have been our worst stretch for outages, even though January traffic is lower than December's." That is evidence bearing on the trade, so the claim misstates the facts the counter-position is supposed to argue from. This undermines the fairness of the dissent (see below).

Dissent check: The memo recommends something, so a strongest case against it is required. The counter-position is present and is not a pure strawman. It argues that thaw tooling could solve a problem the org does not have, and that a calendar-driven cause would make the batch diagnosis wrong. However, its main premise misstates the spec (error 6), and it does not address the risk that a staged thaw spreads change across the January window. It FAILS on fairness.

Omissions (not errors, noted for coverage):
- The spec asks whether the freeze protects the org or moves risk to January. The memo says it has "Low" confidence on this and defers to data it does not have. The question is therefore not answered.
- The audit decision rule covers only "most" impact in each direction. A split result (for example, half freeze-period merges, half calendar) has no stated action.

UNVERIFIABLE (not in the spec and not contradicting it; not counted as errors):
- "Sixty engineers merging for two weeks produces a backlog several times the size of a normal release"
- "written by people who by thaw day are weeks removed from their own code ... under the kind of time pressure that thins out review quality"
- "the engineers merging code during the freeze aren't the ones carrying the January on-call pager"
- "the fix-forward often becomes the next incident"
- "Nothing in the current process — no field for deploy size, trigger source, or days-since-merge in the incident template"
- "three years of postmortems have been diagnosing individual bugs without ever recording the one variable"
- "High that large, infrequent batches of change are inherently riskier ... independent of anything specific to this org" (judgment, labeled as confidence)

Open items: the claims listed under UNVERIFIABLE, and the omissions above.

Passed: No arithmetic or numeric claims are present. The recommendation, reasons, and risks are internally consistent apart from errors 2 through 4. The audit design itself is clearly specified.

---

## Checker 2 (Memo 7)

VERDICT: FAIL

Errors (quoted, each checked against the memo text):

1. "The note should not be written to try to change the decision, because it almost certainly won't" (Why, second paragraph). The support in that paragraph is "rarely reopened", "generally update", and "tend to defend". That backs "unlikely" at most. "Almost certainly" is an overstated claim, and it is material because it tells the reader not to challenge the decision.

2. "doesn't reopen a decision that in practice won't be reopened" (Risks, second paragraph). This repeats the same overstatement as a flat certainty. Material for the same reason.

3. "Then send the written correction to exactly the people who received the original analysis" (What to do). The same section says "this determines who should actually own and send the correction", and the Why section says that if the error reaches other numbers "this stops being one analyst's note to send and becomes a formal restatement someone more senior should own." The procedure never branches on that check. It names the analyst as sender no matter what the check finds, so the step does not follow from the condition the memo sets for it. Material, because it decides who sends the correction.

4. "if they don't, most of this tension dissolves and the note can simply be complete" (Material unknowns). This conflicts with "Leave out entirely: any sentence saying or implying the decision would or wouldn't have gone differently" (What to do) and with "That's the case for keeping the criteria comparison out of the wide note entirely" (Risks, third paragraph). Under the memo's own rules, a ranking result that does not change would still be a decision-relevant statement, so the conditional gives the wrong instruction for what goes in the note. Material, because it bears directly on the note's content.

5. "nothing addressed to the executive team reaches them" (What you may owe). This is an absolute claim about information flow. Executive correspondence is commonly forwarded, and nothing in the spec or the memo supports "nothing". Minor.

6. "the same delay reads as concealment regardless of why you waited" (Risks, third paragraph). "Regardless" asserts how readers will interpret the delay, and no support is given. Minor.

7. "the irreversible decision this all traces back to was made three months ago, not in this note" (Cost of being wrong). The spec says only that the analysis was written three months ago and that the office is now closed. It gives no decision date. This is an unsupported factual claim, and the memo uses it to argue that the cost of being wrong is low. Minor, logged as an open item.

Dissent check: passes. The memo states a strongest counter-position, the case for putting the decision-relevance in the written note, and it states that case in its strongest form. It also names the conditions under which that case would win. It is not a strawman.

Coverage against the spec: both parts of the question, the tone and the ways these usually go wrong, are addressed (the Risks section covers the second). This is a coverage check only and does not affect the verdict.

What would clear the FAIL: soften items 1 and 2 to "unlikely" and "is unlikely to be reopened"; add a branch to the sending step that depends on the other-office check, so that a wider error makes a more senior person the owner; and remove or qualify the "note can simply be complete" line so it matches the exclusion. Items 5 to 7 should be fixed or logged as open items, and then the check should be re-run.

Judgment, not verified: whether a factual-only note with a verbal criteria conversation is the right call, the tone recommendation itself, and the High, Medium, and Low confidence labels. The checks above cannot settle these; they remain judgment.

---

## Checker 3 (Memo 8)

VERIFICATION REPORT: decision memo on how to word a correction to a closure analysis

ERRORS (per the error-first check)

1. Recommendation vs. draft order (material)
   - Recommendation: "Put the corrected numbers first, then one sentence of first-person ownership ("the error was mine")."
   - Draft: "I found an error in the analysis I wrote on [date] for the [Office] closure decision. The error was mine: a formula in..." The ownership sentence comes first, and the corrected figures follow in the next paragraph.
   - The draft contradicts the memo's own recommended order. It is the text the reader is told to send, so this changes what gets sent.

2. Overstated claim in the draft (material)
   - "I have added [check] so this cannot recur."
   - A check reduces the chance of recurrence but cannot guarantee it. "Cannot" makes a promise the author cannot back, in a message to executives after a decision that cost jobs.

3. Unconditional criteria line vs. the memo's own exception (material)
   - Recommendation: "Follow with a short factual statement of where the corrected figures sit against the criteria the original analysis used."
   - Why section: "So a factual line on where the corrected figures stand against the original criteria is part of the correction."
   - Risks section: "No numeric criterion. If the original analysis had none, the line has nothing to test against." Counter-position: the plain message "wins" if "The original memo shows no numeric closure threshold."
   - The recommendation and Why sections are unconditional, but the memo later says the criteria line has nothing to test against when no numeric criterion exists. The headline advice does not say what to do in that case, which is the case the memo itself flags as one where its plan fails.

4. Internal inconsistency in the counter-position (minor)
   - "On this view, the plain corrected-figures message with an ownership sentence wins outright."
   - Next line: "It wins in two cases:"
   - "Outright" implies unconditional; the list makes it conditional.

5. Absolute claim in the counter-position (minor)
   - "Every reader will take the first as the second, and whatever the number shows, it will be quoted back in any dispute over the layoffs."
   - This is stated as certain, though it is a prediction about readers.

6. Asserted fact not in the spec (minor, open item)
   - "It implies the closure was your decision, when they made it with inputs beyond your spreadsheet."
   - The spec says executives used the analysis to justify the closure. It does not say they had other inputs. Stated as fact without support.

7. Unclear wording of the second reading (minor)
   - "If the reported figure was 40% too high measured against itself, the true loss is 60% of what was reported (40% lower)."
   - The arithmetic holds (reported figure overstated by 40% of itself gives 60%), but "measured against itself" does not say what the baseline is. A reader may not know which reading applies.

Checked and found correct: "If the reported loss was 40% above the true loss, the true loss is about 71% of what was reported (29% lower)." (1.4T = R, so T = 0.714R.)

DISSENT CHECK
Present and reasonably fair. It states the case that the criteria line is a trap and that the analyst should deliver figures and ownership only. Item 4 above is a consistency issue within that section, not a strawman.

CONFIDENCE LABELS
The "High" label on "one sentence of first-person ownership beats both a passive technical fix and a personal apology" is a judgment, not a verified result. It is labeled as such and is not counted as an error.

VERDICT: FAIL
Material errors 1, 2 and 3 each change what the reader would send or believe. Items 1 and 2 are in the draft text itself. Item 3 leaves the headline advice unresolved for the no-numeric-criterion case. Minor items 4 to 7 should be fixed or logged as open items. A fixed version needs a fresh check: the draft order should match the recommendation, "cannot recur" should be replaced with a weaker claim, and the criteria line should be made conditional on a numeric criterion existing.

Not assessed (judgment, outside the list): whether the criteria line is the right call, and the legal and HR process the memo says to follow.

---

## Checker 4 (Memo 2)

VERDICT: FAIL

Errors (quoted, in memo order). Material errors are the ones that would change what the reader does or believes.

MATERIAL
1. Recommendation: "The freeze is moving risk into January and concentrating it." Stated as settled. The memo's own support is the batch explanation, which it rates Medium confidence ("Medium: the batch is the main cause") and calls "not a proven one". The counter-position says "the freeze is not what is hurting you." The headline is stronger than the support.
2. Why: "This is why every review blames a different bug." Stated as established. The memo then says the batch is unproven and that the rival causes predict the same pattern ("A big batch predicts 'a different bug each time', and so does every one of those."). The sentence overstates the support.
3. Why: "The shared cause is one level up: why did that bug reach production inside a batch too big to attribute?" Presented as the shared cause. Nothing in the spec or the memo establishes it, and the memo's own unknowns list says the cause is not known.
4. Risks: "Loosening the freeze would move change risk into December's peak traffic and thin staffing." The memo says the opposite of what it knows. The Why section says "you have not said what December looks like", so December staffing is unknown. The counter-position repeats "December's peak traffic and thin staffing" as fact. The argument against loosening the freeze rests on an assertion the memo admits it cannot support.
5. Step 1 vs Step 4 (sequencing). Step 1 says the test must be "finished before the freeze starts", and Step 4 says "decide these changes at least a month before the freeze starts". Step 4 is gated on the step 1 result, but the step 1 deadline can fall after the one-month decision point. The plan has no instruction for that case, so the decision can be missed or taken without its gate.
6. Risks vs Step 4 gate. Step 4 is gated: "If the test supports the batch diagnosis, decide these changes...". Risks says: "If so, run one staged thaw anyway with the new fields recorded." That is a thaw run on an inconclusive test, which the gate excludes. The reader cannot tell which instruction applies.

MINOR
7. Why: "and nobody tested those combinations together." The spec says nothing about testing practice. This is a factual claim about the team that is asserted, not supported.
8. Why: "Google's SRE book reports that roughly 70% of outages are due to changes in a live system". The step does not follow for this memo's claim. The figure is about changes in general, not about batch size, so it cannot separate the batch explanation from the calendar causes. The figure itself was not checked: this run had no fetch tool, so it is UNVERIFIABLE here.
9. Confidence: "Large batches are harder to diagnose and roll back and carry untested interactions (mechanics, and your own description)." The spec does not describe the interactions as untested. Attributing that to "your own description" is a misattribution.
10. Confidence: "One check, merge date against deploy date, settles most of it." Overstated. That check does not address staffing, which the memo lists as a rival cause, or time to restore.

Dissent check: PASS. The counter-position states the case against the recommendation fairly and specifically, including the conditions under which it would win. It is not a strawman.

Coverage against spec: both questions are answered. "What is going wrong" is answered only as a hypothesis, and the memo labels it so. That is judgment and is not verified here.

Self-critique: the real weaknesses are items 4 to 6, which are the plan's own internal inconsistencies, and they should be fixed before the memo is relied on.

Unverified: the SRE book 70% figure (item 8) and any claim about this organization's roster or staffing, since the spec gives neither.

---

## Checker 5 (Memo 3)

VERIFICATION REPORT: decision memo on buying the landscaping business

ERRORS FOUND (checked against the spec and the memo text)

Material:
1. "Running the crews and knowing clients by name shows you can operate this business." This overstates the case and contradicts the spec. The user said they have never handled the books, bidding, or cash flow, and the memo's next sentence concedes those are the decisive gaps. Crew leadership shows you can run crews, not the business.
2. "He introduces you to the top accounts this season, and they renew in your name before you sign." Two problems. First, it conflicts with "It only shows once he is gone" (line 17), which says loyalty cannot be tested before he leaves. The memo never reconciles this. Second, it assumes the top accounts' renewal dates fall before closing, which the memo does not establish.
3. "profit covers the loan payments by less than about 1.25 times. Treat 1.5 times as the comfortable target." and, later, "Coverage would also have to be 1.5 times or better after the stress test." The walk-away threshold is 1.25, but the risks section sets a 1.5 requirement. A reader at 1.3 cannot tell whether to walk. This changes the decision, so it is material.

Minor:
4. "and they decide whether the business can pay its debt." Overstated. Bidding and collections affect debt service, but price, rates, and other factors matter too.
5. "Closing itself is not reversible." Overstated. A closed sale can be undone by a later resale. The sentence means you cannot back out after closing, which should be stated that way.
6. Terminology drifts between "the coming season" (Recommendation), "this season" (the sentence quoted in item 2), and "next season's bidding" (step 2). Pick one reference point.

DISSENT CHECK: FAILS on fairness
The counter-position is substantial, but it argues against a fix the memo does not propose. It says: "An ordinary seller note does not fix that either, because you owe it whether clients stay or leave, and the bank's guarantee runs through you regardless." The memo's fix is an earn-out or holdback tied to retained revenue (step 4), and the seller note appears only in the SBA down-payment context. The counter also never addresses the memo's main mitigation, the pre-closing renewal test. The strongest case against the recommendation needs to meet the retention-linked price and the pre-closing test directly.

UNVERIFIABLE (not checked against any source here; not flagged as wrong)
- "A seller note that counts toward your required down payment has to stay unpaid for the whole loan term, often around ten years. It can cover at most half of that down payment." Not confirmed by any source available to this check. The memo itself marks it as medium confidence and asks for lender confirmation.
- "I got this from law-firm and lender summaries of the SBA's current rules in October 2026, not from the rulebook itself." The sourcing claim cannot be confirmed. No citation is given.
- Whether an earn-out is allowed under an SBA loan. The memo correctly labels this unverified, yet step 4 relies on it. Judgment: the fallback holdback is the right hedge.
- "A bank loan on a deal like this will almost certainly carry your personal guarantee." Plausible but unsourced. Judgment.

COVERAGE OF SPEC
The memo answers both parts. It judges the leaning reasonable as a reason to pursue, not to sign, and gives a concrete walk-away list. The recommendation, reasons, risks, and confidence levels are all present.

VERDICT: FAIL
The coverage-threshold contradiction (item 3) and the overstated claim about operating the business (item 1) are material. The dissent check also fails on fairness. Fix items 1 to 3 and the dissent check, then re-run this check. Minor items 4 to 6 can be fixed or logged as open items. The unverifiable items remain labeled as such.

---

## Checker 6 (Memo 4)

VERIFICATION REPORT

Verdict: FAIL

Material errors (each would change what the reader does or believes):

1. "Walking away, by contrast, costs you an opportunity and nothing else; your savings and your job stay intact, and the option to revisit this deal on better terms, or find a different one, stays open."
   Wrong: the claim that the job stays intact is unsupported and contradicts the memo's own counter-position. That section says the seller, if this buyer won't pay his terms, may "sell to whoever will, or simply keep running the business," and it names "the real chance he sells to someone else or closes the doors" as a live outcome. Declining the deal does not remove the job risk the memo itself raises. The "nothing else" claim is the core of the memo's asymmetry argument, so the error is material.

2. "The bidding and cash-flow gaps are real but fixable on an ordinary timeline: a bookkeeper and a line of credit cover the books and the seasonal dip from day one, and bidding is a skill you can learn under supervision before you're the one signing checks."
   Wrong: "cover ... the seasonal dip from day one" is stated as settled fact. Nothing in the memo or the spec shows a line of credit is available, or that it would be enough. The memo contradicts itself here. Its walk-away conditions say: "or after the down payment you wouldn't have both a household cushion and separate working capital for the business's first slow stretch." If the line of credit covered the dip, that condition would rarely bind. This is an overstated claim and an internal inconsistency, and it bears directly on the decision.

3. "A seller who insists on all cash at closing and won't stand behind his own claim about client loyalty is answering your question for you."
   Wrong: this is a step that does not follow. Refusing a note or earn-out does not show the seller believes clients will leave. The memo's own counter-position grants that refusing to price in the risk can be the seller's "rational move." The sentence turns a possibly rational refusal into evidence of a specific belief, and it is presented as conclusive.

Minor errors (fix or log as open items):

4. "Eight years running crews is real, earned evidence — you know the work, the crews, and the client list, which is exactly what makes you a better buyer than any outsider"
   Overstated: "better buyer than any outsider" is an absolute comparison the memo does not support. Outsiders may bring capital, experience or other advantages.

5. "It can't be bought, and reading his numbers won't resolve it"
   Internally unclear: the memo then proposes tying part of the price to revenue that persists, which is a way of paying for the loyalty outcome. Either say the loyalty itself cannot be bought, or drop "can't be bought."

6. "High: that client concentration — who each relationship actually belongs to — is the single fact most likely to move this decision, since it's the gap you already named"
   Conflation: the spec says the user named loyalty ("whether clients are loyal to the business or to him"), not concentration. The memo treats the two as one gap without saying so. The confidence level is also high for a claim that depends on numbers the memo lists as unknown.

7. "you already have the access to build it"
   Unsupported: the spec does not say the user can see every account's contact history or who deals with each one. This assumption is presented as fact.

8. "a fixed loan payment against falling revenue erodes your earnings far faster than revenue itself falls"
   Unsupported: "far faster" is a quantitative-sounding claim with no support, though the direction (operating leverage) is plausible.

Not an error, but unverified: "A loan for buying an existing small business is typically backed by a personal guarantee — often secured against major personal assets, a house included..." This is a general factual claim about lending with no source in the memo or the spec. I could not check it, so it is unverified.

Dissent check: PASS. The counter-position states the strongest case against the recommendation fairly. It names the conditions under which the counter wins and gives a concrete alternative (accept near-original terms, or walk away now). It is not a strawman, though error 3 above is partly a problem inside it.

Coverage against the spec: PASS. The memo answers both questions. It says the leaning is reasonable as a starting instinct and not yet as grounds to sign, and it gives concrete walk-away conditions in "What to do" (seller won't open books or allow a bid cycle, concentration with his-only clients, no risk-sharing on price, no household cushion or working capital after the down payment).

Judgment, not verified: whether restructuring is the right call, the emphasis on client loyalty as the central question, and the recommendation to test before committing. These are labelled as judgment in the memo's Confidence section, and the checks above cannot settle them.

Required fixes before a PASS: correct item 1 (remove "your job stay intact" and "nothing else", or qualify them against the seller-sells-elsewhere outcome), rewrite item 2 so it does not state the line of credit covers the dip as settled fact and is consistent with the working-capital walk-away condition, and rewrite item 3 so it does not treat refusal of risk-sharing as proof of a belief about client loyalty.

---

## Checker 7 (Memo 6)

VERDICT: FAIL

ERRORS (checked against the spec and the memo's own figures)

1. Material. Quote: "Even at 100% margin and no discounting, revenue through month 36 ($5,287) only just covers $5,000. So payback rests entirely on the unobserved tail, whatever the margin."
Wrong: the memo's own figure shows $5,287 is above $5,000, so at 100% margin payback happens inside the 36 months already observed. The memo's Why section also says recovering $5,000 within 36 months needs "roughly 95% margin", so at high margins the tail is not needed. "Whatever the margin" contradicts this, and "So" does not follow from "only just covers". Corrected version: at 75% margin, payback relies on the tail; at about 95% or higher it does not.

2. Material. Quote: "Treat the $15,000 as a best-case, revenue-based model output" and, under Confidence, "High: the $15,000 is a best-case figure".
Wrong: this is an overstated claim with High confidence. The memo's Risks section says the tail could be better than the formula assumes, which would put true value above $15,000, and the counter-position says $15,000 "could be about right or even low". Only the margin side is biased high (revenue, not margin). The tail's direction is unknown, so "best-case" is not supported. The memo should call it a revenue-basis figure that overstates on margin, with the tail direction unknown.

CHECKED AND CONSISTENT (no error)
- $180 / 0.012 = $15,000. 1/0.012 = 83 months; 83/36 = 2.3x.
- 36-month revenue at constant churn, about $5,289 (memo $5,287); 5-year $7,730; share beyond month 36 about 65%, about $9,700.
- 75% margin undiscounted: 36-month about $3,967 (memo $3,965), 5-year $5,798, endless $11,250.
- 75% margin, 10% discount: 36-month about $3,494 (memo $3,498), 5-year about $4,752 (memo $4,763), endless about $6,784 (memo $6,813). Gaps are 0.1 to 0.4% and depend on timing convention, so not flagged.
- LTV:CAC 3.0, 2.25, 1.36, 0.70 at $5,000 CAC: correct.
- Revenue payback about 34 months; margin payback about 49 months; first-year revenue $2,023 (about 40%); 95% margin needed for 36-month payback: all correct.
- Ceiling rules of thumb: 3:1 on discounted LTV gives about $1,170 to $2,270; 24-month margin payback about $2,830: consistent with "$1,200 to $2,300" and "$2,800".
- Step 6's $5,000 threshold matches the 95%-margin figure, so it is consistent.

DISSENT CHECK: PASS. The strongest counter-position (the tail is unobserved, survival curves flatten, a constant-churn formula understates) is stated fairly, with its conditions for winning (churn below 1% after month 12, later cohorts matching, margin about 80% or better). Note that the "best-case" label in error 2 conflicts with this counter-position.

UNVERIFIABLE (outside the spec, labelled as unverified in the memo; not errors)
- "Subscription survival curves typically flatten with tenure" (general industry claim).
- "annual-contract customers who can only leave at months 12, 24 and 36" (depends on the user's contract terms, which the spec does not state).
- "bids, agency fees and commissions may drift toward it" (hedged judgment).
- The 75% gross margin placeholder and the 10% discount rate (labelled as placeholders).

JUDGMENT (not verified): whether holding the ceiling and running the cohort analysis is the right call, and the weighting of cost of waiting against cost of being wrong.

SELF-CRITIQUE: The memo is otherwise careful. It labels its assumptions and gives a low/base/high range. Its two weak points are the two errors above, and both concern how confidently it states the result.

---

## Checker 8 (Memo 5)

VERIFICATION REPORT: memo against spec

ERRORS (listed first, quoted, one per line)

1. "Sixty engineers merging for two weeks produces a backlog several times the size of a normal release, written by people who by thaw day are weeks removed from their own code and reviewed, on both ends of the freeze, under the kind of time pressure that thins out review quality." The spec gives no backlog size, no release-size comparison and no review-quality data. These are stated as fact with no support. Material: the batching mechanism rests on them.

2. "Nothing in the policy discourages the batch from forming, either: the engineers merging code during the freeze aren't the ones carrying the January on-call pager, so there's no feedback loop pushing back on how much accumulates behind the gate." The spec says nothing about who carries on-call or any feedback loop. This is an unsupported factual claim used as a causal step. Material.

3. "That mechanism alone would produce exactly what's observed: a different named bug in every postmortem, because the postmortems are diagnosing symptoms of a shared structural cause ... that no incident-review template records." This is an overstated claim. The memo later says a different root cause in each postmortem "is equally consistent with" the calendar explanation, and its Confidence section rates the mechanism only "Medium". The sentence contradicts both. Material: it tells the reader the batch explanation is the cause.

4. "moving risk from a high-traffic fortnight run by a skeleton crew to a lower-traffic, fully-staffed one is what the freeze is designed to do" The memo elsewhere says January has "thin post-holiday staffing" and "staff returning rusty or new", and the Risks section lists "thin staff" as a January risk. "Fully-staffed" contradicts the memo's own text. The spec says nothing about staffing. Material: it is the premise of the "freeze is working" argument.

5. "Because it costs little and makes things strictly safer either way, build the metered thaw in parallel rather than waiting on the audit" and "staged, canaried delivery is strictly safer than today's big-bang release". The memo's own Risks section says "Staggering by service without checking cross-service sequencing or migration order can turn a controlled thaw into a broken one." So staged delivery is not strictly safer. "Costs little" is never estimated: the only cost given is "a few engineer-days" for the audit, not the thaw build. Material: this is the stated reason to build now.

6. Opening sentence: "Run the cheap diagnostic before committing to the expensive fix" versus "start building a metered thaw", and "the audit and the thaw build run in parallel rather than in sequence". The headline says to wait for the diagnostic before the expensive fix. The body says to build the expensive fix in parallel without waiting. These point the reader in opposite directions. Material.

7. "That answers the actual question: if most January impact traces back to freeze-period merges and scales with the size of each service's backlog, the batching mechanism is confirmed and worth the bigger investment below" An audit that tags triggers on about four Januaries can make the mechanism supported, not confirmed. "Answers the actual question" also overstates it, because the memo says no one has the backlog data yet. Material: "confirmed" licenses the larger investment.

8. "Nothing in the current process — no field for deploy size, trigger source, or days-since-merge in the incident template — ... three years of postmortems have been diagnosing individual bugs without ever recording the one variable that would show whether they share a cause." The spec does not describe the incident template. The memo asserts its contents and that nothing was ever recorded, with no check. It also names three variables and then calls one of them "the one variable". Minor to material: it is a factual claim the reader cannot verify from the spec.

9. "Every one of those produces its own distinct bug too" This is overstated. The spec does not say each calendar risk produces a bug every year. Minor.

10. "the fix-forward often becomes the next incident" The word "often" has no support in the spec. Minor.

11. Scope inconsistency: the Recommendation says "tag three years of January incidents (and this year's)", while the What to do section says "backfill it for the last three Januaries". Those are different sets of Januaries. Minor open item.

DISSENT CHECK

The memo recommends a diagnostic plus a parallel thaw build. Its "Strongest counter-position" section argues the freeze is doing its job and that thaw tooling would solve a problem the org may not have. That is a real and fairly stated case, not a strawman. It argues mainly against the diagnosis, and it applies to the thaw build only through its conditional "This wins if" clause. The Risks section adds the thaw's own failure modes. Result: passes, with that note.

COVERAGE (judgment, not an error)

The spec asks what is actually going wrong and whether the freeze protects or only moves risk. The memo answers the first only by proposing an audit, and the second only as "Low" confidence. It says so openly. This is an honest gap, not an error, and it is labeled as judgment.

VERDICT: FAIL

Items 1 to 7 are material and each would change what the reader believes or does. To clear the FAIL, the memo needs to: reconcile the headline with the parallel build; drop "strictly safer" and "costs little", or support them; soften "confirmed"; remove or source the backlog, on-call, review-quality and template claims; fix the "fully-staffed" contradiction; and align the set of Januaries. Items 8 to 11 are minor and can be logged as open items. Re-run this check after those fixes.

---

## Checker 9 (Memo 7)

VERIFICATION REPORT: decision memo on how to word and route a correction to a closed-office analysis

ERRORS (listed first, quoted)

1. "The note should not be written to try to change the decision, because it almost certainly won't, and that shouldn't be its job." (Why section, final paragraph.) Material. "Almost certainly" is a confident prediction about how leaders will react. Nothing in the spec supports it, and the memo's own Why section argues only in general terms. This prediction is the stated reason for leaving decision-relevance out of the note.

2. "doesn't reopen a decision that in practice won't be reopened" (Risks section, second paragraph.) Material. Same unsupported prediction, stated as fact. It is used as a reason against the wide written note.

3. "If it later turns out more should have gone in writing to more people, that's a recoverable follow-up conversation, not a crisis" (Risks section, final paragraph.) Material. It tells the reader the cost of under-disclosure is low. The memo's own Why and Risks sections say the opposite: that a second correction "costs far more credibility than the first" and that a delayed disclosure "reads as concealment."

4. Step does not follow from the reasoning. The Why section says: "if the error isn't isolated to the closed office, this stops being one analyst's note to send and becomes a formal restatement someone more senior should own." The What to do section then says: "Then send the written correction to exactly the people who received the original analysis, promptly once the numbers are confirmed." That instruction has no branch for the non-isolated case, so the analyst is still told to send it. Material, because it decides who sends the correction.

5. "High — plain, ownership-first register beats both a bare technical notice and an apology-centered message" (Confidence section.) Minor. The memo offers no evidence for the comparison, and the rules treat this as a judgment call. High confidence is overstated.

6. "the same delay reads as concealment regardless of why you waited" (Risks section, third paragraph.) Minor. "Regardless of why" is an absolute claim with no support.

DISSENT CHECK: Passes. The Strongest counter-position section states the case against omitting decision-relevance from the written note fairly. It is not a strawman, and it names the condition under which it would win.

COVERAGE AGAINST SPEC: The memo answers the tone question (plain first-person, one line of apology for the error, no apology for the closure). It answers the question about saying whether the decision would have changed (no). It answers the "how do these go wrong" question (the Risks section). Coverage is complete.

UNVERIFIABLE (outside the spec, not counted as errors; logged as open items): the general claims in the Why section that corrections are "generally read far better," that voluntary correction "typically costs less," that organizations "generally update the forward-looking numbers" rather than reverse, and that approvers "tend to defend" a decision. Also the claim in the Cost of being wrong section that "the irreversible decision ... was made three months ago." The spec says only that the analysis was written three months ago.

JUDGMENT (stays labeled judgment, not verified): whether decision-relevance belongs in the written note, the manager-first sequencing, and the verbal channel. The memo's own Confidence section already flags the first as a medium-confidence call.

VERDICT: FAIL. Items 1 to 4 are material. Items 1 and 2 rest on an unsupported prediction that drives the central recommendation. Item 3 understates a risk the memo itself describes. Item 4 leaves the sending instruction unresolved for the case the memo itself identifies as serious. Fix these and re-run the check.

---

## Checker 10 (Memo 1)

VERIFICATION REPORT: decision memo on the $15,000 customer LTV and the $5,000 CAC ceiling

ERRORS (checked against the spec and the memo's own numbers)

1. "What the company's own history actually supports, using only the given numbers: applying the same 1.2% rate to the 36 months that have actually elapsed ... gives cumulative revenue per customer of about $5,300"
   Wrong: the $5,300 is a model projection that applies the 1.2% churn rate, the assumption the memo is questioning. No observed customer history was given. Recomputing it, 180 x (1 - 0.988^36) / 0.012 = about $5,290, so the figure is right but it is modeled, not historical.

2. "Against a $5,000 CAC: no customer relationship this company has ever had has generated enough revenue, let alone enough profit, to fully repay it."
   Wrong, and contradicted by the memo's own figure. The memo puts 36-month cumulative revenue at about $5,300, which exceeds the $5,000 CAC. The claim is also stated as observed fact about the company's history, when it comes from the model. This is a headline argument against the $5,000 ceiling, so the error is material.

3. "moves this from 'somewhere between a third and a half of $15,000' to an actual, company-specific number."
   Wrong: the memo's own bounds run from about $2,800 to $5,300, which is roughly 19% to 35% of $15,000. "A third to a half" ($5,000 to $7,500) does not match them. The stated range overstates the upper end and omits the lower one, so the reader misjudges how uncertain the estimate is. Material.

4. "Set the ceiling from a payback test ... the cost recoverable, in gross profit, within a horizon you're willing to wait — 18–24 months is a common bar ... On these numbers that lands near $2,800–3,000, using the 75–80% margin assumption above."
   Wrong for the 18-month end. Using the memo's own churn curve and margins, 18-month cumulative revenue is about $2,930, or about $2,200 to $2,350 gross profit at 75% to 80% margin. Only the 24-month bar gives $2,800 to $3,000 (about $2,830 to $3,020). The stated range should be about $2,200 to $3,000, and the recommended ceiling depends on which horizon is chosen. Material, because the ceiling is the memo's headline number.

CHECKED AND CORRECT (no error found)
- $180 / 1.2% = $15,000; 1/0.012 = 83 months; 83 - 36 = 47 months.
- Flat-churn survival figures: 86% at 12 months, 75% at 24, 65% at 36.
- $5,000 = $15,000 / 3.
- Revenue versus gross profit and undiscounted versus discounted cash flows both only shrink the number. This follows from margin below 100% and positive discount rates.
- The "$4,000–4,200" margin-adjusted 36-month figure is consistent with $5,300 at 75% to 80% margin (about $3,975 to $4,240).

DISSENT CHECK
The memo has a "Strongest counter-position" section. It is stated fairly and in strong form, names the conditions under which it wins (flat or declining hazard by tenure, intact margins), and says which step would settle it. It is not a strawman. Its quoted phrase ("doesn't show that customers leave...") has no source in the spec, so I could not confirm the quotation.

JUDGMENT, NOT VERIFIED (cannot be settled by this check)
- The 75% to 80% margin is labeled illustrative in the memo, so it is not a verified input.
- The 18 to 24 month payback bar and the "common bar" claim.
- The "1 to 5 analyst-days" estimate.
- Whether the $2,800 to $3,000 ceiling is the right call. The memo marks this as Medium confidence, which is appropriate.

VERDICT: FAIL
Items 2 and 4 would change what the reader believes and does. Item 2 wrongly says no customer has repaid CAC when the memo's own figure shows it can. Item 4 gives the wrong ceiling for the 18-month bar. Items 1 and 3 also misstate the evidence base and the uncertainty range. The memo needs these four sentences corrected and the check re-run.

---

## Checker 11 (Memo 4)

VERIFICATION REPORT

Overall verdict: FAIL

Both spec questions are answered (is the leaning reasonable; what would make you walk away). The problems below are in the reasoning and in claims the spec does not support.

ERRORS (quoted sentence, then what is wrong)

Material

1. "A seller who insists on all cash at closing and won't stand behind his own claim about client loyalty is answering your question for you."
Overstated. Refusing a note or earn-out is consistent with many things: a seller who is confident clients stay but wants certainty, a seller who wants cash for reasons unrelated to loyalty, or a seller who distrusts the buyer. The memo's own counter-position says that cash at closing is the seller's "rational move" when loyalty risk is real, and it also lists other reasons a seller might prefer a fast deal. Presenting the refusal as a settled answer to the loyalty question is a step that does not follow. It matters because the memo uses it as a walk-away signal for the reader.

2. "Walking away, by contrast, costs you an opportunity and nothing else; your savings and your job stay intact, and the option to revisit this deal on better terms, or find a different one, stays open."
Overstated, and it conflicts with the memo's own content. The spec says the user has worked at the business for eight years and that the boss is retiring. If the user walks away, the seller may sell to someone else or close the business, and the user's job would be at risk. The counter-position names that exact outcome ("the real chance he sells to someone else or closes the doors"). "Nothing else" is absolute and wrong. It matters because the memo's central asymmetry argument depends on walking away being cheap.

Minor

3. "Running crews well doesn't touch any of the three, and by your own account you have no track record on any of them yet."
Contradicts the Confidence section, which says the user's operational experience is "real and relevant." Crew productivity and labor cost bear directly on bid pricing, and the memo's own Why section credits the user's knowledge of the client list as useful to a buyer. "Doesn't touch" should be softened to "does not by itself answer."

4. "a bookkeeper and a line of credit cover the books and the seasonal dip from day one"
Overstated. The spec gives no information on credit availability or on the seasonal cash gap, and the memo itself lists the cash-flow numbers as unknown. A line of credit is not guaranteed and would depend on the same lender and guarantee the memo warns about. "Cover" should be "could help with."

5. "a fixed loan payment against falling revenue erodes your earnings far faster than revenue itself falls"
Overstated. "Far faster" is a quantified-sounding claim with no numbers, and the memo lists the loan terms and margins as unknown. Operating leverage does make fixed costs amplify revenue changes, but the size of the effect is not established.

6. "It can't be bought, and reading his numbers won't resolve it"
Absolute rhetoric about loyalty. The sentence is judgment, but "can't be bought" is stated as fact. Minor.

UNVERIFIABLE (not in the spec, not contradicted by it; the recommendation rests on some of them, so they are open items)

- "He gets paid in full at closing and walks away with no further stake in whether clients stay." The spec says the purchase "would take most of our savings plus a bank loan" but does not state payment terms or that the seller has no continuing stake. The "larger risk" argument rests on this. Open item: confirm the payment terms.
- "A loan for buying an existing small business is typically backed by a personal guarantee" and "a house included if you own one outright or jointly, in which case your partner would need to sign too." General lending practice, not in the spec. The "larger risk" section depends on it. Open item.
- "The loan gets sized on his historical cash flow" and "your eight years reads to a lender as management experience." General lending practice. Open item.
- "you already have the access to build it" (the list of clients by who deals with them). The spec says the user knows most clients by name, but not that the user has access to account or billing records. Open item.

DISSENT CHECK: PASS. The memo states a strongest counter-position, and it is stated fairly. It gives the conditions under which the seller-first view wins, and it says what the reader should watch for (the seller's response to the first ask). It is not a strawman.

SELF-CRITIQUE NOTE: The recommendation (restructure first, walk away otherwise) is judgment. A clean error list does not confirm it is the right call, and it is labeled as judgment, not verified. The Confidence labels (High/Medium/Low) are self-assessments and were not checked.

SUMMARY: Two material errors (items 1 and 2) make this a FAIL. Items 3 to 6 are minor and should be fixed or logged. Four unverifiable claims are open items. Fix items 1 and 2 and re-run this check before the memo is treated as clean.

---

## Checker 12 (Memo 8)

VERIFICATION REPORT: decision memo on how to correct a closure analysis

ERRORS FOUND (quoted, with what is wrong)

1. "Put the corrected numbers first, then one sentence of first-person ownership ("the error was mine")." (Recommendation)
   The draft template contradicts this. Its first paragraph is "I found an error in the analysis I wrote on [date] for the [Office] closure decision. The error was mine: ..." and the corrected figures come after it in "Corrected: [Office]'s operating loss...". The ownership sentence precedes the numbers, the reverse of the stated order. A reader who copies the template sends the message in the order the memo says not to use. Severity: material, because it changes the message the reader sends. Fix: reorder the template so the "Corrected:" paragraph comes before the ownership sentence, or change the recommendation to match the template.

2. "Every reader will take the first as the second, and whatever the number shows, it will be quoted back in any dispute over the layoffs." (Strongest counter-position)
   Absolute claim ("Every reader", "whatever") with no support in the memo. The argument needs only "readers are likely to" or "many readers may". Severity: minor, but it sits in the section meant to state the opposing case fairly, so it overstates that case.

3. "Executives will work out which, and a vague number reads as minimizing." (Why section, on the two readings of "40%")
   Stated as certain. It is a prediction about other people. Severity: minor. Fix: "Executives are likely to work out which."

4. "A fix that wasn't independently checked and needs a second correction does more damage than the first error." (Order matters section)
   Categorical comparison with no support in the memo, and it is judgment rather than something checkable. Severity: minor. Fix: soften to "usually does more damage" or label it as judgment.

Arithmetic checked, none found: "the true loss is about 71% of what was reported (29% lower)" is correct (1/1.4 = 0.714). "the true loss is 60% of what was reported (40% lower)" is correct under the stated reading.

Errors list otherwise: none found.

UNVERIFIABLE (outside the spec; not counted as errors)
- "they made it with inputs beyond your spreadsheet" (Why section). The spec does not say what inputs the executives used. Flagging this as an open item is appropriate.
- "It may also put an admission of fault in writing" is already labelled unverified in the memo, and HR/legal treatment is not in the spec.
- "Corrections an author volunteers typically cost less than ones someone else discovers" is already labelled as a general pattern, unverified.
- Whether a numeric closure threshold exists in the original memo, whether other models share the formula, and the legal position are listed as material unknowns. They are open items, not errors.

DISSENT CHECK
The memo states a counter-position: the criteria line is a trap, and the plain corrected-figures message with an ownership sentence wins outright if there is no numeric threshold or if HR/legal advise against analyst commentary. This is a fair statement of the opposing case, and it gives the conditions under which the opposing case would win. It is weakened only by the absolute wording in item 2 above.

CONFIDENCE LABELS
"High" for "one sentence of ownership beats both" and "Medium" for the criteria line and the timing are judgments. They are labelled as judgment and I have not verified them.

VERDICT: FAIL
Reason: item 1 is a material error, because the template contradicts the memo's own stated order. Items 2 to 4 are minor overstatements and should be fixed or logged as open items before the verdict can be clean. Once item 1 is fixed, the memo should be re-checked against the same list.

---

## Checker 13 (Memo 3)

VERIFICATION REPORT

Errors (listed first, quoted):

1. MATERIAL. "Cost of being wrong: everything short of signing is cheap and reversible." This is contradicted in the same paragraph: "Exclusivity or other binding terms can lock you in before closing, which is why a lawyer reviews them first." Exclusivity is short of closing and is not reversible, so the claim that everything short of signing is reversible is wrong. A reader could sign exclusivity believing it is cheap to undo. Fix: limit the claim to steps before any binding term, and say that exclusivity is the exception.

2. MINOR. "Coverage would also have to be 1.5 times or better after the stress test." This conflicts with the walk-away rule, "profit covers the loan payments by less than about 1.25 times," and with "Treat 1.5 times as the comfortable target." The memo gives 1.25 as the walk-away line and 1.5 as a target, but this sentence makes 1.5 a requirement in the flip scenario. The gap between 1.25 and 1.5 is left unclear. Fix: state one threshold for each purpose, or say which applies in the flip case.

3. MINOR. "A bank loan on a deal like this will almost certainly carry your personal guarantee." This is an overstated claim with no support in the memo. It also conflicts with the memo's own unknowns: "Material unknowns: the price, and the loan terms including whether it is SBA-backed." The memo cannot be near-certain about loan terms it lists as unknown. Fix: soften to "likely" or "may," and mark it as unverified.

Unverifiable (not in the spec, no source named, not checked):

- "A seller note that counts toward your required down payment has to stay unpaid for the whole loan term, often around ten years. It can cover at most half of that down payment." The memo says it came from "law-firm and lender summaries of the SBA's current rules in October 2026," but names no source and gives no link. I could not confirm either point. The memo labels it Medium confidence, which is appropriate, but the basis cannot be checked from the page.
- "The fee is small next to the deal." No cost data is given.
- "Selling to the employee often means the buyer has the least information, the most loyalty and the strongest fear of losing the job." This is a generalization with no support on the page. It is hedged with "often," so it is not an overstatement, but it is unsupported.

Checks that passed:

- Spec coverage: the memo answers both parts of the question. It says the leaning is reasonable as a reason to pursue the deal, not yet a reason to sign, and it gives walk-away conditions.
- Consistency with the spec facts: eight years, running crews, knowing clients, no experience with books, bidding or cash flow, a supportive but nervous partner, and a boss who is retiring all match the spec.
- Dissent check: the "Strongest counter-position" section states a real case against the recommendation (do not buy client goodwill; the buyer has the least information and bears the loyalty risk) and gives conditions under which it wins. It is not a strawman. The memo does not rebut it, which the check does not require.
- Confidence labels: the memo labels the 1.25, 1.5 and 20% figures as rules of thumb, and labels the earn-out question as unverified.

Overall verdict: FAIL. Item 1 is material because it can change what the reader does (signing exclusivity on the belief that it is reversible). Items 2 and 3 are minor. Fix item 1 and re-run the check. Items 2 and 3 should be fixed or logged as open items. The unverifiable SBA rule should stay labeled as unverified.

---

## Checker 14 (Memo 2)

VERDICT: FAIL

ERRORS (quoted, one per line; material errors are marked)

1. MATERIAL. "This is why every review blames a different bug." States the batch as the settled cause of the varying bug reports. The memo later says "The batch is the leading explanation, not a proven one," so the sentence overstates its own evidence.
2. MATERIAL. "The freeze is moving risk into January and concentrating it." This headline is stated as fact. The memo's own Confidence section rates the batch cause only "Medium" and the December-protection trade-off "Low," and the counter-position says "the freeze is not what is hurting you." The claim should be hedged to match.
3. MATERIAL. "What you have is the moved risk plus a concentration that makes it harder to attribute and slower to fix." The spec gives no time-to-restore data, and the memo's own Material unknowns list includes "whether 'worst' means incident count or minutes down." "Slower to fix" is unsupported and presented as established.
4. Overstated. "One check, merge date against deploy date, settles most of it." The Risks section says "Incident records may be too thin to link causes to merge dates, so the check could be inconclusive." "Settles most of it" contradicts that admission.
5. Minor, step does not follow. "If calendar-triggered faults dominate, it would leave January untouched, so both months could get worse." January being untouched does not make January worse. The "both" needs the later point that a staged thaw adds release events in the return week, but the sentence does not make that link.
6. Minor, internal conflict. "It helps under the batch and drift explanations, not under year-boundary faults or staffing." Step 4 says to "Start only when authors and on-call are back," which is a staffing mitigation, so the thaw does address staffing in part.
7. Minor, feasibility. "decide these changes at least a month before the freeze starts." The spec places the freeze in the last two weeks of December, and today is 2026-11-22. A month before a mid-December start has already passed. The memo does not account for the calendar. Log as an open item.

Checks that pass or are not errors:
- The spec is covered: the memo gives a recommendation, reasons, a test, and a counter-position.
- The dissent check passes. The counter-position is stated fairly, not as a strawman, and says what evidence would make it win.
- The arithmetic claim about pairwise interactions growing with the square of the number of changes is correct.

UNVERIFIABLE (not in the spec; not confirmed against the spec or the user's facts; the recommendation rests partly on several of them, so they are open items)
- "That batch has never run together under production conditions."
- "They are usually tested against main, not against production's config, data and flag state."
- "nobody tested those combinations together."
- "rollback is all-or-nothing."
- "authors merged weeks ago, some are typically on leave, and on-call is typically thin in the first days of January." The memo says the roster will show this.
- "Google's SRE book reports that roughly 70% of outages are due to changes in a live system." No source was fetched in this check, so the figure was not confirmed.

Judgment items left unverified, not errors: whether the staged-thaw plan is the right call, the cost trade-off for December, and whether freezing at all is protective.

Open items for the author: fix errors 1 to 4 and resolve the timing in 7 before the memo is relied on. Items 5 and 6 are minor and should be fixed or logged.

---

## Checker 15 (Memo 6)

VERDICT: FAIL

ERRORS (checked in order, quoting the sentence):

1. Material. "Treat the $15,000 as a best-case, revenue-based model output, not a measured value." The memo's own analysis does not support calling $15,000 a best case. Its churn section says that if 1.2% is net revenue churn, "Every figure built on it, the $15,000 included, is then too high." Its counter-position says a constant-churn formula "often understates the tail" and that on revenue alone $15,000 "could be about right or even low." Calling it a best case tells the reader it is an upper bound, which the memo elsewhere contradicts.

2. Material. "So payback rests entirely on the unobserved tail, whatever the margin." This is false on the memo's own numbers. The preceding sentence says that at 100% margin, 36-month revenue of $5,287 covers $5,000, and line 35 says recovering $5,000 within the 36 observed months needs "roughly 95% margin." At 95% or more, payback falls inside the observed window and does not depend on the tail. The reader would wrongly conclude that no margin level pays back within observed data.

3. Material. "High: the $15,000 is a best-case figure, about 65% of it beyond any observed tenure, and revenue payback on $5,000 is about 34 months after churn. This is arithmetic on your own numbers." The "best-case" part is not arithmetic, and it carries the same error as item 1. It is labelled High confidence on a judgment, so the stated confidence is overstated. The 65%, 34-month and related figures do check out as arithmetic.

4. Minor, open item. "you would only learn the truth about months 37 and beyond one to three years later." A customer acquired at month 0 reaches month 37 after about 3.1 years, so "one to three years" understates the wait for the first cohort. Fix the range or say it is the time to first observations.

CHECKS THAT PASSED:
- Arithmetic re-run cold: $180/0.012 = $15,000; 83-month expected life; survival to month 36 about 64.7%; 36-month revenue about $5,287; 5-year revenue about $7,728; endless 75% margin $11,250; discounted margin figures $3,498, $4,763 and $6,813; LTV:CAC ratios 3.0, 2.25, 1.36 and 0.70; payback 33.6 months on revenue and 48.7 months at 75% margin; first-year revenue about $2,023; the ceiling ranges $1,166 to $2,271 and about $2,829 at 24-month margin payback. All consistent with the memo's stated figures.
- No overstated "proves" or "always" wording was found beyond the items above.

DISSENT CHECK: Present and fair. The "Strongest counter-position" section states the case for the tail being better than the formula with its own conditions (churn below 1% after month 12, later cohorts matching earlier ones, margin of 80% or more). It is not a strawman. The phrase "Subscription survival curves typically flatten with tenure" is general and is labelled unverified.

OMISSIONS (coverage of the spec, not errors): The memo answers both parts of the spec: how far to trust $15,000 and what a more honest estimate looks like. It gives a recommendation, reasons and a counter-case.

JUDGMENT, NOT VERIFIED: Whether holding the ceiling and stepping up by channel is the right call, the placeholder 75% margin and 10% discount rate, and the claim that the marginal channels are likely worse than the blend. These are labelled in the memo as judgment or unverified, and this check cannot settle them.

FIX REQUIRED FOR PASS: Replace "best-case" in the Recommendation and Confidence sections with wording such as "an upper-bound revenue figure on one basis, with the sign of the error uncertain." Rewrite the payback sentence to state that payback within 36 months needs about 95% margin and otherwise depends on the tail. Then re-run this check.

---

## Checker 16 (Memo 1)

VERDICT: FAIL

ERRORS (quoted sentence, then what is wrong)

Material:

1. "What the company's own history actually supports, using only the given numbers: applying the same 1.2% rate to the 36 months that have actually elapsed ... gives cumulative revenue per customer of about $5,300"
   and "That's close to a ceiling on what's demonstrated, not a floor"
   Overstated. The $5,300 is a model output: it assumes 1.2% monthly churn holds for months 1-36. The spec and memo give no observed per-customer revenue or retention, so nothing is demonstrated or shown by history. The memo itself says the 1.2% rate is unconfirmed. (I checked the arithmetic: 180 x (1 - 0.988^36) / 0.012 is about $5,288, so the number is correct as a model output.)

2. "Treat it as a ceiling on what's proven, not a target."
   Same error as item 1 in the "What to do" section. A modeled figure is called proven.

3. "Against a $5,000 CAC: no customer relationship this company has ever had has generated enough revenue, let alone enough profit, to fully repay it."
   Unsupported factual claim about actual customer history. The spec gives no per-customer revenue data. The only revenue figure in the memo is the modeled $5,300, which the memo itself places above $5,000, so this sentence rests on a fact the memo does not have. It is used as a main argument against $5,000.

4. "Set it near what a 24-month, margin-adjusted payback actually supports — roughly $2,800–3,000 at a plausible 75–80% gross margin"
   and "18–24 months is a common bar ... On these numbers that lands near $2,800–3,000"
   Overstated and does not follow. The memo's own "Confidence" section calls the 75–80% margin "illustrative, unconfirmed", so "actually supports" overstates it. Also, the 18–24 month range does not produce $2,800–3,000 across its span. Using the memo's apparent method (1.2% churn, monthly gross profit of $135–144), a 24-month bar gives about $2,830–3,020, but an 18-month bar gives about $2,200–2,350. The stated range fits only the 24-month end. The method is not stated in the memo, so the reader cannot reproduce the figure.

5. "somewhere between a third and a half of $15,000"
   Misstates the memo's own range. A third is $5,000 and a half is $7,500. The memo's estimates are about $2,800–3,000 (roughly a fifth) and $5,300 (roughly a third). The stated range overstates how far the correction moves the number and misdescribes the memo's own results.

Minor (logged as open items, not material on their own):

6. "the 36-month-capped figure becomes roughly $4,000–4,200"
   At 75% margin this is about $3,975 and at 80% about $4,240. The top of the range is slightly off.

7. "The same guardrail applied to the bounded $5,300 figure would put the ceiling in the low thousands"
   $5,300 / 3 is about $1,770, which is under $2,000. "Low thousands" is loose wording.

CHECKED AND CORRECT

- $180 / 1.2% = $15,000; implied lifetime 1/0.012 = 83.3 months, "nearly seven years" (about 6.9 years).
- 83 - 36 = 47 months beyond observed history.
- Flat 1.2% survival: about 86.5% at 12 months, 74.9% at 24, 64.7% at 36, as stated (86/75/65%).
- $5,000 = $15,000 / 3.
- The "margin and discounting only shrink the number" reasoning is valid for positive values.
- The 36-month cap assumption is stated as an assumption elsewhere in the memo.

DISSENT CHECK: PASS. The counter-position in "Strongest counter-position" states a fair case against the recommendation, including what evidence would overturn it (flat or declining hazard by tenure, intact margins). It is not a strawman.

UNVERIFIABLE (outside the spec, not errors)

- "a standard 3:1 LTV:CAC guardrail": an industry convention not in the spec; cannot be checked here.
- The quoted phrase in the counter-position, "doesn't show that customers leave. It just means the company is three years old...", is in quotation marks with no source given. The spec does not contain it, so its attribution cannot be confirmed.
- The "18–24 month payback bar" being a "common" or "reasonable default" is judgment, not checkable against the spec.
- Whether $2,800–3,000 (or any ceiling) is the right call is judgment and stays unverified.

Items 1 through 5 must be fixed and the check re-run before this memo can be called clean.
