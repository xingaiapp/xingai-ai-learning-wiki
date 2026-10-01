# Synthesis: Shared-CPU CQRS Read Path (Invest AI console speed)

Chinese: [shared-cpu-cqrs-console-read-path.zh.md](shared-cpu-cqrs-console-read-path.zh.md)

Public pattern from Invest AI ADR-056 (2026-09-30): CQRS compute/read split is not enough when worker and API share one CPU and one SQLite file — edge-cache identity-free GETs, parallel auth+cache SSR, and incremental worker writes.

## Known

- Invest AI documents worker-write / API-read decision caches ([ADR-012](https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/012-decision-cache-boundary.md)).
- ADR-056 accepts CDN allowlist for public decision GETs, parallel console SSR seeds, dashboard JS split, Golden Pit 60s ISR refresh, and treats OHLCV incremental refresh as required for shared-CPU contention ([ADR-056](https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/056-console-read-path-cdn-parallel-auth.md)).
- ADR-036 amendment details OHLCV full vs incremental modes and re-base detection ([ADR-036](https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/036-worker-ohlcv-bars-cache.md)).
- Teaching surfaces same day: [enterprise design](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-09-30-shared-cpu-cqrs-edge-cache-vs-write-amplification.md) · [tech blog](https://github.com/xingaiapp/xingai-tech-blog/blob/main/posts/2026-09-30-invest-ai-console-cdn-parallel-auth-ohlcv.md).
- ADR-056 cites measured post-ship checks: CDN HIT ~0.15s on dashboard; forced OHLCV `written=3915`, `incremental=69` (was ~67k full rewrite). Product: https://invest.xingai.app

## Missing

- Independent third-party load test of invest.xingai.app (only operator measurements in ADR/blog).
- Separate worker machine as a shipped default (listed as optional follow-up).
- Public runbook screenshot/log bundle for the forced OHLCV SSH command beyond the ADR numbers.

## Rethink

- “We have CQRS” does not imply “reads are fast during worker refresh.”
- Putting Bearer on a shared market snapshot for convenience defeats CDN sharing.
- Full-history rewrite every N minutes is write amplification, not freshness.

## Debate (leave open)

| Question | Lean A | Lean B | Status |
|---|---|---|---|
| Bigger shared VM vs incremental I/O first? | Scale the box | Cut rewrite volume | ADR-056 did incremental + CDN first; VM optional |
| How stale may CDN decision JSON be? | Seconds only | 30–60s + SWR OK for research console | ADR accepts short CDN TTL for console |

## Needs evidence

- Sustained p95 during a full worker cycle after incremental ships (beyond one forced OHLCV run).
- Whether further dashboard panel code-splitting moves LCP/hydrate metrics (not claimed).

## Links

- https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/056-console-read-path-cdn-parallel-auth.md
- https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/036-worker-ohlcv-bars-cache.md
- https://github.com/xingaiapp/xingai-tech-blog/blob/main/posts/2026-09-30-invest-ai-console-cdn-parallel-auth-ohlcv.md
- https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-09-30-shared-cpu-cqrs-edge-cache-vs-write-amplification.md
