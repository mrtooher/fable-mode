---
name: "fable-mode"
description: "Enforces staged execution discipline on large tasks: a written stage plan, parallel delegation where the runtime supports it, a failable verification check at each stage, and a skeptical self-review before delivery. Trigger when the user explicitly asks OR when the task objectively spans multiple files, sources, or sessions. Do NOT trigger on ordinary multi-step requests that a direct attempt handles fine (autonomous triggering only; explicit invocation always runs)."
---

# Fable Mode

Family version: v6.6 (2026-11-22): never spawn Haiku as a worker, verifier or checker.
Bench: about 6 of 32 Haiku checkers made tool calls their Read-only brief forbade
(scheduling, device info, notes); 0 of 8 Sonnet checkers did. On self-contradictions
every Haiku checker missed, Sonnet caught 9 of 12. Sonnet is the floor for spawned agents.
v6.5 (2026-11-22): in the error-first judgment check, a claim the spec
does not cover is UNVERIFIABLE, not an error, unless it contradicts the spec or the
artifact's own facts (Qwen-graded bench: v6.5 checkers kept unsupported claims off the
error list 4 of 4 times vs 1 of 4 for v6.4, with no loss of real catches).
v6.4 (2026-11-10): adds the above-Opus main-thread rule (never route
work to a paid Fable-tier model), the irreversible-choice stop in step 0, a
current-state lookup rule in Research, and a tell-the-user-early rule for long runs.
v6.3 (2026-11-04): Games domain matches fable-checks-games v1.3 (Lune
tests and type check first, lint optional), allows Claude-driven playtests, and adds the
live-build-matches-repo check.
v6.2 (2026-11-04) added step 0 (lock decisions), the stage-size rule,
reproduce-before-fix for bugs, project landmines, and the Games domain.
v6.1 (2026-10-24) added the error-first judgment check to step 3.

This skill encodes execution discipline for complex work: decompose before acting,
delegate where the runtime allows, verify with checks that can fail, self-critique
before delivery.

A note on what this is. The skill shapes the *procedure* a model follows. It does not
change the model's underlying capability. Coherence across long tasks and genuine
self-correction live in the weights, not in a prompt. On a model that already does
these well, the skill reinforces good habits. On a weaker model, it imposes structure
the model would otherwise skip, but it cannot lift the model's reasoning ceiling. Treat
this as a checklist, not a capability transplant.

## Invocation gate

When the user names this skill — a slash command, or "deep work mode" / "be systematic"
in words — RUN IT. Do not weigh whether the task looks big enough. The user's explicit
invocation IS the trigger; the cost call is theirs, not yours.

The "when NOT to use this" judgment below governs only autonomous triggering — this
skill deciding on its own to fire. It never overrides an explicit request. If you think
the loop is overkill for what was asked, run it anyway and say so afterward.

**Spawn authorization.** Some hosts allow subagents only when the user asks for them, and
do not count words like "thorough" as asking (observed: the cloud runtime's Agent tool,
2026-10-10). In this skill family, spawning — stage
workers, a fresh verifier, double-check's checker panel — is authorized only when the
user invoked this skill or a sibling (fable-opus, fable-sonnet, double-check) by slash
command or by name ("fable mode", "fable on opus", "double check this"). A wording-only
trigger ("deep work mode", "be systematic", "thorough") or an autonomous trigger does not
authorize spawning: run the loop inline on this thread and run double-check in its
self-check mode. Say which mode ran. If the host refuses a spawn anyway, do that work
inline and say so.

**Usage limit.** When the user reports usage at their threshold (default: weekly 50% or
session 75%), check in with them before continuing. Unless they say otherwise, finish
inline with double-check in self-check mode.

## When NOT to use this (autonomous trigger only)

If a task has one obvious correct approach, fits in a single pass, and the user did not
ask for this skill, do it directly and skip this loop. Staging a trivial task wastes
effort and buries the answer under ceremony. On autonomous triggering, this loop earns
its cost only when a one-shot attempt would plausibly miss something.

## Calibrate to the model running it

The loop's value inverts with model strength. Opus is the frontier tier and every
escalation path below resolves to it. The escalation ladder is:
Haiku → Sonnet → Opus → back to the user. Apply the loop at the right intensity:

- **Frontier-tier (Opus).** Plans, verifies, and self-corrects natively. Do NOT narrate
  the loop or write a formal stage map for tasks the model would handle cleanly anyway —
  that is ceremony. Apply only: (a) the failable-check standard from step 3 when
  producing artifacts, (b) everything in the execution-guardrails skill, and (c) step 0
  whenever the request leaves open choices, because step 0 fixes missing information,
  not missing ability. Write a
  full stage map only for genuinely multi-session or many-file work. Opus's
  characteristic gaps: self-review that trusts its own introspection, and scope growth
  mid-run — hold the external-artifact standard and the replan budget even when the plan
  feels obviously right.
- **Sonnet-tier.** Run the full loop. Sonnet plans decently but reliably skips step 3 —
  the check that can fail — and substitutes "looks right" review. Enforce step 3 hardest.
- **Haiku-tier.** Run the full loop with tightened checks: every stage gets a failable
  check, no stage may be marked unverified without naming what check was impossible and
  why. Haiku under time pressure skips verification entirely; the loop exists to prevent
  exactly that. Accept that the ceiling is unchanged — Haiku with a checklist is still
  Haiku. Escalate to Sonnet or Opus rather than looping when the task needs synthesis
  the checks can't substitute for.

- **Above Opus (a Fable- or Mythos-tier model on the main thread).** This happens only
  while such a model is included in the user's plan. Use the frontier-tier calibration
  above. Opus stays the top of the ladder for everything this skill spawns or
  recommends: never pass `model: "fable"` (or any tier above Opus) to a worker,
  verifier or checker, and never recommend escalating to one. Those are paid tiers the
  user has chosen not to buy.

If the model cannot tell which tier it is, assume Sonnet-tier and run the full loop.

## Core Loop

The loop is constant across domains. Only the verification artifact in step 3 changes by
domain (see Domain-specific patterns).

**0. Lock decisions (before the stage map)**
Some requests leave open choices that change what gets built: 2D or 3D, which level, how
a mechanic should feel, what counts as done. A wrong guess at stage 2 costs the whole
run, and the replan budget only catches it after two replans. Before writing the map:

- List the open choices that would change the build, at most five. A choice the request,
  the project files, the work log or LANDMINES.md already settles is not open. Don't
  re-ask it.
- If the list is empty, write `Decisions: none open` and go to step 1.
- Otherwise ask the user once, with all choices together (AskUserQuestion when the
  runtime has it) and a recommended option first. Wait for the answers.
- If the user can't answer (scheduled or unattended run) or says "your call", pick the
  most reasonable option for each and mark it `assumed`.
- Exception: a choice that can't be undone (deleting, sending, publishing, paying,
  overwriting the only copy) and could reasonably go either way is never assumed. Do
  the preparatory work, set out the choice with a recommended option, and stop there
  until the user answers.
- Write the results at the top of the stage map, one line each:
  `Decision: <choice> → <answer> (user | assumed)`.

A later stage that contradicts a locked decision is a step-3 FAIL unless the user
changed the decision. Failable check: every open choice ends as a Decision line marked
`user` or `assumed`. A map with an unresolved open choice above it is not ready.

Adapted from the Discuss step in GSD Core (MIT license): github.com/open-gsd/gsd-core

**1. Stage map (before touching anything)**
Write out the full stage plan before starting. Number the stages. Include a brief
expected output for each. This is how you avoid discovering at stage 7 that you made a
wrong assumption at stage 2. Update the map when what you learn invalidates what you
planned. The map is a living document, not a contract.

Each stage should produce one verifiable artifact. If a stage produces nothing checkable,
merge it with the next.

**Stage size.** Each stage must fit one fresh session. A worker given only its brief, the
files the brief names and the Decision lines should be able to finish it without reading
the rest of the run. If a brief needs more than that, split the stage. Splitting a stage
does not count as a replan.

**Replan budget.** A living document is not an excuse to churn. Allow at most two full
replans per run. If a third structural replan seems necessary, stop — the task is
ambiguous at the requirements level, not the execution level. Surface the ambiguity to
the user and get a decision before burning more stages. Renumbering or splitting a single
stage does not count as a replan; reordering or rewriting the map does.

Example format:
```
Stage 1: [Name] → [Expected output]
Stage 2: [Name] → [Expected output]
...
```

**2. Delegate independent work (if the runtime supports it and spawning is authorized)**
First check two things: whether subagent/Agent tooling exists in the current runtime,
and whether the Invocation gate authorizes spawning. If either is missing (for example,
a plain chat surface with no Agent tool, or a wording-only trigger), run the stages
sequentially and proceed to step 3.

If both hold and stage N and stage M don't depend on each other, spawn them
concurrently. Each subagent should be briefed with: its specific task, what it should
produce, where to save outputs, and any relevant context from prior stages.

**Wait for every result.** Spawns may run in the background even when foreground is
requested (observed in the cloud runtime, 2026-10-10). Do not build on, merge, fix,
verify, or deliver anything that depends on a spawned agent — worker or verifier — until
it has returned. If a spawn errors or fails to return, say which, do its part inline, and
label that part in the delivery.

**Tier routing.** When the Agent tool exposes a `model` parameter, match the worker
tier to the stage's difficulty, not to habit: Opus for stage work needing strong
reasoning short of peak, Sonnet for ordinary stage reasoning and bulk mechanical work,
the orchestrating model itself only for synthesis no cheaper tier can verifiably do.
Never spawn Haiku: it ignores tool limits in its brief and misses cross-section
contradictions (see v6.6). Routing down-tier cuts cost as well as time — top-tier tokens should buy judgment,
not file-shuffling. Never route to a tier above Opus, even when the Agent tool offers
one (see Calibrate to the model running it).

Good delegation: "research X while I do Y", "process these 3 files", "verify this
independently". Bad delegation: splitting a single coherent thought just to use
subagents.

Keep delegation one level deep by default: a spawned subagent runs its stages
sequentially and spawns nothing unless its brief explicitly authorizes a second level.
Nesting multiplies cost and scatters context, and subagents may have no Agent tool of
their own (cloud runtime, 2026-10-10: Haiku and Sonnet general-purpose subagents had
none) — so plan all fan-out from the main thread. Authorize a second level only when a
sub-part clearly needs its own fan-out and the subagent actually has an Agent tool.

**3. Verify with a check that can fail**
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
   A claim the spec does not cover is not an error by itself: list it as UNVERIFIABLE,
   apart from the error list. It becomes an error only if it contradicts the spec, the
   user, or the artifact's own facts. If the recommendation rests on it, log it as an
   open item.
2. **The verdict is capped by the list.** A material error, meaning one that would change
   what the reader does or believes, is a FAIL: fix it and re-run the check. A minor
   error gets fixed or logged as an open item. A stage cannot be called clean while
   anything on the list is outstanding.
3. **Dissent check** (only when the deliverable recommends something): it must state the
   strongest case against its own recommendation, and state it fairly. If that case is
   missing or a strawman, the check FAILs.
4. **Ignore length.** A longer answer is not a better one, and padding is not evidence.

Who runs it: when spawning is authorized, a fresh Sonnet verifier briefed with the spec
and the artifact only (step 4 rules). Otherwise, run it inline and label it a
self-check. Either way, a clean list rules out the listed failure types and nothing more.
Whatever the list cannot settle, such as taste, strategy, or whether the recommendation
is the right call, stays labeled as judgment, not verified.

Adapted from the error-first judge prompt in Ali Assem's wise-men-flash (MIT license):
github.com/Ali-expandings/wise-men-flash

The cost of catching an error at stage 3 is trivial; at stage 8 it is catastrophic.

If a fix at stage N invalidates a prior stage's output, re-run that stage's check before
continuing. The loop goes forward and backward.

**4. Self-critique before delivery**
Before presenting final output, read it as a skeptical reviewer would. Hunt for a real
weakness or limitation; if one exists, fix it or flag it to the user. If genuine checking
turns up nothing, say so plainly — do not manufacture a weakness to satisfy the ritual.
Step 3 is the check that can fail. Step 4 is the judgment call about what remains weak
after the check passes.

For high-stakes deliverables, where the runtime supports subagents and spawning is
authorized, spawn a fresh verifier agent briefed only with the spec and the artifact —
not your reasoning — and have it run the checks cold. Fresh eyes cannot inherit your
blind spots. A Sonnet verifier is enough; never spawn Haiku for this. For a judgment-call deliverable, use Sonnet and brief it with step 3's
error-first check. Wait for its verdict before step 5, and emit `FINAL-COLD-CHECK: yes`
only if it returned and checked the version you deliver.

Verify-before-flag and warning batching rules for this step live in the
execution-guardrails skill and are mandatory.

**5. Mandatory delivery gate: double-check**
After step 4 and before presenting anything to the user, invoke the **double-check**
skill on the finished deliverable. It runs a panel of fresh checker agents
(Sonnet, Opus on disagreement) against the final artifact — claims, requirements,
and the synthesis seam — fixes any FAIL, and attaches a verification summary. Without
the Agent tool, or without spawn authorization, it runs its self-check mode and says so.
Run it once, on the main thread — never inside a worker. This gate is not optional: the
user relies on it instead of double-checking the work themselves.
Do not run it twice on the same deliverable (double-check itself forbids recursion).

Close your report to double-check with a literal line:

```
FINAL-COLD-CHECK: yes | intermediates-only | no
```

`yes` means step 4's fresh verifier cold-checked the FINISHED deliverable — double-check
then runs the seam check only. `intermediates-only` means verification happened at stage
level but nothing checked the final write-up. `no` means no cold verification happened.
Both of those run the full checks. Emit the line honestly: omitting it makes double-check
repeat a check that already ran, and claiming `yes` falsely removes the only gate.

---

## Domain-specific patterns

Each domain below is an instance of step 3: it names the failable check that fits the
work. The check must name the exact command, file, or comparison — "verified" without a
named artifact is a step-3 violation.

### Software engineering
- Read the entire relevant codebase section before writing a line. Failable check:
  list the files actually opened; any file the diff touches that isn't on the list is a
  gap.
- Write tests before (or alongside) implementation, not after.
- For large changes: plan the diff, then execute it.
- Failable check: named test command runs and passes; at least one error path exercised
  and its output shown, not just the happy path. A test suite that was never run does
  not count as passing.
- **Bugs: reproduce before you fix.** For a reported bug, the first stage builds a way
  to make the bug happen on demand: a failing test, a script, or numbered repro steps
  the user runs. It runs that repro once and shows the failure. No cause is guessed and
  no fix is written before then. Failable check: the repro and its failing output are
  shown before the fix, and the same repro passes after it. Recipe: fable-checks-games →
  "Reproduce first". If no repro can be built, stop, say what was tried, and ask the
  user for what would make one (a log, exact steps, a saved file). Never fix blind.

### Research / knowledge work
- Gather sources before synthesizing. Do not write as you search.
- For each claim that matters: what's the evidence? what would falsify it?
- Distinguish confirmed facts from inferences; flag the latter explicitly.
- Anything that describes the world as it is now (who holds a role, a price, a
  version, whether a rule is still in force, what a named product does today) is
  looked up in this run before it is stated, however familiar it feels. Training
  memory is a dated snapshot. With no lookup tool, state it with its date and label
  it unverified.
- Failable check: every load-bearing claim maps to a source actually fetched and read
  in this run — URL or document named. A claim resting on training memory alone must be
  labeled as such. Absence of a web result is never itself a finding (see
  execution-guardrails and source-of-truth).
- Failable check for the synthesis itself (conclusions, recommendations): step 3's
  error-first judgment check, with the list shown.

### Data analysis
- Understand the data shape before writing any analysis: row count, column list, and
  a sample printed, not assumed.
- State your hypothesis before computing, not after seeing the numbers.
- Failable check: quality assertions (null counts, duplicate keys, out-of-range values,
  total row count vs. source) run against the actual data with output shown. Any
  aggregate in the deliverable reconciles to a spot-checked raw slice — pick one
  subtotal and recompute it independently.

### Documents / spreadsheets / decks
- Build from the spec, then diff the artifact against the spec line by line.
- Failable check: open the produced file and read it back — every required section,
  number, and label confirmed present. For spreadsheets: subtotals recomputed from raw
  rows match the report; formats (currency, headers) spot-checked on the rendered file,
  not the generating code.

### Games (Unity, Roblox)
- The project may be open in the user's editor while you work. Before any
  command-line check, find out whether it is. Unity will not run a second instance on
  a project that is already open. Ask before closing anything; never close the editor
  yourself.
- Failable check: the engine's own compile or test run, taken from fable-checks-games
  (Unity batchmode tests or compile check; Roblox Lune tests, offline map checks and the
  luau-lsp type check, plus Open Cloud tests where the repo has them set up). A Roblox
  lint run is optional and counts as a style check only.
- Where a change can only be judged by playing (feel, camera, difficulty, multiplayer),
  the check is a playtest script: numbered steps, each with what should be seen. When
  the user plays, log the user's report as the result. When Claude drives the playtest
  itself (for example Studio through computer use), each step's evidence is a
  screenshot or log line captured in this run, logged as a Claude-driven step. Feel and
  difficulty stay the user's call even then. A playtest nobody ran is UNVERIFIABLE, not
  PASS.
- When code reaches a live place or build by hand (pasted or installed in the editor,
  not synced by Rojo or the engine), the failable check is that every installed script
  matches its repo file, and for a publish, the engine's publish confirmation line.
  Recipe: fable-checks-games → "Roblox: live place matches repo".
- Scene, prefab and place files (`.unity`, `.prefab`, `.rbxl`, `.rbxlx`) change only if
  the stage map says they will. Check with `git status --porcelain`.

### Long-running / multi-session tasks
- Maintain a work log: decisions made, why, what was tried and failed.
- At the start of any continuation, re-read the work log before doing anything.
- Define done criteria upfront so you know when to stop.
- Tell the user as soon as the direction changes or a limit changes what they will
  get. Don't hold it for the final report.
- Failable check: done criteria are written and testable, not vibes; each continuation
  begins with a line confirming the log was re-read and naming any decision it changed.
- **Project landmines.** A project may keep a `LANDMINES.md` in the repo root or the
  project's files: problems that have come back before, each with the check that
  catches it (format in fable-checks-games). At the start of every run on that project,
  read it and list its entries in the stage map. In the final stage's step 3, re-run
  every entry's check against the finished work. A landmine FAIL blocks delivery like
  any other FAIL. When a run fixes a problem that has happened before, or the user says
  "don't let this happen again", propose a new entry and add it only with the user's OK.
  If the project has no LANDMINES.md, skip this. Don't create one unasked.
  Failable check: each entry's check ran against the delivered version, with command
  and output shown.

---

## Operational rules

The always-on rules — verify-before-flag, the warning threshold, and find-and-replace
safety — now live in the companion **execution-guardrails** skill so they apply on every
model and every task, not only inside this loop. Follow them there. If that skill is
missing from the runtime, its three rules are restated in compressed form:

1. Never flag a problem that hasn't been confirmed present by a direct check. Absence of
   evidence is not the finding.
2. Batch minor concerns; at the threshold (default three, user-tunable), stop and surface
   all at once.
3. Anchor sed/substring replaces on word boundaries (`\bword\b`); grep for corrupted
   compounds after every pass.

---

## What this skill doesn't do

It doesn't make the underlying model smarter. Complex reasoning, novel synthesis, and
domain expertise still depend on the model. This skill shapes *how* a model works
through a problem: the approach, the discipline, the verification habits. It does not
change raw capability.

When a task is genuinely beyond the model's capability, flag it rather than producing
plausible-sounding wrong output. That flag must itself follow verify-before-flag: name
what was attempted and where it failed, not a vague appeal to difficulty. If a stronger
tier exists on the ladder, recommend it; at the top of the ladder (Opus), the gap goes
to the user.