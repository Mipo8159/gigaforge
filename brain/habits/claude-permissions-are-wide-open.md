---
name: claude-permissions-are-wide-open
description: "Global settings grant blanket Bash plus acceptEdits, deliberately chosen on 2026-08-13 — don't treat a lack of prompts as a lack of authorization to think."
metadata: 
  node_type: memory
  type: project
  originSessionId: 5be04712-1d75-48dd-a56d-8b0687a50e72
  modified: 2026-08-13T08:25:57.567Z
---

`~/.claude/settings.json` allows `Bash` outright, sets `defaultMode: auto`,
and allows Read/Glob/Grep/WebSearch/WebFetch/Skill/Artifact/Task. A short `deny`
list still hard-blocks catastrophic commands (`rm -rf /`, `rm -rf ~`, `sudo rm`,
force-push, `mkfs`, `dd` to a device).

**Why:** Giga chose this on 2026-08-13 over a curated allowlist, after being told
plainly that it lets me run any shell command in the tree without asking. They had
already made the same choice for `mogulkhan/.claude/settings.json`.

**How to apply:** the absence of a prompt is not a judgment call being made for me.
Still confirm before anything irreversible or outward-facing — pushing, deploying,
deleting data, touching other projects on this machine — and still look at a target
before overwriting it. Supports [[working-style-interview-then-autonomous-loop]].
