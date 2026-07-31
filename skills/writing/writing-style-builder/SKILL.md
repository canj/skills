---
name: writing-style-builder
description: Reverse-engineer how a person actually writes from their real
  writing — chat sessions, sent email, Slack, docs, notes, published posts —
  and package it as a reusable voice/style skill they load before drafting.
  Use whenever someone wants AI to "write like me" or "sound like me," asks
  for a writing style skill, voice guide, tone-of-voice doc, or style guide,
  says drafts don't sound like them, wants to stop AI writing from sounding
  like AI, or asks you to learn their voice from their emails, Slack, Notion,
  Drive, or notes — even if they never say the word "skill."
---

# Writing Style Builder

Build a voice guide from someone's real writing, not from adjectives.
"Professional but approachable" produces competent prose that belongs to
nobody. A voice is a set of observable habits — sentence length, how they
open, punctuation tics, words they never use — and every one can be proven
with a quote from their corpus. Anything you can't quote is a guess, and
guesses are what make output feel generic.

Show your work after Phase 2 and Phase 4. The user is the only one who can
tell you you've misread them.

## 1. Scope

Ask three things: what they write most, who reads it, and whether this is for
drafting from scratch or cleaning up AI output. Don't turn it into an interview.

## 2. Gather

Offer only sources you can actually reach: their past chat sessions (their
messages only), sent email, Slack/Teams/Discord, Drive/Notion/Obsidian,
published posts, pasted files. No connectors? Ask for 5–10 pasted samples —
enough for a first pass, and say so rather than treating it as failure.

Sampling rules matter more than volume:

- **Only text they wrote.** No AI drafts, forwards, quotes, templates. A
  polluted corpus teaches you to imitate the exact thing they're escaping.
  Can't tell? Ask.
- **Sent beats drafted; published beats sent.** Stakes produce voice.
- **3+ channels.** Slack voice ≠ blog voice. A single-channel corpus yields a
  guide that's wrong everywhere except that channel.
- **~20 samples minimum.** Below that, say so and mark findings provisional.
- **Include friction** — pieces where they were annoyed, rushed, or delivering
  bad news. Polish hides the tells.

Report count, sources, date range, and exclusions before analyzing. Let them
fix the corpus before you build on it.

## 3. Extract

Every finding needs a verbatim quote. "Writes conversationally" can't be
checked against a draft; "opens with the ask, no greeting — *'Can you get me
the Q3 numbers by Thursday?'*" can.

Label each `[observed]` (3+ examples) or `[provisional]` (1–2, might be noise).
No evidence for a dimension? Write "no signal" — gaps are information,
fabrications aren't.

Cover:

- **Rhythm** — median sentence length and variance, paragraph length, fragments
- **Openings** — greeting or cold open, ask-first or build-to-it. The first
  sentence is the highest-signal unit in the corpus.
- **Closings** — CTA, sign-off, callback, or just stop
- **Punctuation** — em dashes, ellipses, semicolons, parens, ALL CAPS,
  italics, emoji, exclamation frequency. Note the absences too.
- **Vocabulary** — recurring phrases, contractions, profanity, jargon density,
  hedges vs. flat assertions, metaphor domain (sports? cooking? gaming?)
- **Formatting** — bullets vs. prose, headers, bold, typical length per channel
- **Situational** — disagreement, uncertainty, humor, bad news, asking for
  something, being wrong. Hardest to fake, most valuable to capture.
- **Channel matrix** — tone/length/formality/formatting per channel, plus an
  explicit yes/no per channel for the register-carrying traits: profanity,
  emoji, contractions, ALL CAPS, greetings. These are the ones that embarrass
  you when they leak — swearing in a newsletter where they never swear. Leave
  unsourced rows blank and say which they are.

Count, don't estimate. Sentence lengths, em dash frequency, hedge counts,
emoji totals: run a search or a script. A guide whose numbers are guesses gets
caught the first time the user checks one, and then they stop trusting the
rules too.

Don't flatter. Include the crutch words, hedging, and throat-clearing they'd
want to cut. A guide that captures them only at their best reproduces them at
their worst anyway, because it never named the pattern.

## 4. Negative space

Half a voice is what the person never does, and this is the phase that removes
the AI smell. "Be direct" is weak against a model's defaults; a specific banned
list is strong.

Search the corpus for each candidate before banning it — actually search, don't
recall. Present anywhere means it's theirs, so leave it alone. A Never list is
only worth the searches behind it, and banning a word they use is a bug nobody
catches for months: drafts just quietly stop sounding right.

- **Zero-occurrence AI defaults.** delve, leverage, utilize, foster, robust,
  seamless, comprehensive, landscape, tapestry, journey, testament,
  game-changer, "it's worth noting," "in today's fast-paced world," "let's
  dive in," "at the end of the day," "the key takeaway is."
- **Structural moves they don't make** — rule of three, negative parallelism
  ("it's not X, it's Y"), rhetorical-question openers, restating summary
  paragraphs, superficial -ing clauses ("highlighting the importance of"),
  vague attribution ("experts say").
- **Registers they never hit**, in either direction.

**Then build the opposite list — overrides.** Em dashes, fragment runs, emoji,
lowercase starts, "Look," openers, passive voice: all commonly banned as AI
tells, all genuinely somebody's voice. Every `[observed]` trait a cleanup pass
would strip goes in an OVERRIDES section with its evidence. Skip this and
cleanup files the fingerprints off — worse than doing nothing, because the
result looks clean and reads anonymous.

If a general cleanup skill (humanizer or similar) is installed, don't copy its
universal banned list into the style file. That list is maintained elsewhere
and the two copies drift. The style file owns the *personal* negative space
and the overrides.

Show Phases 3 and 4 before writing the file. It's the highest-leverage
correction point in the process — a misread caught here would otherwise get
baked into every future draft.

## 5. Package

Write to `my-writing-style/SKILL.md`, or a plain `writing-style.md` on
platforms without skills — it's just markdown, so it drops into custom
instructions, CLAUDE.md, AGENTS.md, or a system prompt unchanged.

````markdown
---
name: my-writing-style
description: Write as [NAME]. Use when drafting or editing anything that goes
  out under my name — [CHANNELS]. Apply before the first draft, not as cleanup.
---

# Voice: [NAME]

Built from [N] samples across [CHANNELS], [DATE RANGE].
`[observed]` = 3+ examples. `[provisional]` = 1–2, treat as a guess to test.

## Quick rules
5–8 imperatives, most important first, each checkable against a draft.

## By channel
| Channel | Tone | Length | Formality | Formatting | Greeting |
Unsourced rows: [list them, so nobody assumes coverage].

## Do this
**[Pattern]** `[observed]` — [one-line rule]
> [verbatim quote that proves it]

The quote isn't decoration. A rule without an example gets applied generically.

## Situational
Disagreeing · uncertain · bad news · asking · being wrong — pattern + quote each.

## Never
Words, phrases, structures, and formatting verified absent from the corpus.

## Overrides — don't clean these up
Traits a generic AI-cleanup pass would strip that the corpus proves are mine.
This section outranks any cleanup rule.

## Known tics
Habits present in the corpus to flag in a draft, not imitate.

## Calibration samples
2–3 short real excerpts. Pattern-matching against real prose does more work
than any instruction above.
````

Every rule must be checkable — "short sentences" is useless, "most under 20
words, break it deliberately for emphasis" is a rule. Keep it under ~400 lines;
a guide nobody loads is worthless and a bloated one buries what matters. Carry
the `[observed]`/`[provisional]` labels through.

Before delivering, flag any quote pulled from private email or DMs and offer to
swap it for a published equivalent or redact names. This file gets shared.

## 6. Prove it

Don't declare victory.

1. Pick something real they wrote that you did **not** use as a sample.
2. From a one-line summary of it, redraft it using only the style file.
3. Show yours next to theirs and name three specific misses yourself. Spotting
   your own gaps builds more trust than waiting to be told.
4. Revise the file against those misses. Repeat until the gap is boring.

Almost every "write like me" prompt skips this step. It's the only one that
separates a file that *sounds* right from one that *works*.

## Alongside a cleanup skill

If they have an AI-cleanup skill, the two are complements — worth saying out
loud, because most people assume one replaces the other. Cleanup removes what
isn't human; this file supplies what is theirs. Order: style file at draft
time, cleanup at edit time. If the cleanup skill accepts a voice sample, point
it at the style file. When they conflict the style file wins — it has quotes
from the actual person, the cleanup rule has a population-level prior.

## Standing rules

- **Thin corpus? Ask.** Don't fill the gap with an invented persona — that's
  the exact failure this skill prevents. Under-sourced and honest beats
  complete and wrong.
- **Voice drifts.** Suggest rebuilding in ~6 months, or when drafts stop landing.
- **Updating beats rebuilding.** If a style file exists, revise it from new
  evidence. The `[observed]` findings usually still hold; the `[provisional]`
  ones go stale.
