# 概念:Agent 治理与 MCP

English: [agent-governance-and-mcp.md](agent-governance-and-mcp.md)

两个相关但不同的控制问题,反复出现在课程与公开 POC 中:

1. **调用方能不能调用这个工具?** —— OAuth scope / MCP 授权([第 04 课](../courses/04-mcp-interoperability.zh.md))。
2. **就这一次、这一刻,这个具体动作允不允许?** —— 独立于 scope 的业务规则策略层(金额上限、理赔类型白名单、读/写权限)([第 03 课](../courses/03-tool-use-ai-agents.zh.md)的 `Validate → Approve/Execute` 拆分)。

这种「双墙」拆分不是学院派空谈——
[claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.zh.md)
(ADR-006) 之所以写出来,正是因为 scope 单独表达不了
「这个合作伙伴不得授权超过 $10,000 的结算」。
[第三方 MCP 接入](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-07-15-third-party-mcp-auth-api-key-vs-oauth2.md)
这篇设计文章把同一套推理推广成 API Key vs OAuth 的决策框架。
[claims-partner-api-mcp-poc](../products/claims-partner-api-mcp-poc.zh.md) 是互补的、覆盖面优先的 MCP 表面(鉴权延后)。

更长的 OAuth/OIDC/Azure 教学脊柱(令牌、PKCE、Entra、APIM、MCP Resource Server)见
[OAuth / OIDC / Azure Identity 目录](oauth-oidc-azure-identity/00-overview.zh.md)。

[claims-workflow-v2-poc](../products/claims-workflow-v2-poc.zh.md) 今天实现的是简化版 MCP 数据边界(静态服务令牌;scope 已预命名,留给后续 Authorization Server),并在 `PRODUCTION-READINESS.md` 里标出自由文本理赔字段上的提示注入风险——不受信内容操纵 agent 决策,与第 03 课对工具描述命名的同一类失败。

## 关联

- [第 03 课](../courses/03-tool-use-ai-agents.zh.md)、[第 04 课](../courses/04-mcp-interoperability.zh.md)、[第 05 课](../courses/05-agent-runtime-multi-agent.zh.md)
- [概念:决策台账模式](decision-ledger-pattern.zh.md)——需要事后举证时,治理裁决应落在台账行里。
- 把「MCP vs RAG vs Skills」当成互斥三栏——对照 [mcp-vs-rag-vs-skills](../syntheses/mcp-vs-rag-vs-skills.zh.md) 与 procedure-vs-capability 博文。

## 来源

`raw/courses/03-tool-use-ai-agents/README.md`, `raw/courses/04-mcp-interoperability/README.md`, `raw/pocs/claims-mcp-oauth-poc/`, `raw/pocs/claims-workflow-v2-poc/`, `raw/pocs/docs/adr/006-claims-mcp-oauth-poc-real-auth.md`, `raw/xingai-enterprise-ai-design/articles/2026-07-15-third-party-mcp-auth-api-key-vs-oauth2.md`
