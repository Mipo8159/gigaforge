# Prompt log: before → after → why

Real prompts, rewritten. `/curate` appends `prompt-lesson` candidates here.
The goal is to *see* your own patterns change over the months.

---

### 2026-10-01: Debugging (seeded from history)
- **Before:** "help me fix this" + 51 pasted lines
- **After:** "Expected the course list to load; it 500s since yesterday's
  migration. Error below. I suspect the new `creatorId` FK. Reproduce it
  first, then fix."
- **Why:** expected/actual + what changed + a hypothesis cuts the search space
  from "anything" to "check one thing first".

### 2026-10-01: Feature request with no proof
- **Before:** "add another endpoint … compare the header with the active version"
  → later "is everything set?"
- **After:** same spec + "Done when: a curl with an older x-app-version returns
  `updateRequired: true`, with a newer or equal one `false`, and the migration
  has run locally. Show me both curls."
- **Why:** "is everything set?" asks Claude to grade its own homework. A
  done-criterion makes it prove the work.

### 2026-10-01: Learning lab
- **Before:** "step 1"
- **After:** "Step 1, outbox, tutor mode. I write the relay. Give me the
  failing test and the table; hints only when I ask."
- **Why:** the first version gets you code to read; the second gets you a
  skill you can use.

### 2026-10-02: Feature with late constraints
- **Before:** "the coinAmount coming from client side is in euros … rate 1 = 10 …
  if nothing is provided it sits as null … help me roll out the agents" → two
  turns later: "we don't need this conversion on migration level, the feature is
  a few days old, and not on prod"
- **After:** "In core, external-content create/update: client sends coinAmount
  in EUR; store coins = round(eur × 10); responses in EUR; null → free lesson on
  approve. No data migration: not on prod. Done when: €4.99 stores 50, null stays
  null, tsc clean. Use build-loop; reviewer before handover."
- **Why:** constraints you already know ("not on prod") remove whole branches of
  work; stating them first cost one question instead of a built-and-deleted
  migration.

### 2026-10-01: State the end goal in the first message (from inbox)
- **Before:** "explain what AI setup we have" → "plan" → "fresh start, rate me,
  maximise Claude"
- **After:** "Goal: maximise how I use Claude and track my growth. First rate my
  current usage from history, then propose a repo to hold it. Keep answers short."
- **Why:** two answers went to goals the third message superseded.


### 2026-10-02: Bug report missing the facts that decide it
- **Before:** "QA can't update the external content, began when I started wrapping the
  returned URL with the CDN … for a 30 minute video admin panel does not show anything,
  AWS says key not found. diagnose, analyze, plan and resolve"
- **After:** "SDQA, submissions 44/46: PUT returns 500 since the CDN wrapping (expected 200).
  A 30-min upload opened in admin right after submit shows NoSuchKey; a 20-s one plays.
  I suspect the signed URL. Access ready: SSO fresh, VPN on. Done when both work on SDQA.
  Split it: logs in background, admin fix in a worktree."
- **Why:** "what changed" was the best part and found bug 1 fast. IDs, the exact error and
  "right after submit" would have removed about 10 tool calls of searching, and stating
  access up front avoids dead ends mid-investigation.

### 2026-10-02: "Done when" that can't be checked, and a scope that hid the real gap
- **Before:** "check admin repository, add the changes to admin side that allows SUPER_ADMIN role
  user to change the user grade … done when: admin can successfully change user grades without
  any issues. use agentic workflow"
- **After:** "Let only the top admin role change a user's grade (all enum values). Check where it's
  enforced, admin and core. Done when, on local core (I'll run it on :3010, login in
  `.env.local`): the top admin sets all 4 grades via the UI, the DB matches, and a lower admin gets
  403. Background reviewer before handover."
- **Why:** "admin side" was the wrong layer: the server let the lower role write the field, so a
  UI-only fix would have passed the stated criterion and still been open. "Without any issues"
  named no environment, user or check, and missing access (core not running, no login) pushed the
  live proof into a second round.
