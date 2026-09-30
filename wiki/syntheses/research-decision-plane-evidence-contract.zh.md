# 综合：研究平面 vs 决策平面（证据契约）

英文：[research-decision-plane-evidence-contract.md](research-decision-plane-evidence-contract.md)

来自 Invest AI ADR-055（2026-09-29）的公开模式：把「证据支持什么」与「在目标下该怎么做」分开，用证据契约交接。同日发布教学长文与 tech blog。

## Known（已知）

- 公开 Invest 面的产品规则：**无出处，不宣称** — 地图/Smart Money 带引用；落地页证据卡无角色+来源则隐藏（[ADR-054](https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/054-landing-ai-map-preview-not-dashboard.md)）。
- CQRS 计算/只读拆分已有文档（[ADR-012](https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/012-decision-cache-boundary.md)）。
- ADR-055 将研究平面 / 决策平面 + 证据契约标为 **Accepted (planned)** — 不是已部署门控 schema 的宣称。
- 演示准备（ADR-055 / 设计文公开摘要）：Micron 缺可核验 13F 引用；持仓示例改 NVIDIA，而不是编造 MU 行。
- 相关公开教学：[企业设计文章](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-09-29-research-decision-plane-evidence-contract.zh.md) · [tech blog](https://github.com/xingaiapp/xingai-tech-blog/blob/main/posts/2026-09-29-research-decision-plane-evidence-contract.zh.md)。
- 邻近模式：增长只写事实 + 人工门（[ADR-050](https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/050-growth-engine-v1-facts-only.md)）；Decision Agent 为地图投影（[ADR-053](https://github.com/xingaiapp/xingai-invest-ai/blob/main/docs/adr/053-decision-agent-cache-projection.md)）；执行授权 ≠ 证据核验（Robinhood MCP 门控 / Invest ADR-028）。

## Missing（缺失）

- 生产缓存中已部署的 Evidence Contract schema。
- 带拒绝指标的强制 Research→Decision 软件门。
- 端到端决策血缘 UI。
- 本文档集中对任何具体 NVIDIA/Micron 13F 数字的独立复核 — 此处不断言数字。

## Rethink（重思）

- 再加一个没有阻断权的 Supervisor agent，不等于实现了契约。
- 把研究与决策塞进同一提示，会藏起 Micron 事件暴露的缺口。
- 缺证据不得叙述成否定证据（「没有持有人」）。

## Debate（存疑）

| 问题 | 倾向 A | 倾向 B | 状态 |
|---|---|---|---|
| 拆服务 vs 仅逻辑平面？ | 每平面微服务 | 同一 worker/工作流、显式交接 | ADR-055 偏逻辑；规模化后再议 |
| 教育输出与执行输出严格度？ | 处处同一契约 | 按利害分级 | ADR：可分级 + 材料前提硬停 |

## Needs evidence（待证）

- 门控上线后的拒绝率 / 误放行率。
- 演示所用任何持仓数字的申报→行映射审计（ADR-055 未宣称数字）。

## How to use（用法）

- 课程 / 面试探针：「画出研究 vs 决策；注入缺引用；会发生什么？」
- 审 agent 演示时：为讲故事编造持仓的路径直接判失败。
