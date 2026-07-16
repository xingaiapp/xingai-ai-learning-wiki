# Overview

Start here. This wiki compounds public XingAI AI-engineering learning material:
the foundation curriculum and design docs in
[xingai-enterprise-ai-design](products/xingai-enterprise-ai-design.md),
the runnable (and design-only) POCs in
[xingai-enterprise-ai-pocs](https://github.com/xingaiapp/xingai-enterprise-ai-pocs),
reusable patterns from
[xingai-engineering-system](products/xingai-engineering-system.md),
and selected posts from
[xingai-tech-blog](products/xingai-tech-blog.md).

Private product repos stay out. Full catalog: [index.md](index.md).

## The curriculum, in one line each

00 [Foundations](courses/00-ai-foundations.md) → 01 [LLM App Engineering](courses/01-llm-application-engineering.md) → (02 [RAG](courses/02-rag-knowledge-systems.md) / 03 [Tool Use & Agents](courses/03-tool-use-ai-agents.md)) → 04 [MCP](courses/04-mcp-interoperability.md) → 05 [Agent Runtime & Multi-Agent](courses/05-agent-runtime-multi-agent.md) → 06 [Production AI Engineering](courses/06-production-ai-engineering.md) → 07 [Enterprise Decision Systems](courses/07-enterprise-decision-systems.md) → 08 [AI Leadership & CTO](courses/08-ai-leadership-cto.md) → 09 [AI Interview Mastery](courses/09-ai-interview-mastery.md).

Advanced continuation (index snapshotted, bodies not fully ingested yet): [deep-enterprise-ai](https://github.com/xingaiapp/xingai-enterprise-ai-design/tree/main/deep-enterprise-ai).

## Ideas that hold the whole thing together

1. **[5W+How](concepts/5w-how-framework.md)** — how every course is structured.
2. **[Decision Ledger](concepts/decision-ledger-pattern.md)** — Course 07 + claims POC + engineering-system schema.
3. **[Cache / fallback](concepts/cache-first-llm-architecture.md)** — bound cost; never one LLM as the only path.
4. **[Agent governance and MCP](concepts/agent-governance-and-mcp.md)** — two walls (scope vs policy); oauth POC vs coverage POC.
5. **[Loop engineering](concepts/loop-engineering.md)** — explicit state and stop conditions across articles, patterns, and POCs.

## What this wiki adds

`raw/` is the snapshot. `wiki/` must answer questions a single README cannot:

- Auth-vs-coverage vs workflow — [Claims POC family](syntheses/claims-poc-family-tradeoffs.md)
- Where Course 04's confused-deputy list becomes oauth wall #1/#2 *and* partner-api's "auth deferred"
- Where Course 05's checkpointing caveat matches workflow-v2's fresh-graph-per-call choice
- Pattern-pack names (`decision-ledger-schema`) vs POC field names (`DecisionLedger`, SQLite traces)

If a page is just a shortened README or a file list, it fails the synthesis bar in `AGENTS.md` — rewrite it.

## Log

See [log.md](log.md).
