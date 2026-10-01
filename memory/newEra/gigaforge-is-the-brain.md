---
name: gigaforge-is-the-brain
description: Giga's cross-project brain repo at sweeft/gigaforge (built 2026-10-01) — brain/CORE.md loads in every session via ~/.claude/CLAUDE.md; this newEra folder now holds only newEra project facts.
metadata:
  type: project
---

`/home/mip/Desktop/workdir/sweeft/gigaforge` (private GitHub repo `gigaforge`,
Giga pushes it) is the centre of the setup since 2026-10-01:

- `brain/CORE.md` is the always-on habits file, imported by `~/.claude/CLAUDE.md`.
  The six cross-project habits that used to live here (interview-then-loop,
  argue back, never commit, don't strip architecture, mask secrets, wide-open
  permissions) moved to `brain/habits/`.
- This folder physically lives at `gigaforge/memory/newEra`;
  `~/.claude/memory/newEra` is a symlink to it.
- Skills/agents/hooks are edited under `gigaforge/global/` and symlinked into
  `~/.claude` by `gigaforge/bin/install.sh`, which Giga runs (auto-mode blocks
  Claude from changing its own config/memory index, correctly).
- Growth loop: `/retro` → `gigaforge/inbox/` → `/curate` → brain. The
  automatic SessionEnd harvester was designed but **blocked by auto mode as
  unauthorized persistence**. It needs Giga's explicit go-ahead before it's built.
- clasico memory stays local (client-confidential), never in gigaforge.

**Why:** Giga wants the brain to improve after every session from any project,
without collecting garbage, and to measure their AI-usage growth (baseline
≈20–25%, `gigaforge/me/scorecard.md`).

**How to apply:** global lessons go to gigaforge via `/retro` + `/curate`,
not into this folder. See [[issue-flow-kafka-patterns-lab]],
[[session-setup-works-from-either-folder]].
