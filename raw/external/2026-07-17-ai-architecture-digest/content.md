# AI Architecture Digest｜2026-07-17

User-pasted digest (XingAI wiki ingest). Primary URLs cited below without tracking params.

## Four architecture shifts (digest thesis)

1. Agents: from "add more agents" → task-conditioned architecture selection
2. MCP: from short request tools → stateless, extensible, long-running tasks
3. RAG: from one-shot vector retrieve → plan / decompose / re-retrieve / evidence judgment
4. .NET/Azure: from Agent demos → Durable Workflow, unified traces, production governance

## Ten items (as listed in paste)

1. Google — Towards a Science of Scaling Agent Systems (2026-01-28)
   https://research.google/blog/towards-a-science-of-scaling-agent-systems-when-and-why-agent-systems-work/
2. Google ReasoningBank (2026-04-21)
   https://research.google/blog/reasoningbank-enabling-agents-to-learn-from-experience/
3. AI Agent Traps (SSRN, 2026-03-08) — abstract fetch 403 from ingest env
   https://papers.ssrn.com/sol3/papers.cfm?abstract_id=6372438
4. C# MCP SDK 2.0 Preview — releases page (2026-07-14 cited)
   https://github.com/modelcontextprotocol/csharp-sdk/releases
5. Long-running MCP tools on Azure Functions (2026-07-16)
   https://devblogs.microsoft.com/azure-sdk/long-running-mcp-tools-azure-functions/
6. Azure Functions MCP / Foundry Toolbox (2026-06-24 cited)
   https://devblogs.microsoft.com/azure-sdk/functions-mcp-updates-build-2026/
7. Google Agentic RAG (2026-06-05)
   https://research.google/blog/unlocking-dependable-responses-with-gemini-enterprise-agent-platforms-agentic-rag/
8. Azure AI Search Agentic Retrieval / Knowledge Base
   https://learn.microsoft.com/en-us/azure/search/agentic-retrieval-how-to-create-knowledge-base
9. Agentic RAG for insurance STUW (arXiv 2607.07858, 2026-07-08)
   https://arxiv.org/abs/2607.07858
10. Microsoft Agent Framework Durable Workflows (.NET Blog AI category cited)
    https://devblogs.microsoft.com/dotnet/category/ai/
11. Supplement: Foundry Hosted Agents / OTel
    https://devblogs.microsoft.com/foundry/agent-service-build2026/

## Digest action items (user)

1. Claims MCP: do not run long transactions inside the HTTP tool call — Durable Orchestration + Operation ID
2. Research Agent: Evidence Loop with stop by confidence/budget
3. Separate Agent (probabilistic) from Durable Workflow (deterministic) and MCP / APIM-Entra walls

## Closing line (user)

Agent can be probabilistic; business execution, authorization, and workflow state must stay deterministic and recoverable.
