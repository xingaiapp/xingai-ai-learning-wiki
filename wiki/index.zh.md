# 索引

English: [index.md](index.md)

如果你是第一次来,先看 [overview.zh.md](overview.zh.md)。本页是扁平目录,回答
问题时先读这里,再深入具体页面。

## 课程(`wiki/courses/`)

| 页面 | 一句话摘要 |
|---|---|
| [00-ai-foundations](courses/00-ai-foundations.zh.md) | 词汇与心智模型:模型是概率性的,不是神谕。 |
| [01-llm-application-engineering](courses/01-llm-application-engineering.zh.md) | 在模型调用外围建立带类型的边界——下游一切都假设了这套纪律。 |
| [02-rag-knowledge-systems](courses/02-rag-knowledge-systems.zh.md) | 检索是一条受治理的流水线,不是一次库函数调用;ACL 先于排序。 |
| [03-tool-use-ai-agents](courses/03-tool-use-ai-agents.zh.md) | 工作流 vs agent;有边界的权限;对后果性动作设审批闸。 |
| [04-mcp-interoperability](courses/04-mcp-interoperability.zh.md) | MCP 作为受治理的能力边界;confused-deputy 风险。 |
| [05-agent-runtime-multi-agent](courses/05-agent-runtime-multi-agent.zh.md) | 持久化执行;只在真正需要专业化时才加 agent。 |
| [06-production-ai-engineering](courses/06-production-ai-engineering.zh.md) | Demo 与生产证据的区别;发布闸门;金标准/对抗集评测。 |
| [07-enterprise-decision-systems](courses/07-enterprise-decision-systems.zh.md) | 决策台账(Decision Ledger)模式,作为架构来教。 |
| [08-ai-leadership-cto](courses/08-ai-leadership-cto.zh.md) | 组合判断力;打分,但不让分数替你做决定。 |
| [09-ai-interview-mastery](courses/09-ai-interview-mastery.zh.md) | AI 工程面试题(不是通用数据结构与算法刷题)。 |

## 产品(`wiki/products/`)

| 页面 | 一句话摘要 |
|---|---|
| [xingai-enterprise-ai-design](products/xingai-enterprise-ai-design.zh.md) | 课程枢纽:课程、文章、指南、深度企业 AI 索引。 |
| [claims-workflow-v2-poc](products/claims-workflow-v2-poc.zh.md) | 多 agent 理赔流水线;第 1–3 阶段(MCP、LLM+RAG、LangGraph)。 |
| [claims-mcp-oauth-poc](products/claims-mcp-oauth-poc.zh.md) | 面向 claims MCP 的真实 OAuth 2.1 + PKCE + 双墙鉴权。 |
| [claims-partner-api-mcp-poc](products/claims-partner-api-mcp-poc.zh.md) | 全 API 覆盖的 MCP 表面;鉴权延后。 |
| [claims-multiagent-rag-poc](products/claims-multiagent-rag-poc.zh.md) | Supervisor + RAG + human-in-the-loop 的理赔演示。 |
| [multi-agent-lab](products/multi-agent-lab.zh.md) | Orchestrator + 专家 agent + SQLite trace(平台 MVP)。 |
| [event-bus-ai-review](products/event-bus-ai-review.zh.md) | 事件总线 AI 审核——仅架构设计,不可运行。 |
| [xingai-engineering-system](products/xingai-engineering-system.zh.md) | 公开模式文档(决策台账、loop、cache/worker)。 |
| [xingai-tech-blog](products/xingai-tech-blog.zh.md) | 精选架构类教学文章。 |

## 概念(`wiki/concepts/`)

| 页面 | 一句话摘要 |
|---|---|
| [5w-how-framework](concepts/5w-how-framework.zh.md) | 每门课程的教学脊柱。 |
| [decision-ledger-pattern](concepts/decision-ledger-pattern.zh.md) | 不可变、带版本的决策记录。 |
| [cache-first-llm-architecture](concepts/cache-first-llm-architecture.zh.md) | 控制 LLM 成本 / 绝不让单次调用成为单点故障。 |
| [agent-governance-and-mcp](concepts/agent-governance-and-mcp.zh.md) | 双墙鉴权:OAuth scope 对比业务规则 policy。 |
| [loop-engineering](concepts/loop-engineering.zh.md) | 带状态、停止条件、可评测步骤的显式 loop。 |

## 综合(`wiki/syntheses/`)

| 页面 | 一句话摘要 |
|---|---|
| [mcp-vs-rag-vs-skills](syntheses/mcp-vs-rag-vs-skills.zh.md) | 三栏海报对比 XingAI:构成关系而非"二选一";Skills≠MCP 工具。 |
| [enterprise-agent-architecture-vs-xingai](syntheses/enterprise-agent-architecture-vs-xingai.zh.md) | Rishi 企业 agent 海报对比第 02–07 课/claims POC——双方各自的已知缺口。 |
| [layers-of-ai-vs-curriculum](syntheses/layers-of-ai-vs-curriculum.zh.md) | 流行的 Classical→Agentic 分层图映射到 XingAI 课程——以及"自主"被夸大的地方。 |
| [claims-poc-family-tradeoffs](syntheses/claims-poc-family-tradeoffs.zh.md) | 四个 claims POC 之间 Auth vs Coverage vs 工作流的矩阵(+ event-bus 对照)。 |
| [review-findings-2026-07-16](syntheses/review-findings-2026-07-16.zh.md) | 课程审计记录:结构、代码、链接、双语一致性。 |

## 原始来源(`raw/`)

公开快照,2026-07-16(全量同步)刷新。跳过清单:私有仓库、`xingai-ai-learning-wiki`
自身、`xingai-dot-app`。

- `courses/` —— 基础赛道 00–09 文件夹 + COURSE-STANDARD + 索引
- `xingai-enterprise-ai-design/` —— 文章、指南、评估 README、深度企业 AI README
- `pocs/` —— 全部六个公开 POC + 仓库 ADR 001–009
- `xingai-engineering-system/` —— 精选模式文档 + ADR-002
- `xingai-tech-blog/posts/` —— 九篇架构类文章
- `external/` —— 临时 URL/图片/上下文摄入包(见 `xingai-wiki-ingest`)
- `_llm-wiki-pattern.md` —— LLM Wiki 模式文档
