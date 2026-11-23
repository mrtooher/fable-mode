---
name: "double-check"
description: "Automatic final verification pass on completed deliverables. Runs at the end of every fable-mode run — those skills invoke it before delivery. Also triggers when the user says \"double check this\". Uses a panel of fresh checker agents when spawning is authorized (otherwise a cold self-check) to verify the finished output — not to redo the task. Any FAIL gets fixed and re-checked before delivery."
---

# Double Check

Family version: v6.6 (2026-11-22): no Haiku checkers. The mechanical checker is now
Sonnet too (bench: about 6 of 32 Haiku checkers made tool calls their Read-only brief
forbade; 0 of 8 Sonnet did).
v6.5 (2026-11-22): the Sonnet checker lists claims the spec does not
cover as UNVERIFIABLE, not as errors, unless they contradict the spec or the
deliverable's own facts.
v6.4 (2026-11-10): Decision lines count as requirements, the Sonnet
checker runs errors-first on judgment deliverables, the seam check hunts stale
current-state claims, and Opus is the checker ceiling. v6 (2026-10-10) was the
previous version.

Automatic verification pass on a *finished* deliverable. The user should never have to
re-check work themselves — this skill is that re-check.

This skill is both the **gate** (when verification runs, on what, and what happens to a
FAIL) and the **mechanism** (how to brief a cold verifier so it checks the world instead
of your argument). Both live here — there is no companion skill to load.

## What it is and is not

- It verifies **outputs**, it does not re-run the task. A full second run produces a
  second divergent version and a comparison problem; attacking the finished artifact
  catches the same errors at a fraction of the cost.
- It runs **after** the work is complete and **before** it is delivered.
- It never runs on its own output. One double-check per deliverable. Fixes triggered by
  a FAIL get their specific failed check re-run — not a whole new panel. No recursion.

## When it runs

1. **Automatically** at the end of any fable-mode run (fable-mode, fable-opus,
   fable-sonnet). Those skills call this one as their final delivery gate. Exception: if
   a fable run already executed a cold verification of the final deliverable, do not
   duplicate it — run only the seam check (section "Check the synthesis seam") and skip
   the rest. Do not infer this from the narrative: the run closes its report with a
   `FINAL-COLD-CHECK:` line. `yes` → seam check only. `intermediates-only`, `no`, or no
   line at all → run the full checks (panel or self-check mode, per below). Absence of
   the line is never evidence that the check happened.
2. **On request**: "double check this", "verify this", "make sure this is right".

**Panel or self-check.** Some hosts allow subagents only when the user asks for them
(observed: the cloud runtime's Agent tool, 2026-10-10). Run the checker panel only when
this skill was invoked by slash command or by name ("double check this"), or when the
fable run that called it was spawn-authorized (see fable-mode's Invocation gate).
Otherwise — "verify this", "make sure this is right", or a fable run without spawn
authorization — use self-check mode (step 2) and say so. The usage limit overrides both:
when the user reports usage at their threshold, check in first; unless they say
otherwise, use self-check mode.

## Skip conditions

Trivial, reversible, low-stakes output where being wrong costs nothing and is
immediately visible. Say in one line that double-check was skipped and why.
Never skip when the deliverable tells the user to delete data, change a system or
security setting, spend money, or act on a warning.

## The core rule: pass the claims, never the reasoning

An agent reviewing its own work almost always agrees with itself. It re-reads its
reasoning, finds it reasonable, and signs off — the same blind spot that produced the
error also produces the approval. A cold agent has no stake in the conclusion and no
memory of why it seemed right. It has to go get the evidence again. That is the entire
mechanism; everything below protects it.

The moment a verifier reads *why* you concluded something, it starts evaluating your
argument instead of the world. It inherits your framing and your blind spot. You get
agreement, not verification.

Give the verifier: the claim, the spec or original requirements, and where to look.
Withhold: your reasoning, your confidence, your narrative, and which claims you think
are shaky. Do not hint at what you expect it to find — "I think claim 4 might be weak"
tells it where to spend effort and implies the others are fine.

## Procedure

### 1. Extract claims and requirements

From the finished deliverable, build two numbered lists:

- **Claims** (C1, C2, ...): every falsifiable assertion in the deliverable. Facts,
  numbers, file paths, computations, statements that something works. Each must be
  stated so a specific observation could refute it.
  Good: `C3: /Applications is 63 GB.`
  Bad: `C3: Storage looks basically fine, mostly apps.`
  If a claim can't be stated so an observation would refute it, it isn't a claim — it is
  a summary. Either sharpen it or drop it from "established" status in the deliverable.
- **Requirements** (R1, R2, ...): everything the user's original request demanded.
  Each phrased as a yes/no: "deliverable contains X", "file Y exists and opens",
  "all rows from source present".
  When the run locked decisions (fable-mode step 0), each `Decision:` line is a
  requirement too: the deliverable must not contradict it. Name every `assumed`
  decision in the summary so the user can confirm it.

For each item, name the exact check: the command, file, source, or comparison that
settles it. An item with no nameable check is marked UNVERIFIABLE by you, up front,
and labeled as such in the deliverable.

### 2. Detect the runtime, pick the mode

**Panel mode (Agent tool available AND spawning authorized): run the checker panel.**

Spawn fresh checker agents using the brief template below. They receive claims,
requirements, checks, constraints (READ-ONLY — checkers never modify anything), and the
output format. They never receive your reasoning, your confidence, or hints about which
items you suspect.

Tier routing — match the tier to the check, not to the importance of the deliverable:
- **One Sonnet mechanical checker (all mechanical checks in one bundle):** numbers
  re-added, files opened and read back, links/paths exist, commands re-run, counts
  reconciled. Add a second only when the mechanical checks will not fit one brief, and
  say why. Never spawn Haiku as a checker.
- **One Sonnet checker:** requirements coverage (every R satisfied by the artifact
  itself, not by the work log), internal consistency, logic of any argument the
  deliverable makes. When the deliverable is a recommendation, analysis or other prose
  with no answer key, this checker works errors-first: before any verdict it lists
  every overstated claim ("proves", "always", "guaranteed" where the support only backs
  "suggests"), every conclusion that contradicts a fact in the spec, and every step
  that does not follow, each with the sentence quoted, or writes "none found". A claim the
  spec does not cover is not on that list: it is UNVERIFIABLE unless it contradicts the
  spec or the deliverable's own facts, and an open item if the recommendation rests on
  it. A
  recommendation with no fair statement of the strongest case against it is a FAIL.
  Length is not evidence. Taste and strategy stay labeled judgment, not verified.
- **Opus (only if needed):** when two checkers disagree on the same item, or a
  REFUTED verdict is itself disputed after the fix. Opus is the ceiling: never spawn a checker or adjudicator above it, even when
  the Agent tool offers a Fable-tier model; an item Opus cannot settle goes to the user
  as UNVERIFIABLE. Adjudicates; does not re-check
  everything.

**Collect every verdict.** Spawns may run in the background even when foreground is
requested (observed in the cloud runtime, 2026-10-10). Do not fix, synthesize, or
deliver until every checker has returned; never act on a partial panel. If a checker
errors or fails to return, run its checks in self-check mode and label them so.

**Self-check mode (no Agent tool, or spawning not authorized): degraded single-pass mode.**

Say plainly that the checker panel did not run and why (no Agent tool on this surface,
or spawning not authorized). Then run the
checks yourself, cold: work only from the claims/requirements lists and the artifact —
deliberately not from memory of how you produced it. Re-derive each number, re-read
each file or source, re-test each requirement against the artifact. Same ternary
verdicts, same output format. Weaker than fresh agents — label it as a self-check in
the summary.

### Checker brief template

```
You are a COLD VERIFIER. Claims below were produced by other agents.
You did not see their reasoning. Assume each claim may be wrong.

[hard constraints — e.g. READ-ONLY, no sudo, no modifications]

## CLAIMS
C1: <falsifiable assertion> → check via: <command / source>
C2: ...

## OUTPUT
C1: CONFIRMED|REFUTED|UNVERIFIABLE — <exact command> → <exact output line>
C2: ...

## CORRECTIONS
<every claim that was wrong, and what is actually true>

Refute freely. Finding a wrong claim is a success, not a failure.
Do not report a claim as confirmed unless you personally observed
the output that proves it. If you could not check something, say
UNVERIFIABLE — do not guess and do not pad.
```

The "refute freely" line is not optional. Without it, agents optimize for agreement:
they read a claim, find it plausible, and confirm.

### 3. Verdicts — ternary, forced

Every claim and requirement returns exactly one of:

- **PASS / CONFIRMED** — with the exact command or observation and the exact output
  line proving it. "Looks good" is banned; it is not a verdict.
- **FAIL / REFUTED** — with what is actually true instead.
- **UNVERIFIABLE** — with why the check could not run. First-class outcome, not a
  failure. It is how blind spots stay visible instead of quietly becoming assumed-true.
  A panel that never returns UNVERIFIABLE is guessing to look thorough.

### 4. Check the synthesis seam

The error that survives everything above: work checked at intermediate stages, then
the final write-up introduces new claims nobody checked. Multi-agent work has a seam —
the workers produce findings, a verifier checks those findings, and then the synthesizer
writes the deliverable, and the synthesizer's own additions and escalations were never
checked by anyone.

Always extract claims from the **document about to be handed over**, not from
intermediate outputs. Two seam-specific hunts:

- **Escalated hedges:** anywhere a caveat in the underlying work became a firm
  conclusion in the deliverable. If the work said "signal" and the deliverable says
  "exposure", check it. Real example: a worker correctly reported an app bundle's mtime
  as an "un-updated signal, not a true unused signal"; the synthesizer turned that into
  "18 months stale, security exposure, update immediately." The app was four weeks
  behind. Nothing had checked the final report.
- **Proxy metrics read as the real thing:** a timestamp is not a version; a file size
  is not disk usage; a process existing is not a process running; a search returning
  nothing is not evidence of absence. Verify the actual quantity.
- **Stale current-state claims:** anything the deliverable states about the world as it
  is now (a price, a version, who holds a role, whether a rule is in force, what a named
  product does today). The check is whether it was fetched in this run. If it rests on
  training memory or an earlier session, look it up now or mark it UNVERIFIABLE with
  its date.

### 5. Fix, then re-check

Any FAIL: fix the deliverable, then re-run **that specific check**. If the fix
invalidates upstream content, fix and re-check that too.

**One re-check round.** In panel mode, batch every fixed item into ONE fresh re-checker
brief (Sonnet). If anything fails that round,
fix it and verify it by cold self-check — re-derive from the artifact, no new spawn —
and mark those items "self-checked" in the summary. No further spawn rounds. An Opus
adjudicator for a disputed verdict (step 2) sits outside this cap — at most one per
disputed item. In self-check mode, every re-check is a cold re-derivation.

Deliver only when every item is PASS or explicitly UNVERIFIABLE. Never deliver with an
unresolved FAIL footnoted.

### 6. Report

Deliver with a short verification summary:

```
Double-check: N claims + M requirements.
PASS: n. FIXED after FAIL: n (list what was wrong, one line each). UNVERIFIABLE: n (named).
Checkers: [e.g. 2× Sonnet, 1 re-check round | self-check — no Agent tool / spawning not authorized]
```

Name what got refuted and fixed — that is the evidence the check was real. A summary
that confirms everything is either a clean run or a rubber stamp, and the user can't
tell which unless specifics are named. If everything passed cleanly, say that plainly;
do not manufacture a finding. When the mistake was yours rather than a worker's, say so
plainly too — own the specific error and move on, no extended apology.

## Operational rules

- Verify-before-flag applies: a checker's FAIL must cite the observed evidence, not
  the absence of confirmation. Absence of evidence is not a finding.
- Checkers are READ-ONLY. Only the main session fixes things.
- Budget: default panel is 2 Sonnet (one mechanical, one logic), plus at most one
  re-check round. Escalate to Opus only on disagreement. Haiku was dropped on
  2026-11-22 for ignoring Read-only briefs; keep mechanical briefs short instead.