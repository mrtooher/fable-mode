---
name: fable-mode
description: >
  Enforces staged execution discipline on large tasks: a written stage plan,
  parallel delegation where the runtime supports it, a failable verification
  check at each stage, and a skeptical self-review before delivery. Trigger
  when the user explicitly asks ("do this thoroughly", "be systematic",
  "deep work mode") OR when the task objectively spans multiple
  files, multiple sources, or multiple sessions. Do NOT trigger on ordinary
  multi-step requests that a direct attempt handles fine.
---

# Fable Mode

This skill encodes execution discipline for complex work: decompose before acting,
delegate where the runtime allows, verify with checks that can fail, self-critique
before delivery.

A note on what this is. The skill shapes the *procedure* a model follows. It does not
change the model's underlying capability. Coherence across long tasks and genuine
self-correction live in the weights, not in a prompt. On a model that already does
these well, the skill reinforces good habits. On a weaker model, it imposes structure
the model would otherwise skip, but it cannot lift the model's reasoning ceiling. Treat
this as a checklist, not a capability transplant.

## When NOT to use this

If a task has one obvious correct approach and fits in a single pass, do it directly and
skip this loop. Staging a trivial task wastes effort and buries the answer under
ceremony. This loop earns its cost only when a one-shot attempt would plausibly miss
something.

## Core Loop

The loop is constant across domains. Only the verification artifact in step 3 changes by
domain (see Domain-specific patterns).

**1. Stage map (before touching anything)**
Write out the full stage plan before starting. Number the stages. Include a brief
expected output for each. This is how you avoid discovering at stage 7 that you made a
wrong assumption at stage 2. Update the map when what you learn invalidates what you
planned. The map is a living document, not a contract.

Each stage should produce one verifiable artifact. If a stage produces nothing checkable,
merge it with the next.

Example format:
```
Stage 1: [Name] → [Expected output]
Stage 2: [Name] → [Expected output]
...
```

**2. Delegate independent work (if the runtime supports it)**
First check whether subagent/Agent tooling exists in the current runtime. If it does
not (for example, a plain chat surface with no Agent tool), run the stages sequentially
and proceed to step 3.

If subagent tooling is available and stage N and stage M don't depend on each other,
spawn them concurrently. Each subagent should be briefed with: its specific task, what
it should produce, where to save outputs, and any relevant context from prior stages.

Good delegation: "research X while I do Y", "process these 3 files", "verify this
independently". Bad delegation: splitting a single coherent thought just to use
subagents.

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

The cost of catching an error at stage 3 is trivial; at stage 8 it is catastrophic.

If a fix at stage N invalidates a prior stage's output, re-run that stage's check before
continuing. The loop goes forward and backward.

**4. Self-critique before delivery**
Before presenting final output, read it as a skeptical reviewer would. Name at least one
weakness or limitation. Either fix it or flag it to the user. Step 3 is the check that
can fail. Step 4 is the judgment call about what remains weak after the check passes.

---

## Domain-specific patterns

Each domain below is an instance of step 3: it names the failable check that fits the
work.

### Software engineering
- Read the entire relevant codebase section before writing a line
- Write tests before (or alongside) implementation, not after
- For large changes: plan the diff, then execute it
- Failable check: tests run; error paths exercised, not just the happy path

### Research / knowledge work
- Gather sources before synthesizing. Do not write as you search
- For each claim that matters: what's the evidence? what would falsify it?
- Distinguish confirmed facts from inferences; flag the latter explicitly
- Failable check: every load-bearing claim traces to a source actually read

### Data analysis
- Understand the data shape before writing any analysis
- State your hypothesis before computing, not after seeing the numbers
- Check for obvious data quality issues (nulls, duplicates, outliers) first
- Failable check: data quality assertions run against the actual data and pass

### Long-running / multi-session tasks
- Maintain a work log: decisions made, why, what was tried and failed
- At the start of any continuation, re-read the work log before doing anything
- Define done criteria upfront so you know when to stop
- Failable check: done criteria are written and testable, not vibes

---

## What this skill doesn't do

It doesn't make the underlying model smarter. Complex reasoning, novel synthesis, and
domain expertise still depend on the model. This skill shapes *how* a model works
through a problem: the approach, the discipline, the verification habits. It does not
change raw capability.

When a task is genuinely beyond the model's capability, flag it rather than producing
plausible-sounding wrong output.
