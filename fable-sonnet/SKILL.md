---
name: fable-sonnet
description: >
  Run fable-mode execution discipline on Claude Sonnet. Spawns a Sonnet subagent
  that follows the staged loop — stage plan, parallel delegation where the
  runtime supports it, a failable verification check at each stage, and a
  skeptical self-review before delivery. Trigger when the user explicitly asks
  for thorough/systematic/"deep work" handling AND wants it run on Sonnet ("fable
  on sonnet", "stage this on sonnet", "deep work mode, sonnet"). Use as the
  balanced default between Haiku (cheap/fast) and Opus (peak reasoning). Do NOT
  use for ordinary single-pass tasks.
---

# Fable Mode — Sonnet

Run the fable-mode discipline on Claude Sonnet via a subagent. The skill shapes the
*procedure*; the model still sets the reasoning ceiling. Sonnet sits between Haiku and
Opus — strong general reasoning at lower cost than opus. Pick this as the balanced
default for thorough work that doesn't demand peak synthesis.

If a task has one obvious correct approach and fits in a single pass, skip this loop and
do it directly. Staging a trivial task buries the answer under ceremony.

## How to run it

1. Confirm the runtime exposes the Agent tool. If it does not, you cannot pin a model —
   say so and run the loop inline on the current model instead.
2. Spawn an Agent with `model: "sonnet"` and `subagent_type: "general-purpose"`.
3. Brief the agent with: the user's task, where to save outputs, relevant context from
   this session, and the **Core Loop** below as its operating instructions.
4. When the agent returns, relay the result and surface any stage it marked unverified.

For independent sub-parts, spawn multiple Sonnet agents concurrently and merge outputs.
Keep delegation one level deep: the agents you spawn run their stages sequentially and do
not spawn further subagents. Cap concurrency to a handful of agents so cost and context
stay controlled.

## Core Loop (pass this to the subagent)

**1. Stage map (before touching anything)**
Write the full stage plan first. Number stages; give each a brief expected output. Each
stage produces one verifiable artifact; if a stage produces nothing checkable, merge it
with the next. Update the map when new information invalidates a plan — it is a living
document, not a contract.

**2. Run your stages in order; don't nest subagents**
You are already the delegated worker. Run your stages sequentially. Do not spawn further
subagents unless the parent explicitly authorized a second level — nesting multiplies cost
and scatters context.

**3. Verify with a check that can fail**
Each stage defines a pass condition an external artifact satisfies: a test that runs, a
file that provably exists in the expected shape, a source actually fetched and read, an
output diffed against the spec. "I reviewed it and it looks right" is not a check. If a
stage has no failable check, say so and mark the output unverified.

**4. Self-critique before delivery**
Read the final output as a skeptical reviewer. Hunt for a real weakness or limitation; if
one exists, fix it or flag it. If genuine checking turns up nothing, say so plainly — do
not manufacture a weakness to satisfy the ritual. When a task is genuinely beyond Sonnet's
capability, flag it rather than producing plausible-sounding wrong output — and recommend
escalating to fable-mode on opus.

Before flagging any problem — verify it actually exists. Grep, diff, run it, or check
the source directly. Never report a problem that hasn't been confirmed present. An
unverified flag (a warning raised because evidence wasn't found, rather than because a
fault was found) is itself an error: it manufactures doubt where none is warranted and
sends the user chasing ghosts. Absence of evidence is not the finding. Confirm, then flag.

## Domain patterns (pass these to the subagent too)

Each is an instance of step 3 — the failable check that fits the work:
- **Software:** read the full relevant section before writing; tests alongside
  implementation; exercise error paths, not just the happy path.
- **Research:** gather sources before synthesizing; evidence for every load-bearing claim;
  distinguish confirmed facts from inferences explicitly.
- **Data:** understand the data shape before analyzing; state the hypothesis before
  computing; check nulls/duplicates/outliers first.
- **Long-running:** keep a work log; define done criteria upfront; re-read the log before
  any continuation.

## Operational rules (pass these to the subagent too)

**Warning threshold.** Across a multi-stage run, minor concerns accumulate that aren't
worth halting on individually. Keep a running count. At three accumulated warnings, stop
and surface all of them at once before continuing. Three small things pointing the same
direction usually mean one real problem worth a decision.

**Find-and-replace safety.** When editing files with sed (or any substring replace),
always anchor on word boundaries to avoid corrupting compound words — e.g. replacing a
bare `edge` will also mangle `Ledger` into garbage. Use `\bword\b`, not bare `word`.
After any sed pass, grep for glued or malformed compound words before presenting. A
replace that silently corrupts neighboring tokens is the most common self-inflicted
error in file edits.
