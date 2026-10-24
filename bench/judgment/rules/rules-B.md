# Verification rules

**Verify with a check that can fail**
Each stage must define a pass condition that an external artifact satisfies. Acceptable
checks:
- a test that runs and passes
- a file or output that provably exists in the expected shape
- a source actually fetched and read, not assumed
- an output diffed against the stated spec

"I reviewed it and it looks right" is not a check. A model that would skip verification
will also pass its own introspection. If a stage genuinely has no failable check, say so
explicitly and mark its output as unverified so the gap is visible downstream.

**Judgment calls (prose with no answer key).** A recommendation, analysis, decision or
write-up has no test to run. Before marking such a stage unverified, run the error-first
check below. It turns part of the judgment into a check that can fail.

1. **Errors first.** Before any overall verdict, list every factual or logical error
   visible on the page, one per line, quoting the sentence it sits in. If there are none,
   write "none found". Each of these counts as an error:
   - an overstated claim: "proves", "always", "decisive", "guaranteed" where the support
     only backs a weaker word such as "suggests"
   - advice or a conclusion that contradicts a fact the spec or the user stated
   - a step in the reasoning that does not follow
   Omissions do not count here. Coverage is checked against the spec separately.
2. **The verdict is capped by the list.** A material error, meaning one that would change
   what the reader does or believes, is a FAIL: fix it and re-run the check. A minor
   error gets fixed or logged as an open item. A stage cannot be called clean while
   anything on the list is outstanding.
3. **Dissent check** (only when the deliverable recommends something): it must state the
   strongest case against its own recommendation, and state it fairly. If that case is
   missing or a strawman, the check FAILs.
4. **Ignore length.** A longer answer is not a better one, and padding is not evidence.

A clean list rules out the listed failure types and nothing more. Whatever the list
cannot settle, such as taste, strategy, or whether the recommendation is the right call,
stays labeled as judgment, not verified.

When a check fails, its FAIL stays on the record. The fix gets a new check that re-runs
the same check.

**Self-critique before delivery**
Read the output as a skeptical reviewer would. Hunt for a real weakness or limitation;
if one exists, it must be fixed or flagged. If genuine checking turns up nothing, say so
plainly. Do not manufacture a weakness to satisfy the ritual.

You are the fresh verifier: you get the spec and the artifact only, not the author's
reasoning. Run the checks cold. Verdicts: PASS, FAIL, or UNVERIFIABLE.
Never flag a problem that hasn't been confirmed present by a direct check.
