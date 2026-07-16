# OAuth、OIDC、Azure Identity 与 API Security

English: [00-overview.md](00-overview.md)

本目录是对 [`xingai-enterprise-ai-design` **课程 10**](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/README.zh.md) 的 wiki 综合：每页保留课程教学块（5W + 图示 + 最小校验），再对照 XingAI 公开 MCP/OAuth 材料做批判。

**不是**旧外部大纲的粘贴。大纲仅作溯源，见 `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/`。

**课程 wiki 页：** [10-oauth-oidc-azure-identity](../../courses/10-oauth-oidc-azure-identity.zh.md)  
**原始快照：** `raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/`

**本次无 UX PNG**（身份理论 / Azure 映射；无产品界面图）。

## 阅读顺序

1. 协议：[02 认证 vs 授权](02-authentication-vs-authorization.zh.md) → [05 ID vs Access Token](05-id-token-vs-access-token.zh.md) → [06 授权码 + PKCE](06-authorization-code-flow-pkce.zh.md) → [10 Scope / 业务](10-scope-role-business-authorization.zh.md)。
2. Azure 映射：[12 Entra](12-microsoft-entra-id-architecture.zh.md) 至 [21 External ID](21-microsoft-entra-external-id.zh.md) —— 先讲可移植 OIDC 术语。
3. Agent/运维：[22 MCP 认证授权](22-mcp-server-authn-authz.zh.md) + [agent-governance-and-mcp](../agent-governance-and-mcp.zh.md) + [课程 04](../../courses/04-mcp-interoperability.zh.md)。
4. 实验门槛：[PKCE MCP 实验](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.zh.md)。

## 最终规则（课程 10）

```text
OAuth → API 授权
OIDC → 用户登录
ID Token → 客户端
Access Token → API / MCP Server
Refresh Token → 授权服务器
Authorization Code → 令牌端点
state → 保护回调
nonce → 保护 ID Token
PKCE → 保护授权码
Scope → 你能做什么（能力）
Role → 你是什么角色
Business Policy → 该业务对象是否允许
Session → 应用登录状态
```

## 目录

| # | 页面 |
|---|---|
| [01](01-iam-overview.zh.md) | 身份与访问管理概览 |
| [02](02-authentication-vs-authorization.zh.md) | 认证与授权 |
| [03](03-oauth-2-fundamentals.zh.md) | OAuth 2.0 基础 |
| [04](04-openid-connect-fundamentals.zh.md) | OpenID Connect 基础 |
| [05](05-id-token-vs-access-token.zh.md) | ID Token 与 Access Token |
| [06](06-authorization-code-flow-pkce.zh.md) | 授权码流 + PKCE |
| [07](07-state-nonce-and-pkce.zh.md) | state、nonce 与 PKCE |
| [08](08-oauth-token-types.zh.md) | OAuth 令牌类型 |
| [09](09-jwt-bearer-opaque-pop.zh.md) | JWT、Bearer、不透明令牌与 PoP |
| [10](10-scope-role-business-authorization.zh.md) | Scope、角色与业务授权 |
| [11](11-oidc-discovery-and-jwks.zh.md) | OIDC Discovery 与 JWKS |
| [12](12-microsoft-entra-id-architecture.zh.md) | Microsoft Entra ID 架构 |
| [13](13-azure-app-registration.zh.md) | Azure 应用注册 |
| [14](14-msal-integration.zh.md) | MSAL 集成 |
| [15](15-azure-api-management-security.zh.md) | Azure API Management 安全 |
| [16](16-managed-identity-workload-identity.zh.md) | 托管标识与工作负载标识 |
| [17](17-on-behalf-of-flow.zh.md) | 代表流（OBO） |
| [18](18-session-and-cookie-security.zh.md) | 会话与 Cookie 安全 |
| [19](19-api-keys-and-pats.zh.md) | API Key 与 PAT |
| [20](20-oauth-oidc-vs-saml.zh.md) | OAuth/OIDC 与 SAML |
| [21](21-microsoft-entra-external-id.zh.md) | Microsoft Entra External ID |
| [22](22-mcp-server-authn-authz.zh.md) | MCP Server 认证与授权 |
| [23](23-logging-monitoring-auditing.zh.md) | 日志、监控与审计 |
| [24](24-security-best-practices.zh.md) | 安全最佳实践 |
| [25](25-common-errors-troubleshooting.zh.md) | 常见错误与排障 |
| [26](26-complete-azure-reference-architecture.zh.md) | 完整 Azure 参考架构 |

## Known（已知）

- 公开仓库 `xingai-enterprise-ai-design` 已发布课程 10（26 个双语模块 + 主页）；快照在 `raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/`。
- 可运行教学路径早已存在：[PKCE 实验](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.zh.md) + [课程 04](../../courses/04-mcp-interoperability.zh.md) + [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md) 双墙模型。

## Missing（缺失）

- 课程 10 模块内无真实 Entra 租户截图 / APIM 策略 XML / MSAL 样例。
- 模块 26 Azure 参考图缺少可移植的 Fly/Vercel 对照图。

## Rethink（重思）

- 旧 wiki 页只引用外部大纲，图示与失败关闭校验不足——已按课程 10 重写。
- 没有业务策略的「已接入 OAuth」仍达不到双墙标准。

## Debate（争议）

- 课程 10 保持专项，还是升为岗位路径 Level 10。
- 公开 XingAI 仓库默认 Entra 优先，还是 IdP 可移植优先。

## Needs evidence（待证）

- 哪些 XingAI 生产/demo 应用今天使用 Entra External ID、MSAL 或 APIM。

## Sources（来源）

- [课程 10 README](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/README.zh.md)
- `raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/`
- 溯源大纲（已不再作为教学主源）：`raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/`
