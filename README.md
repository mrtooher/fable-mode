# fable-mode

A Claude skill that enforces staged execution discipline on large tasks:
a written stage plan, parallel delegation where the runtime allows, a
verification check at each stage that can actually fail, and a skeptical
self-review before delivery.

## What it does

The skill shapes the *procedure* a model follows on complex work. It makes
the model decompose before acting, delegate independent sub-work where
subagent tooling exists, verify each stage against a failable check rather
than a feeling, and critique its own output before delivering it.

## What it does not do

It does not change the underlying model's capability. Coherence across
long tasks and genuine self-correction live in the model's weights, not
in a prompt. On a model that already does these well, the skill
reinforces good habits. On a weaker model, it imposes structure the model
would otherwise skip, but it cannot raise the reasoning ceiling. Treat it as
a checklist, not a capability transplant.

## When to use it

Trigger on tasks that span multiple files, multiple sources, or multiple
sessions, or when you explicitly ask for systematic execution. Do not use it
on tasks with one obvious approach that fit in a single pass. Staging a
trivial task wastes effort and buries the answer.

## Files

- `SKILL.md` - the skill itself
- `EXAMPLE.md` - a worked before/after showing the verification check catching
  an error that a one-shot attempt ships

## Installation

Place the `fable-mode` directory wherever your Claude environment loads
skills from (for example, a skills directory read by Claude Code), then
invoke it by name or let it trigger on a qualifying task.
