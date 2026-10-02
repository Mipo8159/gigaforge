# Concepts: what Giga can actually do

Levels: **seen** (read or watched it) → **explain** (explained it unaided,
correctly) → **build** (wrote it yourself, it worked) → **teach** (made someone
else, or a doc, get it). Raise a level only on evidence, and record the evidence.

| Concept | Track | Level | Evidence | Next step |
|---|---|---|---|---|
| Kafka topics / partitions / consumer groups | messaging | seen | issue-flow step 00 (Claude-built) | exercises A–G, then explain back |
| Dual-write problem | messaging | seen | issue-flow step 00 exercises B, D | build outbox in step 01 (tutor) |
| Transactional outbox | messaging | seen | theory | **build**: issue-flow step 01 |
| Inbox / idempotent consumer | messaging | seen | theory | issue-flow step 02 |
| Retries + DLQ | messaging | seen | theory | issue-flow step 03 |
| CQRS | messaging | seen | theory | issue-flow step 05 |
| Saga (choreography vs orchestration) | distributed | seen | earlier `saga` repo | issue-flow step 07 |
| Hexagonal architecture | design | build | mogulkhan slices, auxiliary ports/adapters | teach: write the "why" in your own words |
| DI with decorator metadata (SWC) | node | build | auctionize esbuild → SWC fix | — |
| Serverless on AWS (Lambda, DynamoDB, Cognito) | aws | build | auxiliary deployed 2026-08-18 | explain: single-table design aloud |
| DynamoDB transactional counters | aws | seen | job/quota model (planned) | build in auxiliary upload pipeline |
| Kubernetes | k8s | — | — | track 3 |
| Context engineering (CLAUDE.md, memory, skills) | ai | explain | built gigaforge with Claude | build: own skill with evals |
| Agent orchestration (subagents, background review, worktrees, hooks as guards) | ai | seen | 2026-10-02: asked how agents/hooks/skills were used; saw a background reviewer catch a rollout risk | build: launch a worktree session yourself for a parallel half |
| Agent loops / tool use / MCP | ai | seen | `mcp/` teaching server | build: finish the README syllabus |
