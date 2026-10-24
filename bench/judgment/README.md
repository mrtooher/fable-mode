# Judgment-check bench (v6.1)

Tests whether v6.1's error-first judgment check helps a **checker** verify prose with no
answer key: decision memos, recommendations, write-ups.

The check is adapted from the error-first judge prompt in Ali Assem's
[wise-men-flash](https://github.com/Ali-expandings/wise-men-flash) (MIT). It lists errors
before any verdict, caps the verdict by that list, and runs a dissent check on any
recommendation.

## Method

- Two decision memos, each with planted errors and correct decoy figures.
  - `test1/`: Coravin purchase, 8 errors, mostly obvious.
  - `test2/`: house-wine supplier switch, 10 subtler errors buried mid-paragraph.
- Each answer key (`*/key.md`) was AES-encrypted before any checker launched and decrypted
  only after all returned. SHA-256 prefixes: test1 `3bff45b3ee1457e3`, test2
  `946c4c2e4520f1f6`.
- Six fresh checkers per memo, three per arm. Each got only the spec, the memo and its
  rules file, never the key.
  - Arm A (`rules/rules-A.md`): the v6 step 3/4 rules.
  - Arm B (`rules/rules-B.md`): the same rules plus the v6.1 judgment check.
- Test 1 ran Sonnet checkers. Test 2 ran Haiku checkers.

## Results

| | Arm A (v6) | Arm B (v6.1) |
|---|---|---|
| Test 1 (Sonnet): planted errors caught | 24/24 | 24/24 |
| Test 2 (Haiku): planted errors caught | 28/30 | 30/30 |
| Test 2: strawman "case against" flagged | 1 of 3 | 3 of 3 |
| Decoys wrongly flagged (both tests) | 0 | 0 |
| Strategy call labeled "judgment, not verified" | 0 of 6 | 6 of 6 |
| Avg tokens per checker, test 2 | ~90.4K | ~92.0K |

Per-checker rows and an error-by-checker matrix are in `results.xlsx`.

## Reading

- The gain comes from the **dissent check**. Haiku under v6 rules missed a strawman
  "strongest case against" section in two of three runs.
- The rest of the error-first list mostly duplicated v6's existing checks. With v6 rules,
  both models still caught the arithmetic errors, the contradictions with the spec, and
  "guaranteed" / "clearly" overclaims.
- On obvious errors, Sonnet hit the ceiling under both arms.

## Limits

- 12 runs over 2 memos, so this shows a direction, not proof.
- Every checker is a Claude model.
- The same author wrote the memos, the errors and the keys.
- Only the checker side is tested, not whether v6.1 makes the author write better memos.
