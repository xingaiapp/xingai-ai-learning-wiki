# 课程 10：OAuth、OIDC、Azure 身份与 API 安全

English: [10-oauth-oidc-azure-identity.md](10-oauth-oidc-azure-identity.md)

**建议先修：** [04](04-mcp-interoperability.zh.md) · **门槛：** 受保护的 OAuth/OIDC + 双墙实验 · **相关深造：** [deep-enterprise-ai 认证授权](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/deep-enterprise-ai/09-authentication-authorization/README.zh.md)

Level 0–9 岗位路径之后的专项课。二十六模块：协议（01–11）、Azure 映射（12–21）、MCP/运维/架构（22–26）。先讲可移植 OIDC/OAuth；Entra/MSAL/APIM 是参考映射。

## 关联

- 设计课主页：[courses/10-oauth-oidc-azure-identity](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/README.zh.md)
- [概念目录：OAuth / OIDC / Azure Identity](../concepts/oauth-oidc-azure-identity/00-overview.zh.md)
- [课程 04](04-mcp-interoperability.zh.md)、[claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.md)
- 实验：[PKCE 实验](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.zh.md)、[认证深读](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-auth-deep-dive.zh.md)

## Known（已知）

- `xingai-enterprise-ai-design` 已发布课程 README + 26 个双语模块（2026-07-16）。
- 最终规则与课程主页一致（OAuth→API、OIDC→登录、scope 与业务策略双墙）。
- 概念目录 [`oauth-oidc-azure-identity`](../concepts/oauth-oidc-azure-identity/00-overview.zh.md) 已**按课程 10 重写**（教学块 + 认知批判），快照在 `raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/`。

## Missing（缺失）

- 课程内尚无真实 Entra 租户截图（指向 Microsoft Learn）。
- 除可移植 FastAPI PKCE 实验外，尚无独立 Entra 实验。

## Rethink（重思）

- 只教 Azure 会掩盖可移植 OIDC 错误；课程 10 把 Entra 当映射而非教条。

## Debate（争议）

- 课程 10 应升级为岗位路径 Level 10，还是保持专项选修。

## Needs evidence（待证）

- 哪些 XingAI 生产应用已使用 Entra External ID / MSAL / APIM。

## Sources（来源）

本页以公开设计课 README 为主要来源。
