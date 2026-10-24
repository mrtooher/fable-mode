# fable-mode

> **Current: v6.1 (2026-10-24)** — adds an error-first judgment check and a dissent
> check to step 3 for prose with no answer key (see `bench/judgment/`). Live skills: `fable-mode` (root `SKILL.md`),
> `fable-opus`, `fable-sonnet`, `double-check`, `execution-guardrails`. Ladder: Haiku →
> Sonnet → Opus → the user. `fable-fable`, `fable-haiku` and the v3 `agents/` routing
> are retired — see [SUPERSEDED.md](SUPERSEDED.md). Sections below that describe them
> are kept as history.

Execution discipline for Claude on large tasks: a written stage map, delegation to
named agents where the runtime allows, a verification check at every stage that can
actually **fail**, a skeptical self-review, and a mandatory cold double-check before
anything is delivered.

It is a checklist, not a capability transplant. Benchmarked three times so the README
can say what it does and does not do (see [Evidence](#evidence)).

## The ladder

```
Haiku  →  Sonnet  →  Opus  →  Fable 5.1  →  the user
```

One skill per rung, same core loop, tuned to that tier's known failure mode:

| Skill | Model | Use it when | Known gap it guards |
|---|---|---|---|
| `fable-mode` | whatever is running | default; adapts intensity to the model | — |
| `fable-fable` | Claude Fable 5.1 | the deliverable needs an **audit trail** (worklog, reproducible checks, flagged judgment calls) or spans sessions | none measured — a provenance runner, not an accuracy runner |
| `fable-opus` | Claude Opus | peak synthesis short of Fable; orchestrates Sonnet/Haiku workers | trusts its own introspection; scope growth |
| `fable-sonnet` | Claude Sonnet | balanced default for thorough work | skips the failable check, substitutes "looks right" |
| `fable-haiku` | Claude Haiku | bulk, cheap, parallel mechanical work | skips verification under time pressure |

Two always-on companions:

- `execution-guardrails` — verify-before-flag, warning batching, word-boundary
  find-and-replace. Every model, every task, whether or not the loop runs.
- `double-check` — the delivery gate. A panel of fresh checker agents (Haiku for
  mechanical checks, Sonnet for requirements, Opus to adjudicate) attacks the
  *finished* artifact. Every fable runner calls it before handing anything over.

## Core loop

1. **Stage map first.** Numbered stages, expected output each, one verifiable artifact
   per stage. Living document; at most two full replans per run — a third means the
   requirements are ambiguous, go back to the user.
2. **Delegate by name.** Reasoning stages to a Sonnet worker, mechanical stages to a
   Haiku worker, cold checks to a read-only verifier. Workers don't spawn workers.
3. **Verify with a check that can fail.** A test that runs, a file in the expected
   shape, a source actually fetched, an output diffed against spec. "I reviewed it and
   it looks right" is not a check. Name the exact command or mark the stage unverified.
4. **Self-critique.** Fix or flag a real weakness; a clean pass stated plainly beats a
   manufactured caveat.
5. **Double-check.** Fresh eyes, ternary verdicts (PASS / FAIL / UNVERIFIABLE), fix and
   re-check before delivery.

## v3: delegation is structural

Field feedback on v2 (r/claudeskills): telling a model *in prose* to spawn a worker
almost always runs the task inline. So v3 moves the discipline into real agent
definitions under `agents/`:

- `fable-orchestrator` — **no Write/Edit tool**. It cannot produce artifacts; every
  one must come from a named worker. Opus by default; `fable-fable` runs the same
  definition with `model: "fable"` (per-invocation override, documented for Claude
  Code and confirmed in Cowork).
- `fable-worker-sonnet` / `fable-worker-haiku` — one bounded assignment, exact output
  path, named pass condition, evidence in the report.
- `fable-verifier` — read-only; gets the spec and the artifact, never the producer's
  reasoning.

The skills shrink to routers. Full history in `V3-CHANGES.md`.

## Evidence

Three benchmark rounds, deterministic graders, tasks built with **unstated** traps
(duplicate rows, grep-invisible `getattr("calc" + "_total")`, errata chains superseded
by meeting notes, a real federal data file to fetch or fabricate).

| Tier | Effect of the skill | Source |
|---|---|---|
| Fable 5.1 | **0 delta** — 100/100 in all 16 paired runs (n=2/cell, 4 tasks incl. open-ended real-data fetch); ~1.1× tokens, ~2× wall | `BENCHMARK-2026-09-02.md` |
| Opus / Sonnet | 0 delta on closed graded tasks; **real** on open-ended research — Opus+skill fetched and parsed the NIAAA state dataset, Opus baseline shipped synthetic trend lines | July 2026 rounds |
| Haiku | real but noisy: +25 / −17 across rounds; raises the floor on mechanical diligence, cannot supply synthesis | July 2026 rounds |
| v6.1 judgment check (checker only) | Sonnet checkers: tie, 24/24 both arms. Haiku checkers on subtler errors: 30/30 vs 28/30 — both misses a strawman "case against". Small sample. | `bench/judgment/` |

Read: the loop's value **inverts with model strength**. On Fable 5.1 it buys provenance.
On Opus it buys real sources over plausible ones. On Haiku it buys verification the
model would otherwise skip — sometimes. The harness is in `bench/`; rerun it.

## Install

**Claude Code** (user scope — skills to `~/.claude/skills/`):

```bash
git clone https://github.com/mrtooher/fable-mode.git && cd fable-mode && ./install.sh
```

**Cowork / claude.ai**: Settings → Capabilities → Skills → add each `<name>/SKILL.md`
(root `SKILL.md` is `fable-mode`). The agents are not loadable there; the skills detect
that and fall back to inline mode, saying so.

> **Do not install anything from `agents/` as a skill.** Those files are agent
> definitions: second-person system prompts whose frontmatter carries `tools:` and
> `model:`. Loaded as a skill they land in the main thread and assert things about it
> that are false there — `fable-orchestrator` in particular tells its reader it has no
> Write tool and must delegate to worker agents that do not exist on a skill-only
> surface. The result is a stall, or an inline run narrating a delegation that never
> happened — the exact failure v3 exists to prevent. Agents go in `agents/`, skills go
> in skills.

Folder name must equal the `name:` field in each SKILL.md or the skill will not trigger.

## Files

```
SKILL.md                    fable-mode (default, adaptive)
fable-fable/SKILL.md        Fable 5.1 runner
fable-opus/SKILL.md         Opus runner (orchestrator route)
fable-sonnet/SKILL.md       Sonnet runner
fable-haiku/SKILL.md        Haiku runner
execution-guardrails/       always-on rules
double-check/               delivery gate
agents/                     orchestrator, sonnet worker, haiku worker, verifier
bench/                      fixtures generator, graders, prompts, results.json
BENCHMARK-2026-09-02.md     Fable 5.1 results
EXAMPLE.md                  worked before/after: the failable check catching a bug
V3-CHANGES.md               why delegation became structural
install.sh                  Claude Code installer
```

## When NOT to use it

One obvious approach that fits in a single pass → do it directly. Staging a trivial
task buries the answer under ceremony. The loop earns its cost only when a one-shot
attempt would plausibly miss something — or when you need to show your work.
