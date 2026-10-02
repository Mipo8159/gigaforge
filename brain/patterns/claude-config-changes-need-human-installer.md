---
name: claude-config-changes-need-human-installer
description: "In auto mode, edits to Claude's own settings, memory index or background hooks are blocked as self-modification; ship them as a reviewed script Giga runs"
metadata:
  type: project
---

**Evidence (2026-10-01):** the auto-mode classifier denied a memory-index edit
(self-modification) and a background harvest script (unauthorized persistence).
The same changes, put in a reviewed `bin/install.sh` that Giga ran, succeeded.

**Rule:** don't retry or work around that block. Write the change as a script,
show it, and let Giga run it. It is the right trust boundary, and it saves the
failed attempts.
