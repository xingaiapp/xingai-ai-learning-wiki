# Course 10: OAuth, OIDC, Azure Identity & API Security

Chinese: [10-oauth-oidc-azure-identity.zh.md](10-oauth-oidc-azure-identity.zh.md)

**Prerequisite:** [04](04-mcp-interoperability.md) recommended · **Gate:** secured OAuth/OIDC + two-wall lab · **Related deep track:** [deep-enterprise-ai auth](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/deep-enterprise-ai/09-authentication-authorization/README.md)

Specialization after the Level 0–9 hiring ladder. Twenty-six modules: protocol (01–11), Azure mapping (12–21), MCP/ops/architecture (22–26). Portable OIDC/OAuth first; Entra/MSAL/APIM are a reference mapping.

## Connects to

- Design course hub: [courses/10-oauth-oidc-azure-identity](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/README.md)
- [Concept catalog: OAuth / OIDC / Azure Identity](../concepts/oauth-oidc-azure-identity/00-overview.md)
- [Course 04](04-mcp-interoperability.md), [claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.md)
- Labs: [PKCE lab](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.md), [auth deep dive](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-auth-deep-dive.md)

## Known

- Course README + 26 bilingual modules published in `xingai-enterprise-ai-design` (2026-07-16).
- Final rules match the course hub (`OAuth → API`, `OIDC → login`, two-wall scope vs business policy).
- Concept catalog pages under [`oauth-oidc-azure-identity`](../concepts/oauth-oidc-azure-identity/00-overview.md) were **rewritten from Course 10** (teach block + epistemic critique), with raw snapshot at `raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/`.

## Missing

- Live Entra tenant screenshots in the course itself (point to Microsoft Learn).
- Runnable Entra-specific lab beyond the portable FastAPI PKCE lab.

## Rethink

- Azure-only teaching can hide portable OIDC mistakes; Course 10 keeps Entra as mapping, not religion.

## Debate

- Whether Course 10 should become Level 10 on the hiring ladder or stay a specialization electives track.

## Needs evidence

- Which XingAI production apps already use Entra External ID / MSAL / APIM.

## Sources

`raw` not required for this page — primary source is the public design course README.
