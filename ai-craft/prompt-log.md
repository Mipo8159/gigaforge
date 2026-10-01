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
