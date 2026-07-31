# Repo conventions

Read this before adding or editing a skill.

## Layout

```
skills/<bucket>/<skill-name>/SKILL.md
```

Buckets: `writing/`, `in-progress/`, `personal/`, `deprecated/`. Add a new
bucket only when a skill genuinely doesn't fit an existing one — a bucket with
one skill in it is a category that hasn't earned its name yet.

Keep each skill flat. `SKILL.md` plus sibling `.md` files it links by relative
path. Only add `scripts/` (deterministic helpers the skill executes) or
`assets/` (files that end up in the output) when the skill actually needs them.
A `references/` subfolder for two short files is structure for its own sake.

## Publishing rules

A skill in `writing/` — or any future shipped bucket — must have:

1. An entry in the root `README.md` under **Reference**, linking the skill name
   to its `SKILL.md`, with a one-line description.
2. An entry in `.claude-plugin/plugin.json`.

A skill in `in-progress/`, `personal/`, or `deprecated/` must appear in
**neither**. That's what those buckets mean. Promoting a skill = move the folder
and add both entries in the same commit.

## Writing a skill

- **Frontmatter is `name` + `description` only.** The description is the entire
  triggering mechanism, so it carries both what the skill does and the contexts
  that should invoke it. Lean pushy — under-triggering is the common failure.
- **Lean.** Every sentence loads into context on every trigger. Cut anything not
  changing what the agent does. If a paragraph could be deleted without changing
  the output, delete it.
- **Explain why, don't stack MUSTs.** All-caps imperatives are a yellow flag —
  the model follows reasoning further than it follows rules, and rules without
  reasoning break on the cases you didn't anticipate.
- **Imperative voice.** "Search the corpus," not "you should search the corpus."
- **Generic.** This repo is public. No client names, no internal tooling, no
  personal paths, nothing that only works on my machine.

## Testing

Non-trivial skills get evals before they ship: a few realistic prompts, run with
and without the skill, graded on assertions that a wrong answer would fail.
`skill-creator` runs this loop. A skill that doesn't beat its baseline doesn't
go in a shipped bucket.

## Git

Never commit or push on my behalf. Write the files, show me the diff, I'll push.
