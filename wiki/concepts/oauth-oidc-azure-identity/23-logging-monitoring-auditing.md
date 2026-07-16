# 23. Logging, Monitoring, and Auditing

Chinese: [23-logging-monitoring-auditing.zh.md](23-logging-monitoring-auditing.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- Log oid/tid/app/scopes/tool/resource/decision/policy/correlation — never tokens/secrets (§21).
- Aligns with Decision Ledger instinct: durable allow/deny with provenance ([decision-ledger-pattern](../decision-ledger-pattern.md)).

## Missing

- Sentinel/App Insights wiring examples absent from XingAI raw.

## Rethink

- Logging full prompts that embed tokens — adjacent leak class.

## Debate

- What belongs in Decision Ledger vs SIEM.

## Needs evidence

- Public POC audit log field lists vs outline table.

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
