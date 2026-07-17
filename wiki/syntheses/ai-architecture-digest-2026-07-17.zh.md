# AI 架构周报 2026-07-17 与 XingAI

English: [ai-architecture-digest-2026-07-17.md](ai-architecture-digest-2026-07-17.md)

用户整理的周报（`raw/external/2026-07-17-ai-architecture-digest/`）。本页**不是**原文转载，而是把四条架构转向与十个条目映射到 XingAI 公开课程/POC，并标出仍缺证据之处。

**无 UX PNG**（阅读清单；无产品界面）。

## 周报论点（四条转向）

粘贴稿（`content.md`）归纳为：

```text
Agent：堆数量 → 按任务特征选架构
MCP：短请求工具 → 无状态 + 长任务
RAG：一次 Top-K → 规划 / 再检索 / 证据是否足够
.NET/Azure：Agent Demo → Durable Workflow + 统一追踪
```

周报收束句（视为**作者主张**，本轮未当作自然定律验证）：*Agent 可以概率推理；业务执行、权限与工作流状态必须确定性且可恢复。*

## 映射到 XingAI 公开课程

| 周报转向 | 最近的公开锚点 |
|---|---|
| 多 Agent 前的 Architecture Router | [课程 05](../courses/05-agent-runtime-multi-agent.zh.md)、[loop-engineering](../concepts/loop-engineering.zh.md)、[multi-agent-lab](../products/multi-agent-lab.md) |
| 策略/经验记忆（ReasoningBank 形） | [decision-ledger-pattern](../concepts/decision-ledger-pattern.zh.md)——台账记*决策/结果*，不只聊天回合 |
| 不可信观测 / Agent Traps | [agent-governance-and-mcp](../concepts/agent-governance-and-mcp.zh.md)、[课程 04](../courses/04-mcp-interoperability.zh.md) 故障模式 |
| 长任务 MCP + 持久运行时 | 课程 04 + [claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.md)（鉴权双墙） |
| Agentic RAG 证据环 | [课程 02](../courses/02-rag-knowledge-systems.zh.md)、[rag-vs-agentic-rag-vs-xingai](rag-vs-agentic-rag-vs-xingai.zh.md) |
| 身份 / 发现控制面 | [课程 10](../courses/10-oauth-oidc-azure-identity.zh.md)、[oauth-oidc-azure-identity](../concepts/oauth-oidc-azure-identity/00-overview.zh.md) |

## 条目核对（2026-07-17 抽检）

| # | 主题 | 主 URL | HTTP |
|---|---|---|---|
| 1 | Scaling agent systems（Google Research 博文） | https://research.google/blog/towards-a-science-of-scaling-agent-systems-when-and-why-agent-systems-work/ | 200 |
| 2 | ReasoningBank（Google Research 博文） | https://research.google/blog/reasoningbank-enabling-agents-to-learn-from-experience/ | 200 |
| 3 | AI Agent Traps（SSRN） | https://papers.ssrn.com/sol3/papers.cfm?abstract_id=6372438 | **403** |
| 4 | C# MCP SDK releases | https://github.com/modelcontextprotocol/csharp-sdk/releases | 200 |
| 5 | Azure Functions 长任务 MCP Tool | https://devblogs.microsoft.com/azure-sdk/long-running-mcp-tools-azure-functions/ | 200 |
| 6 | Azure Functions MCP / Foundry Toolbox | https://devblogs.microsoft.com/azure-sdk/functions-mcp-updates-build-2026/ | 200 |
| 7 | Google Agentic RAG 博文 | https://research.google/blog/unlocking-dependable-responses-with-gemini-enterprise-agent-platforms-agentic-rag/ | 200 |
| 8 | Azure AI Search Knowledge Base | https://learn.microsoft.com/en-us/azure/search/agentic-retrieval-how-to-create-knowledge-base | 200 |
| 9 | 保险 STUW Agentic RAG（arXiv） | https://arxiv.org/abs/2607.07858 | 200 |
| 10 | .NET / Agent Framework 持久化方向 | https://devblogs.microsoft.com/dotnet/category/ai/ | 200 |
| + | Foundry Hosted Agents / 追踪 | https://devblogs.microsoft.com/foundry/agent-service-build2026/ | 200 |

周报建议的立即 POC 优先级：**（5）Functions 长任务 MCP**、**（10）Durable Agent Workflow**，再看 SDK Preview / Agentic RAG / Azure AI Search。

## 三条行动（周报）对照公开 XingAI 立场

1. **Claims MCP 不要在 `tools/call` HTTP 内跑完整业务事务。** 周报：返回 Operation ID → Durable Orchestration。公开 wiki 已把 OAuth 墙与业务策略分开（[claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.md)）；持久编排是该鉴权拆分在*执行层*的对应物。
2. **Research / RAG 需要带停止条件的证据环。** 对齐课程 02 与 [rag-vs-agentic-rag](rag-vs-agentic-rag-vs-xingai.zh.md) 对一次 Top-K 的批判。
3. **概率 Agent 与确定性 Durable Workflow 分离；MCP 负责发现/调用；Entra/APIM 守身份边缘。** 对齐课程 10 + 04：能力 ≠ 权限 ≠ 持久状态。

## Known（已知）

- 原料包：`raw/external/2026-07-17-ai-architecture-digest/`（`SOURCE.md`、`content.md`、`notes.md`）。
- 2026-07-17 本环境对 11 个落地页抽检：9/11 为 HTTP 200；SSRN #3 为 403。
- 四条转向与三条行动来自用户粘贴（`content.md`），本轮**未**重做实验证明。
- XingAI 公开课已教：勿默认多 Agent（05）、MCP 双墙（04/10）、RAG 为受治管道（02）、生产/持久关切（05/06）。

## Missing（缺失）

- 公开 POC 中落地的 Architecture Router 表（任务特征 → Single/Parallel/Supervisor/Hybrid）。
- `xingai-enterprise-ai-pocs` 中可运行的「长任务 MCP → Durable Functions → Operation ID」样例（周报催促；本轮未核到）。
- Decision Ledger 文档中 ReasoningBank 形*策略教训*对象（台账有；策略 schema 未必有）。
- AI Agent Traps 全文（此处 SSRN 403）。
- XingAI Research AI 公开文档中的 Agentic RAG 成本/评测预算。

## Rethink（重思）

- C# MCP SDK 2.0 Preview「全面无状态」是**迁移观察项**，不是立刻生产命令——周报也写了等 Stable。
- Azure AI Search Knowledge Base 减少编排样板，**不**替代 ACL、新鲜度与评测闸（仍属课程 02）。
- 保险 arXiv 为合成 STUW——可作蓝图，不是 Claims 生产证明。
- 没有成功/失败*条件*就把一切记忆叫 ReasoningBank，会塌回聊天日志。

## Debate（争议）

- Architecture Router 放在 Orchestrator 内，还是独立控制面服务。
- MCP Tasks / 持久句柄 vs 更严 SLO 下的同步工具。
- 可复用策略进 Decision Ledger，还是独立经验库。
- Foundry Toolbox 发现 vs 非 Azure XingAI demo 的自建 MCP 控制面。

## Needs evidence（待证）

- 哪个公开 XingAI POC（若有）已从 MCP 工具返回异步 Operation ID。
- 课程 05 / multi-agent-lab 是按任务特征路由，还是写死拓扑。
- SSRN（或镜像）可读后确认 AI Agent Traps 正文。
- 是否有 XingAI 公开 demo 真正调用 Azure AI Search `2026-04-01` Knowledge Base API。

## Sources（来源）

- Raw：`raw/external/2026-07-17-ai-architecture-digest/`
- 上表主 URL（无 `utm_source`）
- 相关：[agent-governance-and-mcp](../concepts/agent-governance-and-mcp.zh.md)、[课程 04](../courses/04-mcp-interoperability.zh.md)、[课程 10](../courses/10-oauth-oidc-azure-identity.zh.md)、[rag-vs-agentic-rag-vs-xingai](rag-vs-agentic-rag-vs-xingai.zh.md)
