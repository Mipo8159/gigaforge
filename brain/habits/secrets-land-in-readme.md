---
name: secrets-land-in-readme
description: "Giga records the commands and logins they used in a README, so secrets end up there (three times, two projects); scan any README in the diff before handover, and mask what the scan prints."
metadata:
  node_type: memory
  type: feedback
  modified: 2026-08-18T16:00:00.000Z
---

**Twice now** a live `GOCSPX-…` Google client secret has been pasted into
`auxiliary/README.md` alongside the `aws ssm put-parameter` command it belongs
to — once on 2026-08-17 (old client) and again on 2026-08-18 (the new client,
minutes after creating it).

**Why:** the README documents the first-deploy steps, and the natural way to
record "here is the command I ran" is to paste the command *with its arguments*.
The secret rides along. It is a completely understandable habit, not carelessness.

**How to apply:**

1. **Always scan `README.md` before `git add`-ing it:**
   `grep -nE 'GOCSPX|AKIA|ASIA|apps\.googleusercontent\.com|-----BEGIN' README.md`
2. ⚠️ **Mask the match — do NOT print it.** On 2026-08-18 I ran that grep and
   echoed the raw line, putting the live secret into the transcript and forcing
   a rotation that was otherwise unnecessary. Print line numbers only, or pipe
   through `sed -E 's/GOCSPX-[A-Za-z0-9_-]+/<redacted>/'`.
3. To compare a file value against SSM, **hash both and compare digests** —
   never print either side. That part was done correctly.
4. Redact to `'<client-secret>'` placeholders and commit the redacted file;
   the repo should never carry the value at all.

Both times the file was still **untracked**, so git history stayed clean. That
is luck, not process. A pre-commit hook blocking these patterns was offered and
not yet built.

Related: [[auxiliary-is-the-app-auctionize-is-legacy]],
[[auxiliary-free-plan-blocked-four-services]]

**Third time, another project (2026-10-02):** a client repo's uncommitted
README held an environment admin password, a VPN host and password, and user
emails. The background reviewer caught it, reported it without the values, and
the handover told Giga to remove it before staging. So the habit isn't tied to
one repo: **any README in the working tree gets scanned at handover**, and
reviewer prompts should ask for it.
