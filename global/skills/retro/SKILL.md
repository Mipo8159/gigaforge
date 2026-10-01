---
name: retro
description: End-of-session learning — while the whole session is still in context, extract what's reusable, apply it straight to the gigaforge brain (habits, patterns, coaching focus, scorecard, journal, prompt log), secret-scan, commit and push gigaforge, and give Giga one concrete thing to do better next time. Use when Giga says /retro, "wrap up", "what did we learn", "save session knowledge", or is about to exit a meaningful session.
---

# Retro: learn from this session, update the brain, push

Giga asked for the brain to get smarter after every session, automatically,
without collecting junk. This skill is the learner. It runs in-session, so it
has the full context, and Giga is present when it pushes.

`G` = `/home/mip/Desktop/workdir/sweeft/gigaforge`.

## 1. Gather (silently)

- This session: Giga's prompts, corrections, frictions, what worked.
- `G/inbox/*.md`: older candidates (from earlier retros); fold them in too.
- `G/inbox/signals.jsonl`: coach-hook flags per prompt (`no_done`,
  `debug_no_hypothesis`, `multi_task`, `research`, `big_spec`, `vague`).
  Count only the rows since the last row in `me/scorecard.md`'s session table.
  `bin/signals-report.py` gives the monthly rates. Quote the current month
  vs the baseline when a coaching.md bullet is added or retired.

## 2. Apply the bar, then write

Each lesson must be **reusable · evidenced · behaviour-changing · new** (see
CORE.md). Usually 0–3 survive. If none do, still do steps 3–5.

| Lesson | Write to |
|---|---|
| how Giga and Claude should work | `brain/habits/<slug>.md` (memory frontmatter); one CORE.md line only if it should shape *every* session |
| reusable technical decision / gotcha | `brain/patterns/<slug>.md` |
| a prompt that went badly or well | `ai-craft/prompt-log.md` (before → after → why) |
| a concept Giga engaged with | `me/concepts.md` (raise a level only on evidence) |
| project-only fact | leave it to that project's auto-memory; not gigaforge |

Merge into an existing entry rather than adding a near-duplicate. Keep CORE.md
≤ 120 lines: merge or demote to stay under.

**Never write into brain/:** secrets, personal data, or client internals
(product/service names, schemas, URLs). Generalise ("a barrel import cycle
silently renamed a queue") or drop it.

## 3. Update the coaching loop (this is how it builds up)

- `me/scorecard.md`: append one row to the session table (date, project, the
  signals observed).
- `brain/coaching.md` is what the coach hook injects into *every* prompt. Keep
  it at **≤ 5 bullets**, each one a weakness Giga is currently working on,
  with the evidence. Remove a bullet once Giga has shown the better
  behaviour in ~3 sessions running (say so in the retro, since it's a win), and
  add one when a new weakness repeats. A bullet that stays forever
  means the coaching isn't working; change its wording or approach.
- `me/journal/YYYY-MM-DD.md`: append one line: what Giga learned or decided.

## 4. Commit and push gigaforge (Giga's standing request; gigaforge only)

Commit **exactly the files you wrote in this retro**, nothing else:

```bash
G/bin/brain-commit.sh "brain: <what was learned, ≤ 60 chars>" brain/habits/x.md me/scorecard.md ...
```

The helper refuses paths outside `brain/ me/ ai-craft/`, refuses if anything
else is already staged, and runs the pre-commit scan (secrets + client terms).
It never sweeps in Giga's own uncommitted edits. Exit 1 = blocked: fix the
wording (generalise), never `--no-verify`. Exit 2 = nothing changed. A failed
push isn't fatal; say so. Project repos stay untouched (CORE.md "never commit").

## 5. Coach Giga (the reply, ≤ 12 lines)

1. **Learned:** one line per thing that went into the brain (path).
2. **Went well:** one concrete thing Giga did that helped. Keep doing it.
3. **One upgrade:** rewrite one of Giga's *actual* prompts from this session.
4. **Feature you could have used:** the exact moment a subagent, worktree,
   plan mode, hook or `claude -p` would have paid off.
5. The commit hash, and whether it was pushed.
