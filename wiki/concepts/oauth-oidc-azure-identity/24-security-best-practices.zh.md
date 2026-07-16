# 24. 安全最佳实践

English: [24-security-best-practices.md](24-security-best-practices.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- Client：Auth Code+PKCE+MSAL；不用 ID Token 调 API；不用 Access Token 做 SPA 授权 UI。API：校验+业务授权+401/403。基础设施：HTTPS、MI、Key Vault、短 TTL（§22）。

## 缺失

- 未列事件响应/攻防演练。

## 需重新思考

- 无墙 #2 测试的清单表演。

## 争议

- 本地演示 POC vs 生产门槛松紧。

## 待证

- 合规映射（SOC2 等）——超出范围/unknown。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
