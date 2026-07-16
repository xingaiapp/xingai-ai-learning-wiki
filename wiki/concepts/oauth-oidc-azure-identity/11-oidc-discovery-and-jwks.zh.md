# 11. OIDC Discovery 与 JWKS

English: [11-oidc-discovery-and-jwks.md](11-oidc-discovery-and-jwks.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- Discovery：`/.well-known/openid-configuration`；JWKS 经 `jwks_uri`；按 `kid` 验签（§9）。
- claims-mcp-oauth 教学强调 `.well-known`。

## 缺失

- 未写 JWKS 轮换 runbook / 缓存 TTL。

## 需重新思考

- 硬编码签名密钥——大纲禁止，玩具演示仍有。

## 争议

- 多租户 issuer 校验策略。

## 待证

- XingAI POC 所用公共演示 AS 的 live discovery JSON。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
