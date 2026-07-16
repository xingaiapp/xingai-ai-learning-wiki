# AGENTS.md — Wiki Schema and Conventions

This file tells any LLM agent working in this repo how the wiki is structured
and what workflows to follow. Read this before ingesting a source, answering
a query, or running a lint pass. Pattern source: Andrej Karpathy's
["LLM Wiki"](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
gist — see `raw/_llm-wiki-pattern.md` for the original.

## What this wiki is about

Domain: XingAI's AI-engineering learning content and the products that
demonstrate it in practice. Seeded 2026-07-16 from a review of two things,
then expanded the same day to four:

1. **`courses/`** — a 10-course bilingual curriculum (`xingai-enterprise-ai-design/courses/`) teaching AI engineering from foundations to CTO-level leadership.
2. **`xingai-learn`** — a live product (learn.xingai.app) that helps engineers practice coding-interview patterns via an LLM analysis pipeline.
3. **`claims-workflow-v2-poc`** — a multi-agent insurance-claims POC; the most cross-referenced entity in this wiki, since nearly every course concept shows up in it somewhere.
4. **`xingai-agent-firewall`** — runtime agent tool-call governance (policy → risk → approval → ledger).
5. **`xingai-opportunity-radar`** — the issue → Decision Card → Content Pack pipeline that, this session, picked an upgrade to #4.

The wiki exists to answer questions a single grep across separate repos
can't answer well: how the courses' pedagogy shows up in real running code,
which patterns (Decision Ledger, cache-first LLM calls, two-wall governance)
repeat across products under different names, where things diverge, and
what's been found wrong and fixed over time. Scope grows by ingest, not by
rewriting this list every time — check `wiki/index.md` for what's actually
in, this section is a snapshot of intent, not a hard boundary.

## Layers

- **`raw/`** — immutable snapshot of source documents, copied in on
  2026-07-16. These are NOT the living originals — the originals are
  `xingai-enterprise-ai-design/courses/` and `xingai-learn/` in the parent
  workspace. If the source repos change, re-ingest (see Ingest below) rather
  than hand-editing `raw/`.
- **`wiki/`** — everything in here is LLM-written and LLM-maintained. Humans
  read; the agent writes. Structure:
  - `wiki/index.md` — content catalog, organized by category. Read this
    first when answering a query.
  - `wiki/log.md` — append-only chronological record of ingests/queries/lints.
  - `wiki/overview.md` — top-level synthesis, the "start here" page.
  - `wiki/courses/*.md` — one entity page per course (00-09). Each is a
    *summary with cross-references*, not a copy of the raw README — the raw
    file is already well-structured; the wiki's value-add is synthesis and
    links, not duplication.
  - `wiki/products/*.md` — one entity page per product (currently just
    `xingai-learn.md`).
  - `wiki/concepts/*.md` — cross-cutting patterns that appear in more than
    one course or product (e.g. the 5W+How framework, the Decision Ledger
    pattern, cache-first LLM architecture).
  - `wiki/syntheses/*.md` — answers to specific questions that are valuable
    enough to keep, not just chat output (per the "file answers back into
    the wiki" operation below).

## Operations

### Ingest

When a new raw source is added (a new course, a new ADR, a new product):

1. Copy the source file into `raw/` at a path mirroring its origin repo.
2. Read it fully.
3. Update or create the relevant `wiki/courses/`, `wiki/products/`, or
   `wiki/concepts/` page(s). A single source can touch several pages —
   don't just create one page and stop; check whether it changes any
   existing concept or synthesis page too.
4. Update `wiki/index.md`.
5. Append one entry to `wiki/log.md` using the format below.

### Query

When asked a question:

1. Read `wiki/index.md` first to find candidate pages.
2. Read the specific pages, not the raw sources, unless the wiki page
   itself says a claim needs re-verification against raw.
3. Answer with citations to wiki pages (and raw sources where the wiki
   page cites them).
4. If the answer is substantial and durable (not a one-off), offer to file
   it into `wiki/syntheses/` as a new page instead of letting it live only
   in chat.

### Lint

Periodically (or when asked to "review" or "lint" the wiki):

1. Check for contradictions between pages.
2. Check for claims a newer raw source has superseded.
3. Check for orphan pages (no inbound links from `index.md` or another page).
4. Check for concepts mentioned in 2+ pages that don't yet have their own
   `wiki/concepts/` page.
5. Record findings as a `lint` entry in `log.md`; file anything substantial
   as a `wiki/syntheses/` page (see `review-findings-2026-07-16.md` for the
   precedent — that's the audit trail from the review that seeded this wiki).

## Log format

Each `log.md` entry starts with a consistent prefix so it stays parseable:

```
## [YYYY-MM-DD] ingest | <source title>
## [YYYY-MM-DD] query | <question>
## [YYYY-MM-DD] lint | <what was checked>
```

`grep "^## \[" wiki/log.md | tail -5` gives the last 5 entries.

## Conventions

- Wiki pages are English-only at this stage (the source repos are already
  bilingual; the wiki adds synthesis on top, not a third translation layer).
  If bilingual wiki pages become valuable later, mirror the source repos'
  `.md` / `.zh.md` convention.
- Every wiki page ends with a `## Sources` section linking back to the
  specific `raw/` file(s) or, for pages that draw on chat analysis rather
  than a single file, a note saying so.
- Every factual claim about "what the code/data actually does" (not just
  "what the docs say") should be marked as verified or not — this wiki was
  seeded from a review that found and fixed one real stale cross-reference
  by checking actual data, not just trusting prose. Don't regress on that.
- Scale note: at ~20 raw sources / ~25 wiki pages, `index.md` is sufficient
  navigation — no embedding-based search needed yet. Revisit if this wiki
  grows past roughly 100 sources (per the pattern doc's own guidance).
