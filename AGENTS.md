# AGENTS.md — Wiki Schema and Conventions

Chinese: [AGENTS.zh.md](AGENTS.zh.md)

This file tells any LLM agent working in this repo how the wiki is structured
and what workflows to follow. Read this before ingesting a source, answering
a query, or running a lint pass. Pattern source: Andrej Karpathy's
["LLM Wiki"](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
gist — see `raw/_llm-wiki-pattern.md` for the original.

## What this wiki is about

Domain: **public** XingAI AI-engineering learning content and the public POCs
that demonstrate it. Seeded 2026-07-16 from:

1. **`courses/`** — a 10-course bilingual curriculum in
   [`xingai-enterprise-ai-design`](https://github.com/xingaiapp/xingai-enterprise-ai-design)
   (foundations → CTO-level leadership).
2. **`claims-workflow-v2-poc`** — a multi-agent insurance-claims POC in
   [`xingai-enterprise-ai-pocs`](https://github.com/xingaiapp/xingai-enterprise-ai-pocs);
   the main runnable cross-reference for course concepts.

The wiki exists to answer questions a single grep can't: how course pedagogy
shows up in real public POC code, which patterns (Decision Ledger, MCP
two-wall governance, heuristic/LLM dual-path) recur, and what review passes
found wrong or confirmed. Scope grows by ingest of **public** sources only —
check `wiki/index.md` for what's actually in.

## Public-sources-only (required)

This repository is public. Agents must:

- Ingest only from public XingAI GitHub repos, **other public URLs**, or
  **user-provided** context/images/files explicitly meant for this wiki.
- Never copy, paraphrase, or dump private-repo READMEs, ADRs, PRDs, portfolios,
  Decision Cards, Content Packs, or internal product architecture into `raw/`
  or `wiki/`.
- Prefer absolute `https://github.com/xingaiapp/...` (or other canonical) links
  over workspace-relative sibling paths.
- If a public course *mentions* a private sibling product by name, you may note
  that the course cites it — do not pull that private repo's internals into this wiki.

When unsure whether a source is public, check GitHub visibility (repos) or ask
the user to paste an excerpt (URLs that won't fetch).

### Ad-hoc external sources

Non-repo inputs (URL, image, paste, local file) live under:

```text
raw/external/YYYY-MM-DD-<slug>/
  SOURCE.md     # manifest (types, canonical_url, verified)
  content.md    # fetched or pasted text
  notes.md      # optional image/agent notes
  assets/       # optional
```

Cursor skills: **`xingai-ai-learning-wiki`** (public repo sync) and
**`xingai-wiki-ingest`** (URL / image / context). Both must pass the
**synthesis bar**, **epistemic standard**, and **bilingual (EN+中文)** rule.

## Epistemic standard (required)

This wiki aims to be a **knowledge base**, not a brochure and not a guess log.

Every new or materially updated `wiki/` page must make these explicit (as
headings or clearly labeled blocks):

| Block | Required content |
|---|---|
| **Known** | Only claims grounded in snapshotted `raw/`, a fetched public URL, or a check you actually ran. Cite the path/URL. |
| **Missing** | What the source omits that still matters here (auth, eval, ledger *process*, ops, cost, who approves, failure modes). |
| **Rethink** | Assumptions that look wrong or oversimplified next to other public sources (course vs POC, sibling POCs, pattern vs demo). |
| **Debate** | Open design forks — present both sides; do not “win” the argument without an ADR or verified code. |
| **Needs evidence** | Questions that would change the page. Leave them open. Do **not** answer by speculation. |

**Fail / rewrite before commit if:**

- the page mostly repeats what the source already says,
- gaps are filled with plausible-sounding invention,
- image or marketing copy is treated as implementation truth,
- citations point at files you did not read this session.

Confidence language: prefer `verified` / `partial` / `unknown` over “probably.”

Skills carry the same checklist:
`~/.cursor/skills/xingai-wiki-ingest/references/epistemic-checklist.md`.


## Layers

- **`raw/`** — immutable snapshot of public source documents. Layout mirrors
  origin repos (`raw/courses/`, `raw/pocs/`, `raw/xingai-enterprise-ai-design/`,
  etc.). These are NOT the living originals — prefer the public GitHub repos
  for current truth. If sources change, re-ingest rather than hand-editing `raw/`.
- **`wiki/`** — everything in here is LLM-written and LLM-maintained. Humans
  read; the agent writes. Structure:
  - `wiki/index.md` — content catalog. Read this first when answering a query.
  - `wiki/log.md` — append-only chronological record of ingests/queries/lints.
  - `wiki/overview.md` — top-level synthesis.
  - `wiki/courses/*.md` — one entity page per course (00-09): summary +
    cross-references, not a copy of the raw README.
  - `wiki/products/*.md` — one entity page per **public** product/POC.
  - `wiki/concepts/*.md` — cross-cutting patterns that appear in more than
    one course or public POC.
  - `wiki/syntheses/*.md` — durable answers filed back into the wiki.

## Operations

### Ingest

When a new **public** raw source is added:

1. Confirm the source repo/URL is public.
2. Copy into `raw/` at a path mirroring its origin repo.
3. Update or create the relevant `wiki/courses/`, `wiki/products/`,
   `wiki/concepts/`, or `wiki/syntheses/` page(s) — **both** `name.md` and
   `name.zh.md` in the same pass.
4. Update `wiki/index.md` **and** `wiki/index.zh.md` if the catalog changed.
5. Append one entry to `wiki/log.md` (English ops log; no `.zh.md` required).

### Query

1. Read `wiki/index.md` first to find candidate pages.
2. Read the specific pages, not the raw sources, unless the wiki page
   itself says a claim needs re-verification against raw.
3. Answer with citations to wiki pages (and raw sources where cited).
4. If the answer is substantial and durable, offer to file it into
   `wiki/syntheses/`.

### Lint

1. Check for contradictions between pages.
2. Check for claims a newer public raw source has superseded.
3. Check for orphan pages.
4. Check for concepts mentioned in 2+ pages that lack a `wiki/concepts/` page.
5. Check that no page reintroduced private-repo internals.
6. **Critique audit:** pages that only describe “what it is” with no Missing /
   Rethink / Debate / Needs evidence → rewrite.
7. **Guess audit:** confident claims without citations → demote or delete.
8. **Bilingual audit:** every content page under `wiki/` (courses, products,
   concepts, syntheses, index, overview) has a matching `.zh.md`; section
   counts match; mutual language links present; no EN-only lag.
9. Record findings as a `lint` entry in `log.md`; file anything substantial
   as a `wiki/syntheses/` page (EN+ZH).

## Log format

```
## [YYYY-MM-DD] ingest | <source title>
## [YYYY-MM-DD] query | <question>
## [YYYY-MM-DD] lint | <what was checked>
```

`grep "^## \[" wiki/log.md | tail -5` gives the last 5 entries.

## Conventions

- **Synthesis bar (required):** `wiki/` pages must add value raw does not.
  Fail if the page is a shortened README, file list, or heading restatement.
  Prefer contrasts, course↔POC maps, and questions one repo grep cannot answer.
  `raw/` is the copy; `wiki/` is the compound.
- **Epistemic standard (required):** Known / Missing / Rethink / Debate /
  Needs evidence — see section above. No guessing as fact.
- **Every wiki content page is bilingual: `name.md` (English) + `name.zh.md`
  (中文)**, same convention as the design/POC repos. Chinese is a full
  localization — same section order (including Known / Missing / Rethink /
  Debate / Needs evidence), same code blocks, same diagram meaning, same
  claims. Internal wiki links point at the `.zh.md` sibling; `raw/` and
  external URLs stay unchanged.
  - English page header: `Chinese: [name.zh.md](name.zh.md)`
  - Chinese page header: `English: [name.md](name.md)`
  - Applies to: `wiki/courses/`, `wiki/products/`, `wiki/concepts/`,
    `wiki/syntheses/`, `wiki/index`, `wiki/overview`, plus root `README` /
    `AGENTS` / `DISCLAIMER` when those change.
  - **Exception:** `wiki/log.md` stays English-only (ops chronology).
  - Write **both languages in the same ingest pass** — never ship EN and
    leave ZH as TODO.
- Every wiki page ends with a `## Sources` section linking back to specific
  `raw/` file(s) or noting analysis over public sources actually read.
- Claims about “what the code does” need verification notes when the POC is
  checkable; otherwise mark Needs evidence.
- Scale note: at this size, `index.md` is enough navigation. Revisit past ~100
  sources (per the pattern doc).
