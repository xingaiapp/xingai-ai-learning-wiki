# OAuth、OIDC、Azure Identity 与 API Security

English: [00-overview.md](00-overview.md)

来自用户教学大纲的目录（`raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`）。各页**批判并映射**到 XingAI 公共 MCP/OAuth 材料——不是大纲粘贴。

**课程：** [enterprise-ai-design 课程 10](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/README.zh.md) · [wiki 课程页](../../courses/10-oauth-oidc-azure-identity.zh.md)

**本次无 UX PNG**（身份理论 / Azure 映射；未附产品界面图）。

## 阅读顺序

1. 先读 [02 认证 vs 授权](02-authentication-vs-authorization.zh.md)、[05 ID vs Access Token](05-id-token-vs-access-token.zh.md)。
2. 再读 [06 Auth Code + PKCE](06-authorization-code-flow-pkce.zh.md)、[10 Scope / Role / 业务授权](10-scope-role-business-authorization.zh.md)。
3. Agent/MCP：[22 MCP Server 认证授权](22-mcp-server-authn-authz.zh.md) + [agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)。
4. Azure 页（12–21、26）视为**参考映射**，不是「XingAI 已跑此栈」。

## 目录

| # | 页面 |
|---|---|
| [01](01-iam-overview.zh.md) | 身份与访问管理总览 |
| [02](02-authentication-vs-authorization.zh.md) | 身份认证与授权 |
| [03](03-oauth-2-fundamentals.zh.md) | OAuth 2.0 基础 |
| [04](04-openid-connect-fundamentals.zh.md) | OpenID Connect 基础 |
| [05](05-id-token-vs-access-token.zh.md) | ID Token 与 Access Token |
| [06](06-authorization-code-flow-pkce.zh.md) | 授权码流程与 PKCE |
| [07](07-state-nonce-and-pkce.zh.md) | state、nonce 与 PKCE |
| [08](08-oauth-token-types.zh.md) | OAuth 令牌类型 |
| [09](09-jwt-bearer-opaque-pop.zh.md) | JWT、Bearer、Opaque 与 PoP |
| [10](10-scope-role-business-authorization.zh.md) | Scope、Role 与业务授权 |
| [11](11-oidc-discovery-and-jwks.zh.md) | OIDC Discovery 与 JWKS |
| [12](12-microsoft-entra-id-architecture.zh.md) | Microsoft Entra ID 架构 |
| [13](13-azure-app-registration.zh.md) | Azure 应用注册 |
| [14](14-msal-integration.zh.md) | MSAL 集成 |
| [15](15-azure-api-management-security.zh.md) | Azure API Management 安全 |
| [16](16-managed-identity-workload-identity.zh.md) | 托管标识与工作负载标识 |
| [17](17-on-behalf-of-flow.zh.md) | On-Behalf-Of 流程 |
| [18](18-session-and-cookie-security.zh.md) | 会话与 Cookie 安全 |
| [19](19-api-keys-and-pats.zh.md) | API Key 与 PAT |
| [20](20-oauth-oidc-vs-saml.zh.md) | OAuth/OIDC 与 SAML |
| [21](21-microsoft-entra-external-id.zh.md) | Microsoft Entra External ID |
| [22](22-mcp-server-authn-authz.zh.md) | MCP Server 认证与授权 |
| [23](23-logging-monitoring-auditing.zh.md) | 日志、监控与审计 |
| [24](24-security-best-practices.zh.md) | 安全最佳实践 |
| [25](25-common-errors-troubleshooting.zh.md) | 常见错误与排障 |
| [26](26-complete-azure-reference-architecture.zh.md) | 完整 Azure 参考架构 |

## 已知

- 大纲给出初学者→Azure 实践的连贯脊柱（§1–§24），见 `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`。
- XingAI 已有可运行的 OAuth+PKCE+两墙教学：[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)。

## 缺失

- 本 wiki 尚无 live Entra 截图 / discovery JSON / APIM 策略。
- 并非每条都已代码核验到 POC（部分依赖现有产品页）。

## 需重新思考

- 把完整 Azure 参考架构当每个开源 POC 默认栈会伤害可移植性。
- 「接了 OAuth」却无业务策略，通不过两墙标准。

## 争议

- XingAI 公共库教学应 Entra 优先还是 IdP 可移植优先。

## 待证

- 哪些 XingAI 生产应用今天使用 Entra External ID、MSAL 或 APIM。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`、`raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
