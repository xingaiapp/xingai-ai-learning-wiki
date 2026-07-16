# 第 02 课:RAG 与知识系统

English: [02-rag-knowledge-systems.md](02-rag-knowledge-systems.md)

**先修课程:** [01](01-llm-application-engineering.zh.md) · **通过门槛:** 有依据答案的评测

检索增强生成(RAG)是一门纪律,而不是一次库函数调用:摄入 → 解析 → 分块 →
增强 → 索引 → 检索 → 重排 → 组装 → 带引用生成 → 评测,授权(文档级 ACL)
要在排序**之前**、而不是之后执行。故障分析清单(被投毒的文档、跨租户泄露、
过期索引、"看起来有引用、实则无依据"的断言)读起来就像
[claims-multiagent-rag-poc](../products/claims-multiagent-rag-poc.zh.md) 和
[claims-workflow-v2-poc](../products/claims-workflow-v2-poc.zh.md) 第 2 阶段
RAG 层的检查清单——后者选择在小型、按保单划分的语料库上跳过向量数据库,正是
本课程"小而稳定的语料库优先用长上下文"这一指导原则的实际应用。

## 关联

- [claims-multiagent-rag-poc](../products/claims-multiagent-rag-poc.zh.md)、
  [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.zh.md)
- [概念:缓存 / 兜底 LLM 纪律](../concepts/cache-first-llm-architecture.zh.md)
  ——RAG 的检索步骤本身就是另一层次上的"缓存 vs 重新计算"决策。
- 本课教的 `recall_at_k` 指标,正是第 06 课把这种评测直觉推广为金标准/对抗集
  与发布闸门时所依赖的同一种直觉。
- 营销类"RAG 一栏"海报通常止步于 embed→向量数据库——批判见
  [MCP vs RAG vs Skills](../syntheses/mcp-vs-rag-vs-skills.zh.md)。

## 已验证

`recall_at_k({"a","c"}, ["a","b","c"], 2) == 0.5`、
`recall_at_k(..., 3) == 1.0`,手工核对均正确。
[RAG 论文](https://arxiv.org/abs/2005.11401)(Lewis 等)是该技术真实、正确的
一手来源。ZH 版本于 2026-07-16 摄入:Python 代码逐字节一致,标题数一致(7/7)。

## 来源

`raw/courses/02-rag-knowledge-systems/README.md`
