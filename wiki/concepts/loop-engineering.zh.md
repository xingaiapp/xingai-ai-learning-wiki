# 概念:Loop 工程

English: [loop-engineering.md](loop-engineering.md)

带状态、带停止条件、步骤可评测的显式 loop——把 agent/LLM 的工作当作一个
经过工程设计的控制回路,而不是无边界的聊天。在设计文章、engineering-system
模式文档、以及 tech-blog 深度文章中都有讲授;进阶赛道在 `deep-enterprise-ai`
中延续这一主题。

## 出现的位置(公开)

| 来源 | 角度 |
|---|---|
| 设计文章(Beyond Prompt Engineering / Prompt→Loop / Anthropic getting started) | 教学法:从单次 prompt 走向持久化 loop |
| `raw/xingai-engineering-system/patterns/loop-engineering-three-layer.md` + `micro-loop-engine.md` | 可复用的模式文档 |
| ADR-005(`raw/pocs/docs/adr/005-loop-engineering-platform-layers.md`) | POC 的平台分层 |
| Tech blog `2026-07-03-loop-engineering-enterprise-ai-runtime.md` | 运行时视角 |
| [第 05 课](../courses/05-agent-runtime-multi-agent.zh.md) / deep-enterprise-ai 第 05 课 | 在课程体系中的位置 |

## 关联

- [概念:缓存 / 兜底 LLM 纪律](cache-first-llm-architecture.zh.md)——loop
  仍然需要受控的成本与兜底机制。
- [概念:Agent 治理与 MCP](agent-governance-and-mcp.zh.md)——调用工具的 loop
  需要墙。
- 可运行的图:[claims-workflow-v2-poc](../products/claims-workflow-v2-poc.zh.md)、
  [claims-multiagent-rag-poc](../products/claims-multiagent-rag-poc.zh.md)
- 外部参考海报(是批判对象,不是蓝图):
  [企业 agent 架构对比 XingAI](../syntheses/enterprise-agent-architecture-vs-xingai.zh.md)

## 来源

`raw/xingai-enterprise-ai-design/articles/2026-07-03-beyond-prompt-engineering-loop-engineering.md`、
`raw/xingai-engineering-system/patterns/loop-engineering-three-layer.md`、
`raw/pocs/docs/adr/005-loop-engineering-platform-layers.md`、
`raw/xingai-tech-blog/posts/2026-07-03-loop-engineering-enterprise-ai-runtime.md`
