# 产品:claims-partner-api-mcp-poc

English: [claims-partner-api-mcp-poc.md](claims-partner-api-mcp-poc.md)

**仓库:** [xingai-enterprise-ai-pocs](https://github.com/xingaiapp/xingai-enterprise-ai-pocs) · **状态:** 可运行 · 第 1 阶段

OpenAPI 优先:把理赔 REST API 包成一个覆盖面广的 MCP 服务器(约 18 个工具 / 7 个域)、Zod 校验输入、幂等支付写入、以及显式的理赔状态状态机。面向第三方的鉴权**故意缺失**。

## README 不会强调的

这是与[claims-mcp-oauth-poc](claims-mcp-oauth-poc.zh.md)对照实验的另一半。若只学 oauth,你会过拟合到极小表面。若只学这个,你会带着共享静态令牌把面向合作伙伴的工具上线,然后宣称完成。ADR-007 把安静的部分说出来:现在做全覆盖,鉴权层以后再加——与 oauth POC 的 scope 组合,不要发明第三套鉴权故事。

动钱的工具(`claims_create_payment`、状态流转)带 `destructiveHint` 与幂等键。那是第 03 课的后果性动作纪律落在工具元数据上,不是落在 LLM 裁判上。

## 在族里的位置

Workflow-v2 的 MCP 表面保持很小(政策 / 台账 / 支付),因为它的实验是编排 + 审计,不是合作伙伴 API 膨胀。Partner-api 才是膨胀实验。见[Claims POC 族](../syntheses/claims-poc-family-tradeoffs.zh.md)。

## 关联

- [概念:Agent 治理与 MCP](../concepts/agent-governance-and-mcp.zh.md)、[第 04 课](../courses/04-mcp-interoperability.zh.md)
- 文章:[MCP API 覆盖 vs 工作流工具](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-07-13-mcp-api-coverage-vs-workflow-tools.md)

## 来源

`raw/pocs/claims-partner-api-mcp-poc/README.md`, `architecture.md`; `raw/pocs/docs/adr/007-claims-partner-api-mcp-poc-full-coverage.md`
