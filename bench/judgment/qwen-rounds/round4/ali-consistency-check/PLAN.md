# Consistency check for wise-men-flash 0.2.0 — plan, written before any run (2026-10-22)

**Why.** In round 5, flash's weakest axis was correctness (3.8/5 against the plain answer's 4.3). Reading the judges' error lists shows one recurring failure: on seven of the eight questions (R501–R504, R506–R508) at least one judge found a part of the flash memo contradicting another part or the question's premises — an absolute claim its own Risks undercut, a cost-of-being-wrong line calling the plan reversible after its Risks said it was not, or a number that disagreed with the memo's own arithmetic. The finding came from an outside code review (2026-10-21) and was checked against `head-to-head/judgments-v5/`.

**The change under test (0.1.2 → 0.2.0).** A "one memo, one story" synthesis rule; a cost-of-being-wrong line that must agree with Risks and the counter-position; a fifth checker test, CONSISTENCY; the checker now also gets the brief, in a prompt that wraps everything as data. Plus document fixes that do not change behaviour.

**What runs.** wise-men-flash at the working-tree SKILL.md (0.2.0), on R502, R504, R506 and R508 — the four questions whose flash memo the judges flagged for self-contradiction by all or most of the judges, three of them through the reversibility line. Each run uses round 5's exact flash arm prompt (`head-to-head/arm-prompts-r5.md`): a fresh general-purpose orchestrator on Sonnet, members as the skill specifies. One run per question; every run is kept.

**How it is judged.** For each question, a packet with two answers — round 5's flash answer (`head-to-head/raw/<Q>/wise-men-flash.md`) and the new one — in an order fixed by `random.Random(20261022)` before any run, under round 5's judge prompt (`head-to-head/judge-prompt-r5.txt`), adapted only in the number of responses. Two blind Opus judges per question, Read-only.

**What counts.**
- Primary: the number of internal contradictions the judges list in PASS 0 for each answer (a sentence that contradicts another part of the same memo or the question's premises). The change works if the new answers have fewer on at least three of the four questions, summed over both judges.
- Secondary: the correctness score, and the total /25.
- Honest limits: four questions, two judges, Claude judging Claude, one run each, and the questions were chosen because the old answers failed on them, so some regression toward the mean is expected even with no change. This is a check on a targeted fix, not a new round, and its result does not replace round 5's numbers.
