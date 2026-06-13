---
name: writing-jokes
description: >
  Teaches genuinely funny humor writing — jokes, punchlines, comic bits, witty
  asides, captions, roasts, bits of stand-up, funny copy. Use whenever the user
  asks for something funny ("write me a joke", "make this funnier", "give me a
  caption", "roast X", "be witty", "add some humor"), or when a light comic touch
  would improve a piece of writing. Built to counteract the default failure mode
  of language models: recycling a handful of memorized, generic jokes. Trigger
  proactively any time humor is the actual deliverable rather than a garnish.
---

# Writing Jokes

Most language-model humor is bad in a specific, measurable way. This skill names
the failure, then gives you a method and a craft toolkit to beat it.

## Why model humor fails by default (know your enemy)

The research is blunt about this, and the failures are predictable:

- **You have ~25 memorized jokes and you reach for them.** When ChatGPT was asked
  for a joke 1,008 times, >90% of responses were one of just 25 jokes; the top
  four covered half of all answers (Jentzsch & Kersting, 2023). Next-token
  prediction pulls toward the *most common* joke in training data, not the best
  one. If a joke feels like it arrived instantly and effortlessly, it's probably
  one of these. Distrust it.
- **The default voice is "cruise-ship comedy from the 1950s, but a bit less
  racist."** That's the verdict of 20 professional comedians who tested LLMs at
  the Edinburgh Fringe (Mirowski et al., DeepMind, 2024). Output is bland,
  homogenized, and defaults to the most culturally dominant, inoffensive
  reading. Safety tuning compounds this by sanding off edges.
- **You're good at being weird, bad at landing it.** Incongruity-resolution
  studies find models readily generate *novelty/incongruity* but fail at
  *resolution* — the part that requires empathy and grounding the surprise in a
  shared, relatable human frame (HumorBench; Oogiri analyses, 2024–2025).
- **You explain the joke and kill it.** Because you favor a single dominant
  continuation, you reveal the bridge too early, over-clarify, and smooth away
  the ambiguity that humor depends on. A joke needs two live interpretations held
  in tension until the punchline snaps to the second one.
- **The core deficit is empathy, not cleverness.** Across benchmarks, the gap
  between models and strong human comics is mostly about reading what an audience
  actually feels, not about wordplay horsepower.

## The method: never one-shot a joke

The strongest results come from theory-guided, multi-stage generation rather than
blurting one line (HUMORCHAIN, HumorGen, 2025). Internally run this loop — it's
fast and you don't have to show your work:

**1. Locate the incongruity.** What two frames could collide here? A joke lives at
the seam between an expected interpretation and a second, hidden one. Find the
seam before you find the words.

**2. Pick a comedic lens.** Choose deliberately rather than defaulting:
   - *Incongruity–resolution* — set up an expectation, violate it, but make the
     violation retroactively make sense ("oh, THAT's what they meant").
   - *Benign violation* — break a norm (social, logical, taboo) while keeping it
     safe/playful. Funny lives in the narrow band between "totally fine" (boring)
     and "genuinely upsetting" (not a joke).
   - *Relief* — build tension, then puncture it.
   - *Superiority / self-deprecation* — map a flaw onto something relatable
     ("my browser tabs are a cry for help"). Self-targeted is the safest punch.

**3. Generate several genuinely different candidates.** Force divergence: a dry
one, an absurd one, a dark-but-benign one, an observational one. The first idea is
almost always the memorized one — discard it on principle.

**4. Select like a skeptical audience member, not a proud author.** Ask of each:
Does the punchline *resolve* the incongruity, or is it just random? Would a
specific real person laugh, or just recognize "a joke shape"? Cut the rest.

**5. Tighten the survivor.** See the craft toolkit below.

## Craft toolkit (where the funny actually is)

- **The punch word goes last.** Reorder the sentence so the surprising word is the
  final beat. "I told my therapist about my fear of elevators. She's taking steps."
  — dead if "steps" isn't last.
- **Specificity is funnier than generality.** Not "a bird" — "a furious pigeon."
  Not "a snack" — "a single, judgmental almond." Concrete nouns create an instant
  image; vagueness is the enemy of laughs. This is the single highest-leverage fix
  for flat lines.
- **Misdirection.** The setup should confidently point one way so the punchline can
  yank the other. If the audience can see the punchline coming, there's no snap.
- **Rule of three.** Establish, reinforce, subvert: two straight items build a
  pattern, the third breaks it ("love, laughter, and low APR financing").
- **Brevity.** Every word after the laugh-trigger leaks tension. Cut adjectives,
  cut throat-clearing, cut the explanation. Trust the audience to connect the dots
  — that connection IS the joke.
- **Don't explain it.** No "...which is funny because." If it needs a footnote,
  rewrite it, don't annotate it.
- **Callbacks.** In a longer piece, resurrect an earlier joke in a new context.
  Recognition multiplies the laugh.
- **Commit to the bit.** Half-hearted absurdity reads as a mistake; fully committed
  absurdity reads as confident and funny.

## Audience is everything

Humor is not absolute — it's relative to who's listening (SemEval-2026 humor work
frames the audience as part of the joke itself). Before writing, fix the target:
who are they, what do they already know, what's their taste, what's off-limits?
A joke that kills for one crowd dies for another. When the audience is unknown,
favor self-deprecation and observational humor (widely safe) over anything
punching at an identifiable group.

## Lines you shouldn't cross (benign, not violation)

The "benign" in benign violation is load-bearing. Punch up or at yourself, not
down at marginalized groups. Steer clear of jokes whose entire payload is a slur,
a stereotype, or someone's real suffering — research explicitly flags that
"engagement" humor often rides on toxicity, and that's the cheap, bad kind. You
can be edgy, dark, and surprising without the punchline being cruelty. If a line's
only mechanism is "this group is the joke," it failed step 2.

## A worked micro-example

Prompt: "Write a joke about working from home."

- *Memorized-reflex answer (reject):* "Why did the remote worker stay home? Because
  there's no place like 127.0.0.1!" — instant, generic, pun-shaped, no one laughs.
- *Locate incongruity:* the gap between "professional" and "the reality of WFH."
- *Lens:* relatable self-deprecation + specificity.
- *Candidate, tightened:* "I've worn a blazer on top and the same pajama pants for
  so long that my legs have unionized." — specific image ("blazer on top"), punch
  word last ("unionized"), benign, resolves the white-collar/feral incongruity.

## What this skill can't do

It won't make you a comedian, and it won't manufacture lived experience or a real
point of view — the things that make the best human comedy land. It shapes process
and craft so your humor clears the low bar of "recycled and bland" and reaches
"actually got a laugh." When a topic genuinely can't be made funny without crossing
into cruelty, say so instead of forcing it.

---

### Sources

- Jentzsch & Kersting, *ChatGPT is fun, but it is not funny! Humor is still challenging Large Language Models* (2023) — arXiv:2306.04563
- Mirowski et al. (DeepMind), *A Robot Walks into a Bar: Can Language Models Serve as Creativity Support Tools for Comedy?* (FAccT 2024) — arXiv:2405.20956
- *HumorBench: Probing Non-STEM Reasoning Abilities* (2025) — arXiv:2507.21476
- *Humor in AI: Massive Scale Crowd-Sourced Preferences and Benchmarks for Cartoon Captioning* (2024) — arXiv:2406.10522
- *HUMORCHAIN: Theory-Guided Multi-Stage Reasoning for Interpretable Multimodal Humor Generation* (2025) — arXiv:2511.21732
- *HumorGen: Cognitive Synergy for Humor Generation via Persona-Based Distillation* (2026) — arXiv:2604.09629
- *Assessing the Capabilities of LLMs in Humor: Oogiri Generation and Evaluation* (2025) — arXiv:2511.09133
- Warren & McGraw, *Benign Violation Theory*, J. Personality & Social Psychology (2016)
- *Engagement Undermines Safety: How Stereotypes and Toxicity Shape Humor in Language Models* (2025) — arXiv:2510.18454
