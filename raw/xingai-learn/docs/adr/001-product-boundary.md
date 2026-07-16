# ADR-001: Product Boundary — Learn AI vs. Research AI vs. SAT AI vs. Enterprise Curriculum

**Date:** 2026-07-05
**Status:** Accepted
**Author:** Xing @ XingAI
**Also available:** [中文](001-product-boundary.zh.md)

## Context

XingAI has three learning-adjacent products plus one engineer-education repository, and without a recorded boundary they will drift into each other:

- **Learn AI** (this repo, live at learn.xingai.app) — takes an *interview question* (text or screenshot), classifies it into a pattern/family knowledge graph, and answers "**what should I practice next?**" User: engineer preparing for coding interviews.
- **Research AI** (`xingai-research-ai`) — takes a *technology topic*, produces a learning path and study plan. User: someone learning a technology.
- **SAT AI / SAT Memory Coach** (no repo yet; tracked as MVP-stage in the founder pipeline) — takes *SAT mistake uploads*, builds a per-student memory graph of weak knowledge points, generates daily drills and parent reports. User: high-school student + parent.
- **XingAI Enterprise AI Design** (`xingai-enterprise-ai-design`) — publishes a bilingual beginner-to-CTO AI engineering curriculum, deep enterprise labs, and a production-shaped reference POC. User: AI engineer, architect, engineering leader, or CTO. It is educational source material, not another consumer learning product.

The overlap is real: the **three consumer learning products** (Learn AI, Research AI, SAT AI) all track mistakes, model weaknesses, and recommend the next item. The temptation to merge them — or to fold the enterprise curriculum into Learn AI as a course catalog — is exactly the feature creep this ADR exists to block. Separately: enterprise curriculum “interview” means **AI engineering / architecture hiring loops**; Learn AI “interview” means **coding / DSA pattern practice**.

## Decision

**Three separate products plus one separate education repository; no shared runtime or database.** What the products share is *patterns, not libraries*: mistake tracking, mastery modeling, cache-first analysis, and (planned) the Decision Ledger schema — each product implements them against its own domain model. The enterprise curriculum may explain those patterns and link to public product architecture, but it does not become a Learn AI runtime dependency.

The boundary test is the input and the decision delivered:

| Product | Input | Decision delivered | Payer |
|---|---|---|---|
| Learn AI | one interview question | next pattern to practice | the engineer |
| Research AI | a topic | learning path / study plan | the learner |
| SAT AI | mistake uploads over time | today's 10 personalized drills | the parent |
| Enterprise AI curriculum | an engineering competency or architecture problem | lesson, lab, assessment, and reference implementation | engineer / employer / technical leader |

SAT AI specifically is **not** a Learn AI mode: different learner (minor, parent-supervised), different content domain (standardized test, not engineering patterns), different business model (family subscription), and legal/privacy posture (children's data) that must not leak into this codebase.

## Consequences

Positive:
- Learn AI stays sharp: interview patterns only, engineer-facing, no parent dashboards or school-domain compliance in this repo.
- The enterprise curriculum stays deep: it can teach RAG, agents, MCP, security, operations, and CTO strategy without turning Learn AI into a broad learning management system.
- SAT AI can start from a clean scaffold and copy *decisions* (this ADR set) rather than code, per `xingai-engineering-system/patterns/product-upgrade-rule.md`.

Tradeoffs:
- Mistake/mastery modeling will be implemented at least twice (here: `MistakeRecord`, `PatternMastery` in `apps/api/app/models.py`; SAT AI will build its own). Accepted — the domain semantics differ more than the table shapes suggest.
- Cross-product surfaces ("your interview readiness and your kid's SAT progress in one view") require API integration later, not a shared database now.
- Learn AI may eventually expose a curated "Learn the architecture" link, but course progress, labs, and POC execution remain owned by `xingai-enterprise-ai-design` unless a separate integration ADR is accepted.

## Related

- [ADR-002: One LLM Call, Many Engines](./002-single-call-engines.md)
- [ADR-003: Decision Ledger Adoption](./003-decision-ledger.md)
- [xingai-research-startup-agent](https://github.com/xingaiapp/xingai-research-startup-agent) ADR-001 — the same boundary discipline applied to research products. Note: this is a distinct product from `xingai-research-ai` (Learning Decision System, `research.xingai.app`) — see the [Research-to-Startup Agent post](https://github.com/xingaiapp/xingai-tech-blog/blob/main/posts/2026-07-03-research-startup-agent-four-artifact-pipeline.md) for what it does (URL → insight → startup idea → PRD → build prompt). Its repo isn't checked out in this workspace, so its ADR-001 content couldn't be verified in this pass (2026-07-16) — confirm before relying on it.
- `xingai-opportunity-radar/config/portfolio.yaml` (`prefer_upgrade_when`, `do_not_build`) — the same boundary discipline applied portfolio-wide
