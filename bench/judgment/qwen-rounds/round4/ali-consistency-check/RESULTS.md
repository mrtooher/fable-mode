# Consistency check for wise-men-flash 0.2.0 — results (2026-10-22)

Plan: [`PLAN.md`](PLAN.md), written and the blind order fixed (`order.txt`, seed 20261022) before any run. New answers: `answers/`. What each judge read: `blinded/`. What each judge wrote: `judgments/`. The contradiction count: [`classification.md`](classification.md), by a separate blind classifier.

## Primary measure: internal contradictions (summed over both judges)

| question | 0.1.0 (round 5 answer) | 0.2.0 (new run) | fewer? |
|---|--:|--:|---|
| R502 deploy freeze | 5 | 1 | yes |
| R504 lifetime value | 2 | 3 | no |
| R506 correction memo | 5 | 1 | yes |
| R508 buying the business | 2 | 1 | yes |
| **total** | **14** | **6** | **3 of 4** |

The pre-registered bar was fewer on at least three of the four questions: **met**. R504 did not improve: the new memo still overstates in one place ("payback rests entirely on the unobserved tail, whatever the margin", right after showing month-36 revenue covers $5,000 at 100% margin), which both judges caught. The old memo's headline errors are gone in the new runs: R502's "strictly safer", R504's "no customer has ever repaid $5,000", R506's "nothing about the tone of this note is irreversible", R508's "your savings and your job stay intact".

## Secondary measures (mean of 2 judges × 4 questions)

| | correctness /5 | total /25 |
|---|--:|--:|
| 0.1.0 | 3.25 | 19.75 |
| 0.2.0 | 4.00 | 23.12 |

Correctness rose from 3 to 4 on R502, R504 and R508 with both judges, and stayed at 4 on R506. All errors listed in PASS 0, of either kind: 33 for 0.1.0, 18 for 0.2.0.

## Deviations and limits

- Two-answer packets score differently from round 5's nine-answer packets: the same four 0.1.0 answers averaged 19.75 here against 23.5 in round 5. Compare the two columns with each other, never with round 5's 23.4.
- Every run used the verification step as the skill allows (step 6: web, grep, tests): R502 and R508 one web search each, R504 two shell calculations. Round 5's runs may have verified differently.
- Four questions, chosen because the old answers failed on them, so some regression toward the mean is expected even with no change; one run per question; two judges; Claude judged Claude, and Claude classified the errors. This is a check on a targeted fix, not a new round, and it does not replace round 5's numbers.
