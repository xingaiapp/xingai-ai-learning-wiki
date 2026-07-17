# AI Architecture Digest 2026-07-17 vs XingAI

Chinese: [ai-architecture-digest-2026-07-17.zh.md](ai-architecture-digest-2026-07-17.zh.md)

User-curated weekly digest (`raw/external/2026-07-17-ai-architecture-digest/`). This page is **not** a reprint. It maps the digest’s four shifts and ten items onto public XingAI courses/POCs, and flags what still lacks evidence.

**No UX PNG** (architecture reading list; no product chrome).

## Digest thesis (four shifts)

As stated in the paste (`content.md`):

```text
Agent: add-count → task-conditioned architecture choice
MCP: short tools → stateless + long-running tasks
RAG: one-shot Top-K → plan / re-retrieve / evidence sufficiency
.NET/Azure: agent demos → Durable Workflow + unified traces
```

Closing line from the digest (keep as claim of the *author*, not a verified law of nature): *Agent reasoning can be probabilistic; execution, authorization, and workflow state must stay deterministic and recoverable.*

## Map to XingAI public curriculum

| Digest shift | Closest public anchors |
|---|---|
| Architecture Router before multi-agent | [Course 05](../courses/05-agent-runtime-multi-agent.md), [loop-engineering](../concepts/loop-engineering.md), [multi-agent-lab](../products/multi-agent-lab.md) |
| Strategy / experience memory (ReasoningBank-shaped) | [decision-ledger-pattern](../concepts/decision-ledger-pattern.md) — ledger stores *decisions/outcomes*, not only chat turns |
| Untrusted observations / agent traps | [agent-governance-and-mcp](../concepts/agent-governance-and-mcp.md), [Course 04](../courses/04-mcp-interoperability.md) failure modes |
| Long-running MCP + durable runtime | Course 04 + [claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.md) (auth walls); durable patterns in deep-enterprise track |
| Agentic RAG evidence loop | [Course 02](../courses/02-rag-knowledge-systems.md), [rag-vs-agentic-rag-vs-xingai](rag-vs-agentic-rag-vs-xingai.md) |
| Identity / discovery control plane | [Course 10](../courses/10-oauth-oidc-azure-identity.md), [oauth-oidc-azure-identity](../concepts/oauth-oidc-azure-identity/00-overview.md) |

## Item checklist (sources spot-checked 2026-07-17)

| # | Topic | Primary URL | HTTP |
|---|---|---|---|
| 1 | Scaling agent systems (Google Research blog) | https://research.google/blog/towards-a-science-of-scaling-agent-systems-when-and-why-agent-systems-work/ | 200 |
| 2 | ReasoningBank (Google Research blog) | https://research.google/blog/reasoningbank-enabling-agents-to-learn-from-experience/ | 200 |
| 3 | AI Agent Traps (SSRN) | https://papers.ssrn.com/sol3/papers.cfm?abstract_id=6372438 | **403** |
| 4 | C# MCP SDK releases | https://github.com/modelcontextprotocol/csharp-sdk/releases | 200 |
| 5 | Long-running MCP tools on Azure Functions | https://devblogs.microsoft.com/azure-sdk/long-running-mcp-tools-azure-functions/ | 200 |
| 6 | Azure Functions MCP / Foundry Toolbox | https://devblogs.microsoft.com/azure-sdk/functions-mcp-updates-build-2026/ | 200 |
| 7 | Google Agentic RAG blog | https://research.google/blog/unlocking-dependable-responses-with-gemini-enterprise-agent-platforms-agentic-rag/ | 200 |
| 8 | Azure AI Search Knowledge Base (agentic retrieval) | https://learn.microsoft.com/en-us/azure/search/agentic-retrieval-how-to-create-knowledge-base | 200 |
| 9 | Insurance STUW Agentic RAG (arXiv) | https://arxiv.org/abs/2607.07858 | 200 |
| 10 | .NET / Agent Framework durable direction | https://devblogs.microsoft.com/dotnet/category/ai/ | 200 |
| + | Foundry hosted agents / traces | https://devblogs.microsoft.com/foundry/agent-service-build2026/ | 200 |

Priority order in the digest for immediate POC work: **(5) long-running MCP on Functions**, **(10) Durable Agent Workflow**, then SDK preview / Agentic RAG / Azure AI Search.

## Three action items (digest) vs public XingAI stance

1. **Claims MCP must not own the whole business transaction on `tools/call` HTTP.** Digest: return Operation ID → Durable Orchestration. Public wiki already separates OAuth wall from business policy ([claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.md)); durable orchestration is the *execution* twin of that auth split.
2. **Research / RAG needs an evidence loop with stop conditions.** Aligns with Course 02 and the [rag-vs-agentic-rag](rag-vs-agentic-rag-vs-xingai.md) critique of one-shot Top-K.
3. **Separate probabilistic Agent from deterministic Durable Workflow; MCP discovers/calls tools; Entra/APIM own identity edges.** Matches Course 10 + Course 04 teaching: capability ≠ permission ≠ durable state.

## Known

- Digest package snapshotted under `raw/external/2026-07-17-ai-architecture-digest/` (`SOURCE.md`, `content.md`, `notes.md`).
- Nine of eleven cited landing URLs returned HTTP 200 from this environment on 2026-07-17; SSRN #3 returned 403.
- Four-shift thesis and three action items appear in the user paste (`content.md`); they are **digest claims**, not re-proven experiments in this wiki pass.
- XingAI public courses already teach: don’t default multi-agent (05), two-wall MCP auth (04/10), RAG as governed pipeline (02), durable/production concerns (05/06).

## Missing

- Side-by-side Architecture Router table (task features → Single/Parallel/Supervisor/Hybrid) implemented in a **public** XingAI POC.
- Runnable “long-running MCP tool → Durable Functions → Operation ID” sample in `xingai-enterprise-ai-pocs` (digest urges it; wiki has not verified such a sample this session).
- ReasoningBank-shaped *strategy* schema in public Decision Ledger docs (ledger exists; “strategy lesson” object may not).
- Full text of AI Agent Traps (SSRN 403 here).
- Cost / eval budgets for Agentic RAG loops in XingAI Research AI public docs.

## Rethink

- “MCP going fully stateless” in C# SDK 2.0 Preview is a **migration watch**, not a production mandate — digest itself says wait for stable.
- Azure AI Search Knowledge Base reduces *boilerplate* orchestration; it does **not** replace ACL filtering, freshness, or eval gates (Course 02 still owns those).
- Insurance arXiv uses synthetic STUW settings — useful blueprint, not production proof for Claims.
- Naming every product memory “ReasoningBank” without success/failure *conditions* collapses back to chat logs.

## Debate

- Architecture Router inside the Orchestrator vs a separate control-plane service.
- MCP Tasks / durable handles vs always-sync tools with stricter SLOs.
- Store reusable strategies in Decision Ledger vs a dedicated experience store.
- Foundry Toolbox discovery vs self-hosted MCP control plane for non-Azure XingAI demos.

## Needs evidence

- Which public XingAI POC (if any) already returns async operation IDs from MCP tools.
- Whether Course 05 / multi-agent-lab encodes task-feature routing or still hard-codes topologies.
- Confirm AI Agent Traps PDF/HTML content once SSRN (or a mirror) is readable.
- Whether Azure AI Search `2026-04-01` Knowledge Base API is what any XingAI public demo actually calls.

## Sources

- Raw: `raw/external/2026-07-17-ai-architecture-digest/`
- Primary URLs in the table above (no `utm_source` tracking params)
- Related wiki: [agent-governance-and-mcp](../concepts/agent-governance-and-mcp.md), [Course 04](../courses/04-mcp-interoperability.md), [Course 10](../courses/10-oauth-oidc-azure-identity.md), [rag-vs-agentic-rag-vs-xingai](rag-vs-agentic-rag-vs-xingai.md)
