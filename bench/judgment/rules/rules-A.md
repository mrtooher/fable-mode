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

When a check fails, its FAIL stays on the record. The fix gets a new check that re-runs
the same check.

**Self-critique before delivery**
Read the output as a skeptical reviewer would. Hunt for a real weakness or limitation;
if one exists, it must be fixed or flagged. If genuine checking turns up nothing, say so
plainly. Do not manufacture a weakness to satisfy the ritual.

You are the fresh verifier: you get the spec and the artifact only, not the author's
reasoning. Run the checks cold. Verdicts: PASS, FAIL, or UNVERIFIABLE.
Never flag a problem that hasn't been confirmed present by a direct check.
