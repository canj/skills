# skills

Agent skills I actually use, published so you can too.

A skill is a folder with a `SKILL.md` in it. The agent reads the description,
decides whether the task matches, and loads the instructions if it does. No
install step beyond putting the folder somewhere your agent looks.

Everything here has been run against real work and, where the output is
checkable, benchmarked against not using it. If a skill didn't beat the
baseline it isn't in this repo.

## Install

Copy the skill folder you want into your agent's skills directory:

```bash
# Claude Code / Cowork
cp -r skills/writing/writing-style-builder ~/.claude/skills/

# or clone and symlink, so you get updates
git clone https://github.com/canj/skills ~/Development/canj-skills
ln -s ~/Development/canj-skills/skills/writing/writing-style-builder ~/.claude/skills/
```

To load the whole collection as a plugin, point your agent at this repo's
`.claude-plugin/plugin.json`.

## Reference

### Writing

- **[writing-style-builder](./skills/writing/writing-style-builder/SKILL.md)** —
  Reverse-engineers how you actually write from your real writing, then packages
  it as a voice guide you load before drafting. Fixes the "AI drafts don't sound
  like me" problem with evidence instead of adjectives.

## How this repo is organized

Skills live in buckets under `skills/`. Buckets are just topics — they don't
affect how a skill runs.

| Bucket | What's in it |
|---|---|
| `writing/` | Voice, drafting, editing |
| `in-progress/` | Drafts. Not listed above, not in the plugin manifest, may change or disappear. |
| `personal/` | Tied to my own setup. Not promoted. |
| `deprecated/` | Retired. Kept for anyone still running them. |

Anything in `in-progress/`, `personal/`, or `deprecated/` is deliberately absent
from the Reference list and from `plugin.json`. If it's not listed above, it's
not ready.

`CLAUDE.md` has the conventions an agent should follow when adding a skill here.

## License

MIT. Use them, fork them, sell the output. Attribution appreciated, not required.
