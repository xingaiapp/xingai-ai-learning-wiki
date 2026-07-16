# 07. state、nonce 与 PKCE

English: [07-state-nonce-and-pkce.md](07-state-nonce-and-pkce.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- state 护回调/CSRF；nonce 绑定 ID Token；PKCE 绑定 code 与 Client（§4）。
- 应用 MSAL 等库生成——大纲 §12 反对手写。

## 缺失

- 未量化 state/nonce 存储位置（cookie vs 服务端会话）。

## 需重新思考

- 开发者常把 state 与 nonce 混为一谈——§4.1 对照表是解药。

## 争议

- PKCE S256 强制 vs plain 遗留场景。

## 待证

- claims-mcp-oauth-poc 中 state/nonce 代码路径（下次代码核验再引）。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
