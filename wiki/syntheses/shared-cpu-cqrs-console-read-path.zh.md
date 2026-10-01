# 综合：共享 CPU 的 CQRS 读路径（Invest AI 控制台性能）

English: [shared-cpu-cqrs-console-read-path.md](shared-cpu-cqrs-console-read-path.md)

公开模式来自 Invest AI ADR-056（2026-09-30）：仅有 worker 写 / API 读不够——当二者共用一颗 CPU 与一个 SQLite 时，要用边缘缓存无身份 GET、SSR 并行登录+缓存、以及 worker 增量写入。

## Known（已知）

- Invest AI 已文档化决策缓存的 worker 写 / API 读（[ADR-012](https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/012-decision-cache-boundary.md)）。
- ADR-056 接受：公开决策 GET 的 CDN 白名单、控制台 SSR 并行 seed、dashboard JS 拆包、黄金坑 60s ISR 刷新，并把 OHLCV 增量视为 shared-CPU 争用下的必需项（[ADR-056](https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/056-console-read-path-cdn-parallel-auth.zh.md)）。
- ADR-036 修正写明 OHLCV 全量 vs 增量与回溯检测（[ADR-036](https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/036-worker-ohlcv-bars-cache.zh.md)）。
- 同日教学面：[企业设计文](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-09-30-shared-cpu-cqrs-edge-cache-vs-write-amplification.zh.md) · [技术博客](https://github.com/xingaiapp/xingai-tech-blog/blob/main/posts/2026-09-30-invest-ai-console-cdn-parallel-auth-ohlcv.zh.md)。
- ADR-056 记载上线后抽查：dashboard CDN HIT ~0.15s；强制 OHLCV `written=3915`，`incremental=69`（曾 ~6.7 万全量）。产品：https://invest.xingai.app

## Missing（缺失）

- 第三方对 invest.xingai.app 的独立压测（目前仅有 ADR/博客中的运营测量）。
- 默认拆成独立 worker 机器（仅列为后续可选项）。
- 除 ADR 数字外，强制 OHLCV SSH 的公开日志包。

## Rethink（重思）

- 「我们有 CQRS」≠「worker 刷新时读也快」。
- 给共享市场快照挂 Bearer，等于放弃 CDN 共享。
- 每隔 N 分钟全历史重写是写放大，不是新鲜度。

## Debate（辩论，保持开放）

| 问题 | 倾向 A | 倾向 B | 状态 |
|---|---|---|---|
| 先升配 shared VM 还是先做增量 I/O？ | 升配 | 削减重写量 | ADR-056 先增量+CDN；VM 可选 |
| CDN 决策 JSON 允许多旧？ | 只能秒级 | 研究控制台可 30–60s+SWR | ADR 接受短 TTL |

## Needs evidence（待证）

- 增量上线后完整 worker 周期内的持续 p95（不止一次强制 OHLCV）。
- dashboard 面板再拆对 LCP/hydrate 的量化（未宣称）。

## Links

- https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/056-console-read-path-cdn-parallel-auth.zh.md
- https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/036-worker-ohlcv-bars-cache.zh.md
- https://github.com/xingaiapp/xingai-tech-blog/blob/main/posts/2026-09-30-invest-ai-console-cdn-parallel-auth-ohlcv.zh.md
- https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-09-30-shared-cpu-cqrs-edge-cache-vs-write-amplification.zh.md
