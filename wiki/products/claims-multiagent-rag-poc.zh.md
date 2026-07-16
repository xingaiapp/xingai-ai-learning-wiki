# 产品:claims-multiagent-rag-poc

English: [claims-multiagent-rag-poc.md](claims-multiagent-rag-poc.md)

**仓库:** [xingai-enterprise-ai-pocs](https://github.com/xingaiapp/xingai-enterprise-ai-pocs) · **状态:** 可运行 · 第 1–6 阶段

Supervisor + 专家 agent + 带引用的 RAG + human-in-the-loop,面向保险理赔。明确是**决策助手**,不是自动裁决——不确定或高金额路径会升级。

## README 不会强调的

它夹在[multi-agent-lab](multi-agent-lab.zh.md)(平台形态、假工具)与[claims-workflow-v2-poc](claims-workflow-v2-poc.zh.md)(领域修正 + MCP + 双路径 LLM + LangGraph)之间。同样的行业名词,不同的作业题:

| POC | 作业题 |
|---|---|
| multi-agent-lab | 不带领域包袱,能不能交接 + 追踪? |
| **本 POC** | 专家 + RAG 引用能不能撑住理赔故事? |
| workflow-v2 | 能不能修好一张坏自动化图,*并且*加深 MCP/LLM/图? |

第 02 课的「ACL 先于排序」与「引用形态的无支撑断言」失败模式,是评估本 POC 检索 agent 的镜头。第 05 课的「只为真正的专业化才加 agent」解释了为何 Intake / Retrieval / Fraud / Adjudication 是分开的节点,而不是一个巨型提示词。

## 张力

Human-in-the-loop 在这里是特性;workflow-v2 更往自动化阶段推进,用 Case Resolution Router 做*恢复*,而不只是升级。不要把它们当成同一二进制的 v1/v2——它们优化不同风险。

## 关联

- [第 02 课](../courses/02-rag-knowledge-systems.zh.md)、[第 05 课](../courses/05-agent-runtime-multi-agent.zh.md)、[概念:Loop 工程](../concepts/loop-engineering.zh.md)
- [Claims POC 族](../syntheses/claims-poc-family-tradeoffs.zh.md)
- 博文快照:`raw/xingai-tech-blog/posts/2026-06-25-claims-multiagent-rag-supervisor-poc.md`

## 来源

`raw/pocs/claims-multiagent-rag-poc/README.md`, `architecture.md`; `raw/pocs/docs/adr/` 下的 ADR-001/002
