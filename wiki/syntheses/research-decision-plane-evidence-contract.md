# Synthesis: Research Plane vs Decision Plane (Evidence Contract)

Chinese: [research-decision-plane-evidence-contract.zh.md](research-decision-plane-evidence-contract.zh.md)

Public pattern from Invest AI ADR-055 (2026-09-29): separate what evidence supports from what to do under objectives; join them with an Evidence Contract. Teaching article + tech blog published the same day.

## Known

- Product rule in public Invest surfaces: **No Citation, No Claim** — map/Smart Money citations; landing evidence card hides without role + source ([ADR-054](https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/054-landing-ai-map-preview-not-dashboard.md)).
- CQRS compute/read split already documented ([ADR-012](https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/012-decision-cache-boundary.md)).
- ADR-055 accepts Research Plane / Decision Plane + Evidence Contract as **Accepted (planned)** — not a claim of a deployed gate schema.
- Demo prep (publicly summarized in ADR-055 / design article): Micron lacked verifiable 13F citation; holdings example switched to NVIDIA rather than inventing a MU row.
- Related public teaching: [enterprise design article](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-09-29-research-decision-plane-evidence-contract.md) · [tech blog](https://github.com/xingaiapp/xingai-tech-blog/blob/main/posts/2026-09-29-research-decision-plane-evidence-contract.md).
- Adjacent patterns: facts-only growth + human gate ([ADR-050](https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/050-growth-engine-v1-facts-only.md)); Decision Agent as map projection ([ADR-053](https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/053-decision-agent-cache-projection.md)); execution authorization ≠ evidence check ([Robinhood MCP gates](https://github.com/xingaiapp/xingai-robinhood-mcp) / Invest ADR-028).

## Missing

- Deployed Evidence Contract schema in production cache.
- Enforced Research→Decision software gate with reject metrics.
- End-to-end decision lineage UI.
- Independent revalidation (in these docs) of any specific NVIDIA/Micron 13F row figures — none asserted here.

## Rethink

- “Add another Supervisor agent” without stop authority does not implement the contract.
- Combining research and decision in one prompt hides the gap the Micron incident made visible.
- Missing evidence must not be narrated as negative evidence (“no holders”).

## Debate (leave open)

| Question | Lean A | Lean B | Status |
|---|---|---|---|
| Separate services vs logical planes only? | Microservices per plane | Same worker/workflow, explicit handoff | ADR-055 prefers logical; open for later scale |
| How strict for educational vs execution outputs? | Same contract everywhere | Proportionate controls by stakes | ADR says proportionate + hard stop on material premises |

## Needs evidence

- Measured reject / false-accept rates after a gate ships.
- Filing-to-row mapping audits for any holdings number used in demos (not claimed in ADR-055).

## How to use

- Course / interview probe: “Draw Research vs Decision; inject a missing citation; what happens?”
- When reviewing agent demos: fail any path that invents holdings to keep the story pretty.
