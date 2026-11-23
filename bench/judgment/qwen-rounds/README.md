# Qwen-graded judgment bench, rounds 1–6 (2026-11-22)

These rounds test fable-mode's checker rules on decision memos. A model other than Claude (Qwen) wrote most of the memos, held the answer keys and did the grading, which removes two weaknesses of the October bench: Claude wrote its own errors, and Claude graded Claude. Rounds 4–6 use Ali Assem's wise-men-flash consistency-check memos, whose answer key came from his own blind judges.

Each round used fresh checker agents in blind slots. Every checker got one memo, its SPEC and one rule file, but never the key, and the rule-set assignment stayed sealed until scoring was done. The assignments are in each round's `assignment.json`.

Rule files (`rules/`):
- `rules-B-v6.4.md`: v6.1–v6.4 error-first check (same text as `../rules/rules-B.md`).
- `rules-C-v6.5.md`: adds "a claim the spec does not cover is UNVERIFIABLE, not an error, unless it contradicts the spec or the artifact's own facts."
- `rules-D-v6.5-plus-self-contradiction.md`: C plus an explicit "contradicts another part of the same artifact" error type. Tested, but not adopted.

In the results, "old" means the v6 rules (`../rules/rules-A.md`) and "new" means v6.4 (`rules-B`).

## Results

| Round | Memos | Checkers | Question | Result |
|---|---|---|---|---|
| 1 | 2 Qwen memos, 10 blunt planted errors each | 12 Haiku, old vs new | Does v6.4 catch more planted errors? | Tie, 60/60 each. Ceiling effect. |
| 2 | 3 Qwen memos: 2 with 4 subtle errors, 1 "clean" control | 12 Haiku, old vs new | Same, plus the false-positive rate on a clean memo | Tie, 16/16 each. The control wasn't clean: checkers found 3 real flaws Qwen hadn't planted. 3 of 4 checkers counted not-in-SPEC claims as errors. |
| 3 | Round 2's control memo | 8 Haiku, v6.4 vs v6.5 | Does v6.5 stop counting not-in-SPEC claims as errors? | v6.5 kept them separate in 4 of 4 checkers, v6.4 in 1 of 4. Real flaws found: 9/12 (v6.5) vs 8/12 (v6.4). Adopted as v6.5. |
| 4 | Ali's 8 consistency-check memos (4 old, 4 new) | 16 Haiku, v6.4 vs v6.5 | Do our checkers catch his judges' contradictions? | 6/10 real key items for each arm (checked by hand against the reports; Qwen said 100%). Each arm found about 20 contradictions the key missed. Qwen ruled 4 of the key's 20 entries false. Fewer contradictions were found in the new memos than the old (17 vs 22). |
| 5 | The 4 memos with round-4 misses | 16 Haiku, C vs D | Does an explicit self-contradiction rule help? | D 3/10, C 0/10 on the targets. 2 of D's 3 catches were on a contested item. |
| 6 | Round 5's two memos with all-miss targets (memos 3 and 7) | 8 **Sonnet**, C vs D | Is it the model or the rule? | Sonnet caught 9/12 of the targets that Haiku missed 0/12, at C 5/6 and D 4/6. The rule doesn't help Sonnet, so D was not adopted. |

## Stray tool calls

Every round 5 and 6 brief said "Your only allowed tool is Read." Haiku checkers still made calls the brief forbade in about 6 of 32 runs across rounds 4–5: scheduling a message (one was created and later deleted), adding an Apple Note (denied), and device-info lookups. All 8 Sonnet checkers made exactly 2 reads. This led to v6.6, which never spawns Haiku as a worker, verifier or checker.

## Changes this bench drove

- **v6.5:** claims the spec does not cover are UNVERIFIABLE, not errors (round 3).
- **v6.6:** Sonnet is the floor for spawned agents, and Haiku is removed from worker, verifier and checker roles (rounds 5–6).
- **Not adopted:** the explicit self-contradiction rule (round 6).

v6.5 and v6.6 are saved in the author's own skills. The SKILL.md files in this repo have not been synced to them yet.

## Limits

- The samples are small: 4 checkers per arm in round 3, and 2 per arm per memo in rounds 4–6.
- Qwen's grading was inconsistent. It ruled not-in-SPEC flags FALSE in round 2 and REAL in round 3. In round 4 it credited catches that were not in the reports, and I corrected those by hand (a self-check).
- In round 4, Qwen saw the checker reports before it judged Ali's key, so its list of contradictions the key missed is not independent.
- All checkers were Claude models. Only the grading came from outside.
- Rounds 4–6 memo text and checker reports are not included, because the memos are Ali Assem's work (wise-men-flash, MIT) and permission to republish them is pending. The scores and assignments are included.
