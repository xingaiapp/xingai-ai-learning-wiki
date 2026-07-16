# Overview

Start here. This wiki covers two things reviewed on 2026-07-16: a 10-course AI-engineering curriculum (`courses/`, listed below) and a live coding-interview-practice product ([`xingai-learn`](products/xingai-learn.md)). They are adjacent, not duplicate — see [the boundary synthesis](syntheses/courses-vs-xingai-learn-boundary.md) if that's what brought you here.

## The curriculum, in one line each

00 [Foundations](courses/00-ai-foundations.md) → 01 [LLM App Engineering](courses/01-llm-application-engineering.md) → (02 [RAG](courses/02-rag-knowledge-systems.md) / 03 [Tool Use & Agents](courses/03-tool-use-ai-agents.md)) → 04 [MCP](courses/04-mcp-interoperability.md) → 05 [Agent Runtime & Multi-Agent](courses/05-agent-runtime-multi-agent.md) → 06 [Production AI Engineering](courses/06-production-ai-engineering.md) → 07 [Enterprise Decision Systems](courses/07-enterprise-decision-systems.md) → 08 [AI Leadership & CTO](courses/08-ai-leadership-cto.md) → 09 [AI Interview Mastery](courses/09-ai-interview-mastery.md) (cuts across all of them). Full list with one-line summaries: [index.md](index.md#courses-wikicourses).

## The four ideas that hold the whole thing together

1. **[5W+How framework](concepts/5w-how-framework.md)** — how every course is structured, and the same framework this session used to write a standalone design article.
2. **[Decision Ledger pattern](concepts/decision-ledger-pattern.md)** — Course 07's core teaching, and the single most-repeated architectural idea across every product this session touched (xingai-learn, claims-workflow-v2-poc, xingai-agent-firewall, xingai-invest-ai).
3. **[Cache-first LLM architecture](concepts/cache-first-llm-architecture.md)** — how to put an LLM in the request path without paying for it on every request; xingai-learn's ADR-002 is the sharpest real instance.
4. **[Agent governance and MCP](concepts/agent-governance-and-mcp.md)** — the runtime-vs-pre-production split that Courses 03-05 teach and that this session's Opportunity Radar pick (Agent Skill Assurance & Evaluation) was chosen specifically to close.

## What this wiki actually adds beyond the raw sources

Not a copy of well-organized material — the raw courses are already good. The value here is what a single read-through of either repo alone wouldn't surface:

- Where the same pattern (Decision Ledger, cache-first, two-wall governance) shows up in multiple products under different names.
- [One real error found and fixed](syntheses/review-findings-2026-07-16.md) in `xingai-learn`'s ADR-001 — including the fact that the *first* attempted fix was itself wrong, and why.
- The direct, non-obvious connection between this wiki's own domain and the same-day Opportunity Radar Decision Card (Course 08's portfolio judgment, made for real).

## Log

See [log.md](log.md) for the full ingest/query/lint timeline.
