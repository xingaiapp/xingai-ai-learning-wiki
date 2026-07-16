# Overview

Start here. This wiki covers the public 10-course AI-engineering curriculum
(`courses/` from
[xingai-enterprise-ai-design](https://github.com/xingaiapp/xingai-enterprise-ai-design))
and the public
[claims-workflow-v2-poc](products/claims-workflow-v2-poc.md)
that the courses keep using as a runnable example.

## The curriculum, in one line each

00 [Foundations](courses/00-ai-foundations.md) → 01 [LLM App Engineering](courses/01-llm-application-engineering.md) → (02 [RAG](courses/02-rag-knowledge-systems.md) / 03 [Tool Use & Agents](courses/03-tool-use-ai-agents.md)) → 04 [MCP](courses/04-mcp-interoperability.md) → 05 [Agent Runtime & Multi-Agent](courses/05-agent-runtime-multi-agent.md) → 06 [Production AI Engineering](courses/06-production-ai-engineering.md) → 07 [Enterprise Decision Systems](courses/07-enterprise-decision-systems.md) → 08 [AI Leadership & CTO](courses/08-ai-leadership-cto.md) → 09 [AI Interview Mastery](courses/09-ai-interview-mastery.md) (cuts across all of them). Full list: [index.md](index.md#courses-wikicourses).

## The ideas that hold the whole thing together

1. **[5W+How framework](concepts/5w-how-framework.md)** — how every course is structured.
2. **[Decision Ledger pattern](concepts/decision-ledger-pattern.md)** — Course 07's core teaching; the claims POC implements a ledger-shaped audit trail.
3. **[Cache / fallback discipline](concepts/cache-first-llm-architecture.md)** — bound LLM cost and never let one model call be a single point of failure.
4. **[Agent governance and MCP](concepts/agent-governance-and-mcp.md)** — OAuth scope vs independent business-rule policy (two walls).

## What this wiki adds beyond the raw sources

Not a copy of already-good course READMEs. The value is cross-linking:

- Where the same pattern shows up in Course 07 teaching *and* the claims POC.
- [What the 2026-07-16 courses review actually checked](syntheses/review-findings-2026-07-16.md).

Private product repos are intentionally out of scope — see README / AGENTS.md.

## Log

See [log.md](log.md) for the ingest/query/lint timeline.
