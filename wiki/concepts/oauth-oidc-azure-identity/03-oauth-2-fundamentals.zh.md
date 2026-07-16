# 03. OAuth 2.0 基础

English: [03-oauth-2-fundamentals.md](03-oauth-2-fundamentals.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- OAuth 2.0 是授权框架：Client / AS / RS / scope——本身不是标准化登录协议（§1.2）。
- [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md) 以 MCP Resource Server 形态实现 OAuth 2.1 + PKCE。

## 缺失

- 大纲未集中对比 device code / client credentials / ROPC。

## 需重新思考

- 把「用 Google 登录」一律叫 OAuth 而不提 OIDC，会糊掉 §1.3。

## 争议

- OAuth 2.0 与 2.1（公有客户端强制 PKCE）——XingAI POC 偏 2.1，业界仍混用。

## 待证

- 各公共 POC README 声称的 OAuth 版本需再核验。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
