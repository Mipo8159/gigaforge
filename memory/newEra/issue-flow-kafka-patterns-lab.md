---
name: issue-flow-kafka-patterns-lab
description: "newEra/issue-flow — Giga's hands-on lab for Kafka/Outbox/Inbox/DLQ/CQRS/GraphQL/Sagas; 4 Nest 12 services, built ONE step per round"
metadata:
  node_type: memory
  type: project
  originSessionId: ca3f0323-b315-4e60-9819-48637d2cc490
  modified: 2026-09-29T19:06:12.398Z
---

`newEra/issue-flow` is a learning lab (started 2026-09-29): Giga must get hands-on with Kafka, outbox/inbox, CQRS, GraphQL, DLQ and sagas "as fast as humanly possible". Four NestJS 12 services — issues (producer, :3001), audit, watchers, search (consumers :3002-3004) — each with its own Postgres DB; one topic `issues.events` (3 partitions), three consumer groups.

Roadmap in README: 00 baseline ✅ → 01 outbox → 02 inbox → 03 retries+DLQ → 04 event evolution → 05 CQRS → 06 GraphQL → 07 saga → 08 prod-grade.

**Why:** the goal is *seeing the flow and seeing it break*, not shipping. Comprehension is the deliverable, like [[auctionize-real-goal-is-transcoding-template]].

**How to apply:**
- ONE step per round, then stop so Giga can run it and commit ([[giga-commits-are-mine-to-make]]). Each step = code + docs/steps/NN-*.md with Mermaid at every level (context, container, kafka topology, component, sequences) + "break it" exercises whose outputs were ACTUALLY run. Render Mermaid with `npx @mermaid-js/mermaid-cli` and look at the PNG — parsing isn't enough (a note overflowed once).
- Step 07 saga design was deliberately left OPEN — Giga chose "decide at step 7". Options on the table: add a 5th service (e.g. projects with WIP limit) or give watchers a veto.
- Decisions already made, don't relitigate: own thin Kafka wrapper in libs/kafka (not @nestjs/microservices); client is @platformatic/kafka (KafkaJS dead since 2023, Confluent client has no Node 26 prebuilt and compiles librdkafka for 5+ min); Mermaid in repo for the detailed step docs, BUT Giga's primary view is an animated browser page per step: docs/visual/step-NN.html (self-contained inline SVG + buttons that animate a message through happy path and failure scenarios). Giga rejected long instruction pages: "I need something more simpler, not instructions to list down and read by pages." Keep instructions to one line of commands. Test the page headlessly with the puppeteer in ~/.npm/_npx (mermaid-cli's), clicking every button.
- Nest 12 is ESM: `.js` relative imports, tsc builder (NOT the rspack default) rewrites `@app/*` aliases; entryFile is `apps/<x>/src/main`, output `dist/apps/<x>/apps/<x>/src/main.js`.
- Consumer gotchas already hit and fixed: ghost members after kill -9 stall the group (client default session 60s/rebalance 102s → set 10s/15s); finite consumer retries crashed the process on broker restart (now `retries: true`); awaiting consume() in bootstrap blocked HTTP.
- Killing services from Bash: use the port (`ss -ltnp | grep :300x`), never `pkill -f dist/apps/...` — it matches its own shell.

## Where we stopped (2026-09-29, end of day 1)

- **Done:** step 00 built and verified. Code, `docs/steps/00-baseline.md` (Mermaid + 7 exercises A–G), animated `docs/visual/step-00.html` (3 scenario buttons, puppeteer-tested light/dark/phone), `scripts/create-issue.sh` + `scripts/inspect.sh`, `npm run dev` via concurrently (no `-k`, so a chaos crash doesn't kill the others).
- **State left behind:** Docker infra (postgres, kafka, kafka-ui) still running with 1 clean-slate issue (FLOW-1). Services stopped. NOT a git repo yet — Giga does `git init` + first commit.
- **Giga's homework before step 01:** click through step-00.html, run exercises A–G for real, answer the 5 "check yourself" questions at the bottom of 00-baseline.md.
- **Next session starts with:** "step 1" → Transactional Outbox. Plan: `outbox` table in issues_db written in the SAME TypeORM transaction as the issue; a polling relay publishes unsent rows and marks them sent (at-least-once, so duplicates are expected → sets up step 02). Deliverables: code + docs/steps/01-outbox.md + docs/visual/step-01.html where the "Kafka down" button now shows the event waiting in the outbox and flushing when Kafka returns (nothing lost). Rerun exercises B and D to prove it.
- **Start sessions from inside `newEra/issue-flow/`** — it has its own `.claude/settings.local.json` pointing at this shared memory dir (see [[session-setup-works-from-either-folder]]).
