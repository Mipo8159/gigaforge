---
name: retro
description: Deliberate end-of-session reflection — while the whole session is still in context, extract the reusable lessons, prompt lessons, concepts and AI-usage signals into a gigaforge inbox candidate, and give Giga one concrete thing to do better next time. Use when Giga says /retro, "wrap up", "what did we learn", "save session knowledge", or at the end of a long or important session.
---

# Session retro

You have the full session in context, so this is better quality than any
after-the-fact harvest. Use that advantage: be specific and quote.

## 1. Write the candidate file

Path: `/home/mip/Desktop/workdir/sweeft/gigaforge/inbox/<YYYY-MM-DD-HHMM>-<project>-retro.md`

Use exactly the format in
`/home/mip/Desktop/workdir/sweeft/gigaforge/global/hooks/harvest-prompt.md`
(Candidates / AI-usage signals / Journal line). Hold to its "never include"
list: no secrets, no personal data, and no client specifics outside
`project-fact`.

If nothing clears the bar (reusable · evidenced · behaviour-changing · new),
write no file and say so. That is a fine result.

## 2. Coach Giga (in the reply, not the file)

Three short parts:

1. **What went well**: one thing Giga did that made the session better, named
   concretely, so they keep doing it.
2. **One upgrade**: the single highest-leverage change for next time, as a
   rewritten version of one of *their actual prompts* from this session.
3. **Feature to try**: one Claude Code capability they didn't use that would
   have helped here (plan mode, a subagent, a worktree, a hook, /code-review,
   context7, headless `claude -p`…), and the exact moment it would have paid off.

Keep the reply under ~15 lines. Remind them `/curate` promotes the candidate
when they're ready.
