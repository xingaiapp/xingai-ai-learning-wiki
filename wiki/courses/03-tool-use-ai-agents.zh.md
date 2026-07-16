# 第 03 课:工具调用与 AI Agent

English: [03-tool-use-ai-agents.md](03-tool-use-ai-agents.md)

**先修课程:** [01](01-llm-application-engineering.zh.md) · **通过门槛:** 安全的工作流/agent 对比 · **下一课:** [04 MCP](04-mcp-interoperability.zh.md)

后续一切都依赖的"工作流 vs agent"区分:工作流走的是写死的代码路径,agent 则
让模型在*有边界的权限*内自行选择步骤和工具。状态图中"校验 → 审批(后果性动作)/
执行(只读)"的拆分,与
[claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.zh.md) 的双墙授权模型
相对应——OAuth scope 回答"这个调用方到底能不能调用这个工具",本课程的审批闸
回答"这个具体动作,现在,是否被允许"。

故障分析中"工具描述是规划环节的不可信输入"这一条,与
`claims-workflow-v2-poc` 的 `PRODUCTION-READINESS.md` 中针对自由文本
`loss_description` 标记的问题,是同一种底层故障模式——不可信内容左右了
agent/LLM 的决策。

## 关联

- [04 MCP 与互操作性](04-mcp-interoperability.zh.md)——MCP 是实现本课程
  "带策略与审计的最小权限工具"这一理念的一种方式。
- [概念:Agent 治理与 MCP](../concepts/agent-governance-and-mcp.zh.md)
- [claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.zh.md)、
  [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.zh.md)

## 已验证

ZH 版本于 2026-07-16 摄入:Python 代码逐字节一致,标题数一致(7/7)。

## 来源

`raw/courses/03-tool-use-ai-agents/README.md`
