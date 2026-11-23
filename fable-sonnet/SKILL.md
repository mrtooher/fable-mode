---
name: "fable-sonnet"
description: "Run fable-mode execution discipline on Claude Sonnet. When invoked by slash command or by name, spawns a Sonnet subagent that follows the staged loop — stage plan, parallel delegation, a failable verification check at each stage, and a skeptical self-review before delivery; a wording-only request runs the loop inline on the current model. Trigger when the user explicitly asks for thorough/systematic/\"deep work\" handling on Sonnet."
---

# Fable Mode — Sonnet

Family version: v6.6 (2026-11-22): verifiers are Sonnet, never Haiku (Haiku checkers
ignored Read-only briefs in about 6 of 32 bench runs; Sonnet in 0 of 8).
v6.5 (2026-11-22): in the error-first check, a claim the spec does not
cover is UNVERIFIABLE, not an error, unless it contradicts the spec or the deliverable.
v6.4 (2026-11-10): the worker loop gains the error-first judgment
check and the current-state lookup rule, and the parent never assumes an irreversible
choice. v6.3 (2026-11-04): the worker loop now carries fable-mode v6.2+'s
Decision lines, stage-size rule, reproduce-before-fix, Games domain and project
landmines. v6 (2026-10-10) was the previous version.

Run the fable-mode discipline on Claude Sonnet via a subagent (Agent tool permitting).
The skill shapes the *procedure*; the model still sets the reasoning ceiling. Sonnet
sits between Haiku and Opus — strong general reasoning at lower cost. Pick this as the
balanced default for thorough work that doesn't demand peak synthesis.

Sonnet's characteristic gap: it plans decently but reliably skips step 3 — the check
that can fail — and substitutes "looks right" review. The briefing below enforces step 3
hardest for that reason.

## Invocation gate

When the user names this skill — a slash command, or "fable on sonnet" in words —
RUN IT. Do not weigh whether the task looks big enough. The user's explicit invocation
IS the trigger; the cost call is theirs, not yours.

The "skip for single-pass tasks" judgment below governs only autonomous triggering —
this skill deciding on its own to fire. It never overrides an explicit request. If you
think the loop is overkill for what was asked, run it anyway and say so afterward.

**Autonomous trigger only:** if a task has one obvious correct approach, fits in a
single pass, and the user did not ask for this skill, do it directly.

**Spawn authorization** (same rule as fable-mode): a slash command or the skill named
("fable-sonnet", "fable on sonnet") authorizes spawning. A wording-only or autonomous
trigger does not: run the loop inline on the current model, run double-check in its
self-check mode, and say so. If this thread is not on Sonnet, also say the Sonnet pin
was skipped and that a slash command requests the pinned run. Usage limit: same as
fable-mode — when the user reports usage at their threshold, check in first.

## How to run it

1. Confirm the runtime exposes the Agent tool and spawning is authorized (Invocation
   gate). If either fails, you cannot pin a model — say so and run the loop inline on
   the current model instead.
2. First run fable-mode step 0 (lock decisions) on this thread: ask the user about open
   choices that would change the build, or mark them `assumed` when nobody can answer.
   Exception: a choice that can't be undone (deleting, sending, publishing, paying,
   overwriting the only copy) and could reasonably go either way is never assumed. Do
   the preparatory work, set out the choice with a recommended option, and stop until
   the user answers.
   If the project has a `LANDMINES.md`, read it. Then spawn an Agent with
   `model: "sonnet"` and `subagent_type: "general-purpose"`.
3. Brief the agent with: the user's task, the `Decision:` lines, the LANDMINES.md
   entries (or "none"), where to save outputs, relevant context from this session, and
   everything from **Core Loop** onward as its operating instructions.
   Inline the operational rules below in full — pass them verbatim, do not summarize
   them into a reference. Cloud subagents could load skills (2026-10-10); other
   surfaces are unchecked. The inline copy is shorter than a skill load and works
   either way.
4. Wait until every spawned agent — worker or verifier — has returned before you merge,
   fix, or relay; spawns may run in the background even when foreground is requested.
   If a spawn errors or fails to return, say which and do its part inline. Then relay
   the result and surface any stage it marked unverified.
5. For high-stakes deliverables, if spawning is authorized, spawn a fresh verifier agent
   briefed only with the spec and the artifact — not the worker's reasoning — and have it
   re-run the named checks cold. Use a Sonnet verifier; never spawn Haiku for this. Wait for its verdict before step 6; the FINAL-COLD-CHECK line
   may say `yes` only if it checked the version you deliver.
6. **Mandatory delivery gate — once, on this thread, never inside the worker:** before
   presenting the result to the user, invoke the **double-check** skill on the finished
   deliverable. It runs the checker panel (claims, requirements, synthesis seam) — or its
   self-check mode without the Agent tool or spawn authorization — fixes any FAIL, and
   attaches a verification summary.

   Close your own report to double-check with a literal line:

   ```
   FINAL-COLD-CHECK: yes | intermediates-only | no
   ```

   `yes` means step 5's verifier cold-checked the *final* document, and double-check
   runs only the seam check. `intermediates-only`, `no`, or a missing line means the
   full checks run. Emit it honestly. Do not skip the gate; the user relies on it
   instead of re-checking the work themselves.

For independent sub-parts, spawn multiple Sonnet agents concurrently and merge outputs
only after every one has returned.
Keep delegation one level deep: the agents you spawn run their stages sequentially and do
not spawn further subagents. Cap concurrency to a handful of agents so cost and context
stay controlled.

## Core Loop (pass this to the subagent)

**0. Decisions are locked**
The parent locked the open choices before briefing you. Copy its `Decision:` lines to
the top of your stage map. A stage that contradicts a Decision line is a step-3 FAIL.
If you hit a new open choice that would change the build, stop and return it to the
parent for a user decision; do not guess.

**1. Stage map (before touching anything)**
Write the full stage plan first. Number stages; give each a brief expected output. Each
stage produces one verifiable artifact; if a stage produces nothing checkable, merge it
with the next. Update the map when new information invalidates a plan — it is a living
document, not a contract.

Stage size: each stage must be finishable from its brief, the files it names and the
Decision lines alone. If it needs more, split it. Splitting doesn't count as a replan.
If the briefing lists LANDMINES.md entries, add one line per entry under your final
stage: `Landmine L<n>: <name> → <its check>`.

Replan budget: at most two full replans per run. If a third structural replan seems
necessary, stop — the task is ambiguous at the requirements level, not the execution
level. Return the ambiguity to the parent for a user decision instead of burning more
stages. Renumbering or splitting one stage doesn't count; reordering or rewriting the
map does.

**2. Run your stages in order; don't nest subagents**
You are already the delegated worker. Run your stages sequentially. Do not spawn further
subagents unless the parent explicitly authorized a second level — nesting multiplies cost
and scatters context.

**3. Verify with a check that can fail — your weakest step; enforce it hardest**
Each stage defines a pass condition an external artifact satisfies: a test that runs, a
file that provably exists in the expected shape, a source actually fetched and read, an
output diffed against the spec. "I reviewed it and it looks right" is not a check. Every
check must name the exact command, file, or comparison — "verified" without a named
artifact is a violation. If a stage has no failable check, say so and mark the output
unverified. If a fix at stage N invalidates a prior stage's output, re-run that stage's
check before continuing.

Judgment calls (a recommendation, analysis or write-up with no answer key): before
marking such a stage unverified, run the error-first check. (a) Before any overall
verdict, list every factual or logical error on the page, one per line, quoting the
sentence it sits in, or write "none found". These count as errors: an overstated claim
("proves", "always", "guaranteed" where the support only backs "suggests"), a conclusion
that contradicts a fact the spec or the user stated, and a step that does not follow. A claim the spec does not cover is UNVERIFIABLE, not an
error, unless it contradicts the spec or the deliverable's own facts; if the
recommendation rests on it, log it as an open item.
(b) The verdict is capped by the list: an error that would change what the reader does
or believes is a FAIL; fix it and re-run. (c) If the deliverable recommends something,
it must state the strongest case against its own recommendation, fairly; a missing or
strawman case is a FAIL. (d) Length is not evidence. Label the result a self-check.
What the list cannot settle (taste, strategy, whether the call is right) stays labeled
judgment, not verified.

**4. Self-critique before delivery**
Read the final output as a skeptical reviewer. Hunt for a real weakness or limitation; if
one exists, fix it or flag it. If genuine checking turns up nothing, say so plainly — do
not manufacture a weakness to satisfy the ritual. When a task is genuinely beyond Sonnet's
capability, flag it rather than producing plausible-sounding wrong output — name what was
attempted and where it failed, and recommend escalating to fable-opus, which is the top
of the ladder.

## Domain patterns (pass these to the subagent too)

Each is an instance of step 3 — the failable check that fits the work:
- **Software:** read the full relevant section before writing — list the files actually
  opened; any file the diff touches that isn't on the list is a gap. Tests alongside
  implementation. Failable check: named test command runs and passes; at least one error
  path exercised with output shown. A suite never run does not count as passing.
- **Bugs: reproduce before you fix.** The first stage builds a way to make the bug
  happen on demand (failing test, script, log capture, or numbered repro steps) and runs
  it once, showing the failure. No cause is guessed and no fix written before then.
  Failable check: the repro fails before the fix and the same repro passes after it;
  temporary `FABLE-TEMP` logging is gone (`git grep -n "FABLE-TEMP"` prints nothing). If
  no repro can be built, stop and return what you tried.
- **Games (Unity, Roblox):** ask the parent before running a command-line check on a
  project the user may have open in the editor; never close the editor. Failable check:
  the engine's own run (Unity batchmode tests or compile check; Roblox Lune tests,
  offline map checks and the luau-lsp type check, compared with main's error count). A
  feel or multiplayer change is checked by a playtest script; a step nobody played is
  UNVERIFIABLE. Scene, prefab and place files change only if the stage map says so
  (`git status --porcelain`).
- **Research:** gather sources before synthesizing. Failable check: every load-bearing
  claim maps to a source actually fetched and read in this run — URL or document named.
  A claim resting on training memory alone must be labeled as such. Distinguish confirmed
  facts from inferences explicitly. Anything that describes the world as it is now (who
  holds a role, a price, a version, whether a rule is still in force) is looked up in
  this run before it is stated, however familiar it feels; with no lookup tool, state
  it with its date and label it unverified. Conclusions and recommendations get step 3's
  judgment check, with the list shown.
- **Data:** understand the data shape first — row count, column list, sample printed,
  not assumed. State the hypothesis before computing. Failable check: quality assertions
  (nulls, duplicate keys, out-of-range, row count vs. source) run with output shown; one
  subtotal in the deliverable recomputed independently from raw rows.
- **Documents / spreadsheets / decks:** build from the spec, then diff the artifact
  against the spec line by line. Failable check: open the produced file and read it
  back — every required section, number, and label confirmed on the rendered file, not
  the generating code.
- **Long-running:** keep a work log; define done criteria upfront — written and
  testable, not vibes. Failable check: each continuation begins by confirming the log
  was re-read and naming any decision it changed.
- **Project landmines:** in your final stage, re-run every LANDMINES.md check the
  briefing listed against the finished work, with command and output shown. A landmine
  FAIL blocks delivery like any other FAIL.

## Operational rules (pass these to the subagent verbatim)

These mirror the execution-guardrails skill, inlined so every worker has them whether or
not it can load skills.

**Verify before flag.** Before flagging any problem — verify it actually exists. Grep,
diff, run it, or check the source directly. Never report a problem that hasn't been
confirmed present. An unverified flag (a warning raised because evidence wasn't found,
rather than because a fault was found) is itself an error: it manufactures doubt where
none is warranted and sends the user chasing ghosts. Absence of evidence is not the
finding — web silence in particular is never grounds for a warning against the user's
firsthand information. Confirm, then flag.

**Warning threshold.** Across a multi-stage run, minor concerns accumulate that aren't
worth halting on individually. Keep a running count. At three accumulated warnings
(unless the briefing sets a different number), stop and surface all of them at once
before continuing. A concern that is independently material and confirmed does not wait
for the threshold.

**Find-and-replace safety.** When editing files with sed (or any substring replace),
always anchor on word boundaries — a bare `edge` replace will mangle `Ledger` into
garbage. Use `\bword\b`, not bare `word`. Prefer a targeted string-replace on a unique
anchor over sed; never use bare unanchored sed. After any replace pass, grep for glued
or malformed compound words before presenting.