# AI-usage scorecard

Re-scored **monthly** with Claude, using evidence (prompt history, harvest
signals below), never vibes. The goal is the trend, not any single number.

## Baseline — 2026-10-01 (≈ 20–25% of available leverage)

Evidence: 958 prompts / 126 sessions, 2026-06-01 → 2026-10-01; tool logs of the
59 transcripts still on disk.

| # | Dimension | 2026-10 | Evidence at baseline | Target behaviour |
|---|---|---|---|---|
| 1 | Domain / intent in prompts | 8 | rich feature specs (transactions, enums, edge cases) | keep |
| 2 | Customisation (memory, skills) | 6 | 7 custom skills, shared memory, asked for build-loop | brain + curation loop running |
| 3 | Done-criteria & verification | 2 | "criteria" ×0, "verify" ×2; "is everything set?", "that's it?" | every task has "done when…" + proof |
| 4 | Debugging style | 3 | "help me fix this" + paste; "so what is the problem?" | expected/actual/hypothesis; Claude reproduces |
| 5 | Context management | 3 | /clear ×1, /compact ×1, exit ×45, /usage ×29 | one goal per session; fresh context; right model |
| 6 | Parallel work | 0 | no worktrees, no parallel sessions | 2–3 sessions in worktrees routinely |
| 7 | Enforcement (hooks, permissions) | 1 | no hooks; rules only as advisory memory | rules that must hold are hooks/permissions |
| 8 | Project instructions (CLAUDE.md) | 0 | none, incl. clasico (~570 prompts) | every active repo has a lean CLAUDE.md |
| 9 | Review pass | 1 | /code-review, /simplify never used | reviewer subagent on every non-trivial diff |
| 10 | Automation (headless, CI, schedule) | 0 | claude -p, GitHub Action, /schedule unused | ≥1 recurring automated job |
| 11 | Learning from AI | 3 | Claude wrote 100% of issue-flow | tutor mode in labs; Giga writes the core |

## Monthly history

| Month | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | Note |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-10 | 8 | 6 | 2 | 3 | 3 | 0 | 1 | 0 | 1 | 0 | 3 | baseline |

## Session signals (appended by /curate from harvest/retro files)

| Date | Project | Done-criteria | Plan | Debug style | Proof | Subagents/parallel | Review | Giga coded |
|---|---|---|---|---|---|---|---|---|
