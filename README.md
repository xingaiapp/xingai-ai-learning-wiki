# XingAI AI-Learning Wiki

A trial run of Andrej Karpathy's [LLM Wiki pattern](raw/_llm-wiki-pattern.md):
instead of re-deriving answers from raw documents on every question, an LLM
agent incrementally builds and maintains a persistent, cross-referenced wiki
that compounds over time.

**Domain:** seeded 2026-07-16 from a review of `xingai-enterprise-ai-design/courses/`
(a 10-course AI-engineering curriculum) and `xingai-learn` (a live
interview-pattern-practice product) — including the one real error that
review found and fixed (see
[`wiki/syntheses/review-findings-2026-07-16.md`](wiki/syntheses/review-findings-2026-07-16.md)).
Expanded the same day with three more products that the courses and each
other kept cross-referencing: `claims-workflow-v2-poc`, `xingai-agent-firewall`,
and this session's own `xingai-opportunity-radar` output.

## Layout

```
raw/            immutable snapshot of source docs (copied 2026-07-16)
  courses/               10 course READMEs (EN+ZH) + course standard + course index (EN+ZH)
  xingai-learn/          README + ADR-001..007
  claims-workflow-v2-poc/  README, PRODUCTION-READINESS.md, architecture.md, ADR-008, ADR-009
  xingai-agent-firewall/   README, PRD, ADR-001..006
  xingai-opportunity-radar/ this session's issue, Decision Card, Content Pack, portfolio.yaml
  _llm-wiki-pattern.md   the pattern doc itself, for reference
wiki/           everything below this line is LLM-written, human-read
  index.md      start here — content catalog
  log.md        chronological ingest/query/lint record
  overview.md   top-level synthesis
  courses/      one entity page per course
  products/     one entity page per product (xingai-learn, claims-workflow-v2-poc, xingai-agent-firewall, opportunity-radar)
  concepts/     cross-cutting patterns (5W+How, Decision Ledger, cache-first, MCP/agent governance)
  syntheses/    durable answers to specific questions, filed back instead of left in chat
AGENTS.md       the schema — read this before ingesting, querying, or linting
```

## How to use this

Open `wiki/index.md` first. Point any LLM agent (Claude Code, Codex, etc.)
at this repo with `AGENTS.md` as the schema and ask it to ingest a new
source, answer a question, or run a lint pass — see `AGENTS.md` for the
exact conventions it should follow.

## Status

Trial / v0. Raw sources are a one-time snapshot, not synced to the living
repos (`xingai-enterprise-ai-design`, `xingai-learn`) — re-ingest by hand if
those change. If this proves useful, the natural next step is a small script
or scheduled task that re-syncs `raw/` and triggers a re-ingest pass.

## Disclaimer

Educational / informational only. See [DISCLAIMER.md](DISCLAIMER.md). Wiki
pages may be wrong; raw snapshots may be stale. XingAI gives no warranty.
