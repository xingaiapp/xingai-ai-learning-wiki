# 产品:claims-mcp-oauth-poc

English: [claims-mcp-oauth-poc.md](claims-mcp-oauth-poc.md)

**仓库:** [xingai-enterprise-ai-pocs](https://github.com/xingaiapp/xingai-enterprise-ai-pocs) · **状态:** 可运行 · 第 1 阶段

公开证明:「MCP 鉴权」不是中间件勾选项。OAuth 2.1 + 强制 PKCE、`.well-known` 发现、短寿命 audience 限定 JWT、Review→Adjudicate(禁止一步绑定写)、以及双墙——scope 回答「调用方能不能调这个工具」,结算策略回答「*这一笔*理赔在*这个*金额上能不能过」。

## README 不会强调的

故意**窄**。实验对象是密码学与策略墙时,四个左右的工具胜过十八个。这就是它与[claims-partner-api-mcp-poc](claims-partner-api-mcp-poc.zh.md)(覆盖面优先、鉴权延后)相对而立的原因。把任何一个当成「唯一」理赔 MCP 设计都会压扁矩阵——见[Claims POC 族](../syntheses/claims-poc-family-tradeoffs.zh.md)。

第 2 墙是第 03 课的想法(`Validate → Approve` 对后果性动作)在 `policies.py` 里落地为代码,不是提示词文本。Scope 单独表达不了金额上限;这正是 ADR-006 的全部要点。

## 与 workflow-v2 的张力

[claims-workflow-v2-poc](claims-workflow-v2-poc.zh.md) 的 MCP 服务器仍用静态服务令牌。它自己的生产就绪清单把「真实 OAuth」排在优先级 #2,并把第 4 阶段指向*本*模式。所以缺口不是「没人设计鉴权」——而是「workflow POC 还没把 auth POC 接上」。

## 关联

- [概念:Agent 治理与 MCP](../concepts/agent-governance-and-mcp.zh.md)、[第 03 课](../courses/03-tool-use-ai-agents.zh.md)、[第 04 课](../courses/04-mcp-interoperability.zh.md)
- 设计:[Robinhood MCP 案例](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-07-11-mcp-in-production-robinhood-case.md)、[PKCE lab](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.md)

## 来源

`raw/pocs/claims-mcp-oauth-poc/`(README、architecture、mcp-auth-deep-dive); `raw/pocs/docs/adr/006-claims-mcp-oauth-poc-real-auth.md`
