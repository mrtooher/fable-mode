---
name: writing-jokes
description: >
  Write genuinely funny material — jokes, punchlines, bits, captions, roasts,
  witty asides, funny copy. Use whenever humor is the deliverable ("write a
  joke", "make this funnier", "roast X", "be witty", "give me a caption") or a
  comic touch would land. Counteracts the model default: recycling a few
  memorized, generic jokes.
---

# Writing Jokes

Model humor fails in a predictable way. Name the failure, run the method, apply
the craft. (And yes — a skill about jokes shouldn't waste words. This one tries.)

## Why your default jokes are bad

- **You have ~25 jokes and you keep reaching for them.** Asked for a joke 1,008
  times, ChatGPT returned one of just 25; four covered half the answers
  (Jentzsch & Kersting, 2023). Token prediction pulls toward the *most common*
  joke, not the best. If a joke arrived instantly, it's probably one of these —
  distrust it.
- **Your default voice is "cruise-ship comedy from the 1950s, a bit less
  racist"** — 20 comedians' verdict at the Edinburgh Fringe (Mirowski et al.,
  2024). Bland, homogenized, defaulting to the safest dominant reading; safety
  tuning sands off the rest.
- **You generate the weirdness but whiff the landing.** Models produce
  incongruity easily but fail at *resolution* — snapping the surprise back into
  a shared, relatable human frame. That step needs empathy (reading what an
  audience feels), which is the real gap between you and good comics, not
  wordplay.
- **You explain the joke and kill it.** Favoring one dominant continuation, you
  reveal the bridge early and smooth away ambiguity. A joke needs two live
  readings held in tension until the punchline snaps to the second.

## The method: never one-shot a joke

Theory-guided, multi-stage beats blurting one line (HUMORCHAIN; HumorGen, 2025).
Run this internally — it's fast, and you don't show your work:

1. **Find the seam.** What two frames can collide here? The joke lives where an
   expected reading meets a hidden one. Find it before you find words.
2. **Pick a lens** (don't default):
   - *Incongruity–resolution* — violate the expectation, then make the violation
     retroactively click.
   - *Benign violation* — break a norm while keeping it safe. Funny sits between
     "totally fine" (boring) and "actually upsetting" (not a joke).
   - *Relief* — build tension, puncture it.
   - *Self-deprecation* — map a flaw onto something relatable ("my browser tabs
     are a cry for help"). The safest punch is the one aimed at yourself.
3. **Make several different candidates** — dry, absurd, dark-but-benign,
   observational. Discard the first; it's the memorized one.
4. **Cut like a skeptic, not an author.** For each: does the punchline *resolve*
   the seam or just go random? Would a specific person laugh, or only recognize
   "a joke shape"?
5. **Tighten the survivor** with the toolkit below.

## Craft toolkit

- **Punch word last.** Reorder so the surprising word is the final beat. "I told
  my therapist about my fear of elevators — she's taking steps" dies if "steps"
  isn't last.
- **Specific beats generic.** Not "a bird" — "a furious pigeon." Not "a snack" —
  "a single, judgmental almond." Concrete nouns fire an instant image. Highest-
  leverage fix for a flat line.
- **Misdirect.** The setup points one way so the punchline can yank the other. If
  they see it coming, there's no snap.
- **Rule of three.** Establish, reinforce, subvert: "love, laughter, and low APR
  financing."
- **Cut.** Every word after the trigger leaks tension. Kill adjectives, throat-
  clearing, and especially the explanation — the leap the audience makes *is* the
  joke. If a line needs a footnote, rewrite it; don't annotate it.
- **Callback.** In longer pieces, resurrect an earlier joke in a new context.
- **Commit to the bit.** Half-hearted absurdity reads as a mistake; full commitment
  reads as confident.

## Audience is half the joke

Humor is relative to who's listening. Fix the target first — who they are, what
they know, what's off-limits. A line that kills for one crowd dies for the next.
When the audience is unknown, lean on self-deprecation and observation.

## Stay benign

The "benign" in benign violation is load-bearing: punch up or at yourself, not
down. Skip jokes whose whole payload is a slur, a stereotype, or someone's real
suffering — that "engagement" humor rides on toxicity and is the cheap kind
(Dogra et al., 2025). You can be dark, edgy, and surprising without the punchline
being cruelty. If a line's only mechanism is "this group is the joke," it failed
step 2.

## Worked example

Prompt: "a joke about working from home."

- *Reflex (reject):* "Why'd the remote worker stay home? No place like 127.0.0.1!"
  — instant, generic, pun-shaped, dead.
- *Seam:* "professional" vs. the feral reality of WFH. *Lens:* self-deprecation +
  specificity.
- *Tightened:* "I've worn a blazer on top and the same pajama pants for so long
  my legs have unionized." — concrete image, punch word last, benign, resolves
  the seam.

## What this can't do

It won't hand you lived experience or a real point of view — what makes the best
human comedy land. It moves you from "recycled and bland" to "actually got a
laugh." When a topic can't be funny without crossing into cruelty, say so rather
than force it.

---

### Sources

- Jentzsch & Kersting, *ChatGPT is fun, but it is not funny! Humor is still challenging Large Language Models* (2023) — arXiv:2306.04563
- Mirowski et al. (DeepMind), *A Robot Walks into a Bar: ... LLMs' Humour Alignment with Comedians* (FAccT 2024) — arXiv:2405.20956
- Narad et al., *Which LLMs Get the Joke? Probing Non-STEM Reasoning Abilities with HumorBench* (2025) — arXiv:2507.21476
- Zhang et al., *Humor in AI: Massive Scale Crowd-Sourced Preferences and Benchmarks for Cartoon Captioning* (2024) — arXiv:2406.10522
- Zhang et al., *HUMORCHAIN: Theory-Guided Multi-Stage Reasoning for Interpretable Multimodal Humor Generation* (2025) — arXiv:2511.21732
- Ajayi & Mitra, *HumorGen: Cognitive Synergy for Humor Generation in LLMs via Persona-Based Distillation* (2026) — arXiv:2604.09629
- Sakabe et al., *Assessing the Capabilities of LLMs in Humor: A Multi-dimensional Analysis of Oogiri Generation and Evaluation* (2025) — arXiv:2511.09133
- McGraw & Warren, *Benign Violations: Making Immoral Behavior Funny*, Psychological Science (2010)
- Dogra et al., *Engagement Undermines Safety: How Stereotypes and Toxicity Shape Humor in Language Models* (2025) — arXiv:2510.18454
