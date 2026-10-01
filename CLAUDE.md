# gigaforge: working inside the brain repo

This repo is Giga's shared brain with Claude: curated habits, project memories,
the skills/agents/hooks installed globally, and the record of how Giga's AI
skill grows. `brain/CORE.md` is already loaded (via `~/.claude/CLAUDE.md`).

## Layout and who writes what

| Path | What | Written by |
|---|---|---|
| `brain/CORE.md` | always-on rules, ≤ ~120 lines | `/curate` only |
| `brain/habits/` | how we work together (one fact per file, memory frontmatter) | `/curate` |
| `brain/patterns/` | reusable technical decisions (library picks, gotchas, designs) | `/curate` |
| `memory/<project>/` | project facts; a project's `autoMemoryDirectory` points here | auto-memory |
| `inbox/` | **gitignored** harvest candidates, untrusted | SessionEnd hook, `/retro` |
| `me/scorecard.md` | AI-usage scores, re-scored monthly | `/curate` + Giga |
| `me/concepts.md` | topic → seen / explain / build / teach | `/curate` + Giga |
| `me/journal/` | one file per day, 3 lines per session | `/curate` |
| `ai-craft/` | Track 0: drills + prompt log | Giga + Claude |
| `global/` | installed into `~/.claude` by `bin/install.sh` (symlinks) | edit here, never in ~/.claude |

## Rules for this repo

- **Never commit** (see CORE). Hand over a summary instead.
- Before handover, run `.githooks/pre-commit` manually; it is the secret scan.
- Editing a skill/agent/hook: edit under `global/`. The symlinks make it live
  immediately. Say which sessions need a restart (hooks and CLAUDE.md load at
  session start).
- `brain/` entries use the same frontmatter as memory files
  (`name`, `description`, `metadata.type`) and link with `[[name]]`.
- Pruning counts as progress too. A smaller CORE.md that says the same thing
  is a better one.
