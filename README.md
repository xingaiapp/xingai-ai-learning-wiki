# XingAI AI-Learning Wiki

A trial run of Andrej Karpathy's [LLM Wiki pattern](raw/_llm-wiki-pattern.md):
instead of re-deriving answers from raw documents on every question, an LLM
agent incrementally builds and maintains a persistent, cross-referenced wiki
that compounds over time.

**Domain:** public XingAI AI-engineering learning material — mainly the
10-course curriculum in
[`xingai-enterprise-ai-design`](https://github.com/xingaiapp/xingai-enterprise-ai-design)
and the runnable
[`claims-workflow-v2-poc`](https://github.com/xingaiapp/xingai-enterprise-ai-pocs)
that the courses keep pointing at. Seeded 2026-07-16; scrubbed the same day
to keep **only public-repo sources** in this public wiki.

## Public-sources-only rule

This repo is public. Do **not** ingest, copy, or summarize material from
private XingAI repositories (product apps, internal ADRs, Opportunity Radar
outputs, unpublished POCs, etc.). Prefer absolute GitHub links to public
repos over local sibling paths.

## Layout

```
raw/            immutable snapshot of public source docs (copied 2026-07-16)
  courses/               10 course READMEs (EN+ZH) + course standard + index
  claims-workflow-v2-poc/  README, PRODUCTION-READINESS.md, architecture.md, ADR-008, ADR-009
  _llm-wiki-pattern.md   the pattern doc itself, for reference
wiki/           everything below this line is LLM-written, human-read
  index.md      start here — content catalog
  log.md        chronological ingest/query/lint record
  overview.md   top-level synthesis
  courses/      one entity page per course
  products/     public POCs (claims-workflow-v2-poc)
  concepts/     cross-cutting patterns (5W+How, Decision Ledger, cache/fallback, MCP governance)
  syntheses/    durable answers filed back instead of left in chat
AGENTS.md       the schema — read this before ingesting, querying, or linting
```

## How to use this

Open `wiki/index.md` first. Point any LLM agent (Claude Code, Codex, etc.)
at this repo with `AGENTS.md` as the schema and ask it to ingest a new
**public** source, answer a question, or run a lint pass.

## Status

Trial / v0. Raw sources are a one-time snapshot from public repos — re-ingest
by hand if those change. If this proves useful, the next step is a small
script that re-syncs `raw/` from public remotes only.

## Disclaimer

Educational / informational only. See [DISCLAIMER.md](DISCLAIMER.md). Wiki
pages may be wrong; raw snapshots may be stale. XingAI gives no warranty.
