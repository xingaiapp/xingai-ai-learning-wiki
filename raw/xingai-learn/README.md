# Learn AI (XingAI)

**Master Patterns. Not Questions.**

> Stop Solving Questions. Learn The Pattern Behind Them.

AI Interview Decision System — not a LeetCode clone.

**Domain:** [learn.xingai.app](https://learn.xingai.app)  
**Repository:** [xingaiapp/xingai-learn](https://github.com/xingaiapp/xingai-learn)

**UI languages:** English · 中文 · 한국어 (switcher in the top bar / drawer). Analyze returns localized intent/solution text; cache keys include locale so EN and 中文 analyses stay separate.

**SEO / AEO:** `metadataBase`, per-route metadata, Open Graph image, `robots.ts`, `sitemap.xml`, `public/llms.txt`, homepage FAQ + `FAQPage` / `SoftwareApplication` JSON-LD, and `/legal/privacy|terms|disclaimer`.

**Token budget:** cache-first always (OCR → analysis fingerprint → title reuse → sessionStorage). LLM only on cold miss. Leave `OPENAI_API_KEY` empty or set `FORCE_MOCK_LLM=true` to spend $0. Seed prewarms common demos. See [ADR-007](docs/adr/007-cache-first-token-budget.md).

## Philosophy

Decision > Information

Learn AI answers: **"What should I practice next?"**

## Relationship To XingAI Engineering Courses

Learn AI is the **learner-facing coding interview decision product**. It analyzes an interview question, identifies the underlying pattern, records weaknesses, and recommends the next pattern to practice.

The separate [`xingai-enterprise-ai-design`](https://github.com/xingaiapp/xingai-enterprise-ai-design) repository owns the **educational curriculum for AI engineers, architects, and CTOs** (not a second Learn AI):

- [`courses/`](https://github.com/xingaiapp/xingai-enterprise-ai-design/tree/main/courses) — beginner-to-CTO **AI engineering** foundation and **AI-role hiring-loop** readiness (system design, tools, RAG, governance)—not DSA pattern drills.
- [`deep-enterprise-ai/`](https://github.com/xingaiapp/xingai-enterprise-ai-design/tree/main/deep-enterprise-ai) — advanced RAG, agent harness, loop, multi-agent, MCP, identity, security, observability, audit, evaluation, operations, and CTO architecture labs.
- [`enterprise-poc/`](https://github.com/xingaiapp/xingai-enterprise-ai-design/tree/main/enterprise-poc) — production-shaped **teaching** reference implementation (not a production service).

These surfaces are complementary but intentionally separate. Learn AI may deep-link to a relevant curriculum lesson in the future, but it must not copy the curriculum into its runtime database, replace its pattern-practice flow with a course catalog, or present the enterprise POC as a production service. See [ADR-001](docs/adr/001-product-boundary.md).

## Architecture

```
Frontend (Next.js) → FastAPI → Engines → SQLite
```

| Layer | Tech |
|---|---|
| Frontend | Next.js 15, TypeScript, Tailwind CSS |
| Backend | FastAPI, Python 3.9+ |
| Database | SQLite (source of truth + cache tables) |
| LLM | OpenAI (Gemini/Anthropic ready) |

## Quick Start

```bash
# Backend
cd apps/api
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
python -m app.seed
uvicorn app.main:app --reload --port 8002

# Optional: refresh real metadata after editing data/pattern_catalog.v1.json
cd ../..
apps/api/.venv/bin/python scripts/import_patterns.py

# Frontend (new terminal, repo root)
npm install
cp .env.example .env.local
npm run dev
```

Open **http://localhost:3002**

## Deploy (Vercel frontend)

Next.js lives at the **repo root**. Vercel Root Directory should be blank (or `.`). Full checklist: [`VERCEL.md`](./VERCEL.md).

## MVP Features

- Question Classification Engine
- Interview Intent Engine
- Prerequisite Knowledge Engine
- Pattern Engine + Knowledge Graph
- Solution Engine (explain before code)
- Replay Engine
- Similar Question Cache
- Learning History
- Mistake Engine
- Recommendation Engine
- Company Mode (Google, Meta, Amazon, etc.)
- Interview Readiness Score

## Ports

| Service | Port |
|---|---|
| Web | 3002 |
| API | 8002 |

## Environment

See `apps/api/.env.example` and root `.env.example`.

## ADRs

- [ADR-001: Product Boundary — Learn AI vs. Research AI vs. SAT AI](docs/adr/001-product-boundary.md)
- [ADR-002: One LLM Call, Many Engines — Cache-First in the Request Path](docs/adr/002-single-call-engines.md)
- [ADR-003: Decision Ledger Adoption](docs/adr/003-decision-ledger.md)
- [ADR-004: Cache-Always Strategy for Real Learning Data](docs/adr/004-cache-always-real-data.md)
- [ADR-005: Development-only LLM Fallback](docs/adr/005-development-llm-fallback.md)
- [ADR-006: SQLite Runtime Schema Guard Before Alembic](docs/adr/006-sqlite-runtime-schema-guard.md)

## Real Data Strategy

Learn AI uses **cache-always** for real pattern, question, and company data. External datasets must be imported offline into SQLite/cache tables first; runtime routes read local cache only. No dashboard, readiness, company, or pattern graph request should fetch external websites or invent missing weights at request time.

Current local catalog:

- `data/pattern_catalog.v1.json` stores metadata only: family, pattern slug, question title, difficulty, tags, source URL, and license note (**187 patterns** across interview families).
- `scripts/import_patterns.py` imports that catalog into SQLite and prunes orphan patterns from older seeds.
- `scripts/refresh_catalog.py` is the offline refresh job wrapper for scheduled local/CI refresh.

## Enterprise Operations

- [Decision Ledger operations](docs/enterprise/learning-decision-ledger-operations.md) · [中文](docs/enterprise/learning-decision-ledger-operations.zh.md)
- [Real-data cache operations](docs/enterprise/real-data-cache-operations.md) · [中文](docs/enterprise/real-data-cache-operations.zh.md)

## Version

0.3.19 — Boundary polish: absolute curriculum links; hiring-loop vs coding-pattern wording; llms FAQ
0.3.18 — Clarify Learn AI vs enterprise-ai-design curriculum boundary; link ledger/cache ops docs
0.3.17 — History: remove one item + clear all
0.3.16 — Fix Analyze stuck on Loading; History CTA + row Analyze buttons
0.3.15 — Study Tree: recommended study path (trunk order, next CTA, path highlight)
0.3.14 — Move Next.js app to repo root so Vercel detects `next` by default
0.3.13 — Document Vercel Root Directory `apps/web` (superseded by 0.3.14)
0.3.12 — Aggressive cache-first token budget (fingerprints, title reuse, prewarm, session cache)
0.3.11 — Solutions: detailed explanation + step-by-step test/stack execution_trace (cache sol:v2)
0.3.10 — Study Tree map (difficulty lanes Easy/Medium/Hard) in nav — not a problem checklist
0.3.9 — SEO/AEO ready: robots, sitemap, llms.txt, OG, FAQ JSON-LD, legal pages
0.3.8 — Full Chinese UI + Analyze locale (LLM/mock + cache keyed by language)
0.3.7 — Lucide icons for chrome nav, theme/locale, Analyze CTAs, upload/camera
0.3.6 — Mobile-first chrome (top bar + drawer + bottom tabs), light/dark, en/zh/ko nav
0.3.5 — Analyze: interviewer intent card (summary + why signals + not-testing)
0.3.4 — Today shows latest Decision Ledger next-step with Practice → Analyze
0.3.3 — Company Mode hydrate + company detail (high-weight patterns → Analyze)
0.3.2 — Pattern detail: open graph node → cached examples → Analyze
0.3.1 — Full 187-pattern curated catalog + importer prune for orphan seed rows
0.3.0 — Real metadata catalog + cache-always import flow + Decision Ledger adopted
0.2.0 — MVP with modular engines + mistake tracking

## Engine Architecture

```
Question Text
    ↓
Classification Engine  → category, pattern, difficulty
    ↓
Intent Engine          → what interviewer tests
    ↓
Prerequisite Engine  → required knowledge
    ↓
Pattern Engine         → pattern → family
    ↓
Solution + Replay      → explain before code
    ↓
Similar Question Cache → SQLite cache (5 from 20)
    ↓
Recommendation Engine  → next best question (company-aware)
    ↓
Decision Engine        → orchestrates full pipeline
```
