# 概念:Loop 工程

English: [loop-engineering.md](loop-engineering.md)

带状态、停止条件、可评测步骤的显式 loop——把 agent/LLM 工作当成工程化控制环,而不是开放聊天。贯穿设计文章、engineering-system 模式与 tech-blog;进阶轨在 `deep-enterprise-ai` 继续。

XingAI 地图(三层 + 硬停止——不是无限智能体套件):

![XingAI Loop 工程 — Context / Harness / Loop](../assets/ux/loop-engineering-vs-xingai/xingai-map.png)

与 Cobus Greyling OSS 工具包海报消歧:[loop-engineering-toolkit-vs-xingai](../syntheses/loop-engineering-toolkit-vs-xingai.zh.md)。

## 已知

- 公开模式分开 **Context | Harness | Loop**;Loop 要有入口、循环体、可编程停止(最大迭代、预算、无进展、超时、HITL)。引用 `raw/xingai-engineering-system/patterns/loop-engineering-three-layer.md`。
- 教学法:从单次 prompt 走向持久 loop——设计文章 + tech blog(见来源)。
- 公开 POC 可运行图:[claims-workflow-v2-poc](../products/claims-workflow-v2-poc.zh.md)、[claims-multiagent-rag-poc](../products/claims-multiagent-rag-poc.zh.md)。

## 缺失

- 许多营销「loop」图省略停止条件与 MCP 墙(见工具包综合页)。
- Decision ledger 作为 loop 产物在别处教授([决策台账](decision-ledger-pattern.zh.md)),但常不画进 loop 海报。

## 需重新思考

- npm README 营销里的「Loop」≠ XingAI 三层控制环——引用时分开。
- 仅把停止条件写进 prompt 通不过模式自身的测试(智能体永远跑)。

## 争议

- Harness 里多少东西(worktrees、调度器)该画进 Loop 层图,多少留在运行时运维文档?

## 待证

- 是否有 XingAI 公开产品按 Cobus 工具包意义打「Loop Ready」分——此处不声称。

## 公开出处

| 来源 | 角度 |
|---|---|
| 设计文章(Beyond Prompt Engineering / Prompt→Loop 等) | 教学法:从单次 prompt 到持久 loop |
| `raw/xingai-engineering-system/patterns/loop-engineering-three-layer.md` + `micro-loop-engine.md` | 可复用模式文档 |
| ADR-005(`raw/pocs/docs/adr/005-loop-engineering-platform-layers.md`) | POC 的平台分层 |
| Tech blog `2026-07-03-loop-engineering-enterprise-ai-runtime.md` | 运行时视角 |
| [第 05 课](../courses/05-agent-runtime-multi-agent.zh.md) / deep-enterprise-ai 第 05 课 | 课程位置 |

## 关联

- [概念:缓存/回退 LLM 纪律](cache-first-llm-architecture.zh.md)——loop 仍要有界成本与回退
- [概念:Agent 治理与 MCP](agent-governance-and-mcp.zh.md)——调工具的 loop 需要墙
- 可运行图:[claims-workflow-v2-poc](../products/claims-workflow-v2-poc.zh.md)、[claims-multiagent-rag-poc](../products/claims-multiagent-rag-poc.zh.md)
- 工具包海报批判:[loop-engineering-toolkit-vs-xingai](../syntheses/loop-engineering-toolkit-vs-xingai.zh.md)

## 来源

`raw/xingai-enterprise-ai-design/articles/2026-07-03-beyond-prompt-engineering-loop-engineering.md`、
`raw/xingai-engineering-system/patterns/loop-engineering-three-layer.md`、
`raw/pocs/docs/adr/005-loop-engineering-platform-layers.md`、
`raw/xingai-tech-blog/posts/2026-07-03-loop-engineering-enterprise-ai-runtime.md`、
`raw/external/2026-07-19-loop-engineering-toolkit-poster/`
