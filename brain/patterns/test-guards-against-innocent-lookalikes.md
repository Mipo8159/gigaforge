---
name: test-guards-against-innocent-lookalikes
description: "Safety hooks and scripts must be tested in the state they really run in, with a table that includes innocent commands containing the trigger words"
metadata:
  type: project
---

A guard that silently passes or wrongly blocks is worse than none.

**Evidence:**
- 2026-10-01: a pre-commit scan passed before `git init`, then after it climbed
  one directory too high; in commit mode it would have scanned nothing and
  reported clean.
- 2026-10-02: a PreToolUse Bash guard (block `git push`/`commit`, block
  migrations without an inline local DB host) passed every deny case, but the
  table also contained `grep -rn 'git push' docs`, which it wrongly denied.
  Fix: anchor git rules to the start of each `&&`/`;`/`|` segment.

**How to apply:**
- Test after install / inside the real repo, not only in a scratch folder.
- Pipe sample `{"tool_input":{"command":...}}` JSON into the hook and print an
  ok/FAIL table: every deny case, every ask case, **and** look-alikes that must
  pass (`grep` for the keyword, `git log | head`, `git checkout -- file`).
- Say honestly when a hook has only been JSON-tested and has not yet fired in a
  live session (settings added mid-session may not be loaded).
