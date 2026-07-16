# XingAI AI-Learning Wiki

Chinese: [README.zh.md](README.zh.md)

A trial run of Andrej Karpathy's [LLM Wiki pattern](raw/_llm-wiki-pattern.md):
instead of re-deriving answers from raw documents on every question, an LLM
agent incrementally builds and maintains a persistent, cross-referenced wiki
that compounds over time.

**Domain:** public XingAI AI-engineering learning material — curriculum and
design docs in
[`xingai-enterprise-ai-design`](https://github.com/xingaiapp/xingai-enterprise-ai-design),
POCs in
[`xingai-enterprise-ai-pocs`](https://github.com/xingaiapp/xingai-enterprise-ai-pocs),
patterns in
[`xingai-engineering-system`](https://github.com/xingaiapp/xingai-engineering-system),
and selected
[`xingai-tech-blog`](https://github.com/xingaiapp/xingai-tech-blog) posts.

`raw/` holds snapshots. `wiki/` is a knowledge base: **Known / Missing /
Rethink / Debate / Needs evidence** — synthesis and critique, not shortened
READMEs and not guesses. Content pages are **bilingual** (`name.md` +
`name.zh.md`). See `AGENTS.md`.


## Public-sources-only rule

This repo is public. Do **not** ingest, copy, or summarize material from
private XingAI repositories. Prefer absolute GitHub links over local sibling
paths. Confirm visibility with `gh` before any new ingest.

## Layout

```
raw/
  courses/                         foundation track 00–09 (folder READMEs)
  xingai-enterprise-ai-design/     articles, guides, assessments, deep-enterprise-ai index
  pocs/                            all public POCs + docs/adr 001–009
  xingai-engineering-system/       selected patterns + ADR-002
  xingai-tech-blog/posts/          selected architecture posts
  _llm-wiki-pattern.md
wiki/                              LLM-written catalog (see wiki/index.md)
AGENTS.md                          schema for ingest / query / lint
```

## How to use this

Open `wiki/index.md` first. Point any LLM agent at this repo with `AGENTS.md`
as the schema.

**Cursor skills (global):**

- `xingai-ai-learning-wiki` — scan/sync public `xingaiapp` GitHub repos
- `xingai-wiki-ingest` — ingest **URL / image / pasted context / local file**
  into `raw/external/` then update `wiki/` (synthesis, not copy-paste)

Trigger with those names or `/xingai-ai-learning-wiki` / `/xingai-wiki-ingest`.

## Status

Trial / v0. Full public-repo sync last run **2026-07-16**. Wiki content pages
are bilingual (`wiki/**/*.md` + `*.zh.md`, 31/31 pairs) as of the same day.
Skipped: `xingai-ai-learning-wiki` (self), `xingai-dot-app` (P2 marketing).
Deep enterprise course bodies not fully snapshotted yet (README index only).

## Disclaimer

Educational / informational only. See [DISCLAIMER.md](DISCLAIMER.md). Wiki
pages may be wrong; raw snapshots may be stale. XingAI gives no warranty.
