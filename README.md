# gigaforge

Giga's shared brain with Claude, and the record of how working with AI gets
better over time. It does three jobs:

1. **Makes every Claude session smarter**, in any project, by loading a short,
   curated set of habits (`brain/CORE.md`) everywhere.
2. **Learns from every session** without collecting junk: sessions produce
   *candidates*, and only the ones that clear a strict bar become brain.
3. **Measures growth**: an AI-usage scorecard, a concept ladder, a journal.

## How it fits together

```
  any project session (clasico, issue-flow, auxiliary, …)
        │   loads ~/.claude/CLAUDE.md ──@import──► brain/CORE.md   (always-on habits)
        │   + the project's own CLAUDE.md  + the project's memory
        ▼
  end of session ── /retro ──► inbox/   (untrusted candidates, gitignored)
                                  │
                         /curate  │  4-part bar: reusable · evidenced ·
                                  │  changes behaviour · new
             ┌────────────────────┼─────────────────────┬──────────────────┐
             ▼                    ▼                     ▼                  ▼
     brain/habits,patterns   ai-craft/prompt-log   me/scorecard,       project memory
     (+ CORE.md if universal)                      concepts, journal   (client = local only)
```

## Layout

| Path | Purpose |
|---|---|
| `brain/` | curated cross-project knowledge. `CORE.md` is always loaded |
| `memory/newEra/` | newEra projects' shared auto-memory (`~/.claude/memory/newEra` links here) |
| `global/` | installed into `~/.claude`: `CLAUDE.md`, skills, agents, hooks |
| `me/` | scorecard, concepts, journal: *Giga's* growth |
| `ai-craft/` | Track 0, working with Claude: drills, prompt log |
| `tracks/` | technical curriculum (messaging → scaling → k8s → AWS → AI eng) |
| `labs.md` | every connected project and where its memory lives |
| `bin/` | `install.sh` (wire into ~/.claude), `link-project.sh` |
| `.githooks/` | secret scan on commit (prints masked findings only) |

## Commands you'll use

| Command | When |
|---|---|
| `/retro` | end of any meaningful session (2 min) |
| `/curate` | weekly, or when the session-start notice says ≥5 candidates wait |
| `/tutor` | lab work where *you* should write the core |
| `/debug-protocol` | anything broken |
| `/onboard-project` | first session in a repo without a CLAUDE.md |
| `/build-loop` | "build this until it works, don't keep asking me" |
| agents: `reviewer`, `researcher` | second opinion on a diff; cited research brief |

## Setup (also on a new machine)

```bash
git clone <private-url> /home/mip/Desktop/workdir/sweeft/gigaforge
/home/mip/Desktop/workdir/sweeft/gigaforge/bin/install.sh
```
