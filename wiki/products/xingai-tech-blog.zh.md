# 产品族：xingai-tech-blog（精选）

English: [xingai-tech-blog.md](xingai-tech-blog.md)

**仓库：** [xingai-tech-blog](https://github.com/xingaiapp/xingai-tech-blog)

`raw/` 只保留**精选**教学帖（不是整站镜像）。本页**不是**文件清单——而是这些帖子合在一起、课程/POC  alone 说不清的论点。

## 跨帖主张（精选集）

1. **决策引擎 ≠ 聊天机器人**（`2026-07-01-xingai-decision-engine-not-chatbot`）——与第 07 课、理赔「助手非自动裁决」同极。若 UI 是聊天记录，产品多半反了。
2. **MCP 分阶段，而非一次上齐网关**——对应 oauth vs 覆盖面拆分：薄表面证明鉴权，另一面证明覆盖，再合并（[家族综合](../syntheses/claims-poc-family-tradeoffs.zh.md)）。
3. **Skills vs MCP**（`2026-06-14-cursor-skills-vs-mcp-when-to-use-which`）——信任与分发边界不同；第 04 课能力协商是 MCP 形，agent skills 是编写时包。勿用对方清单互评。把「MCP vs RAG vs Skills」当互斥三栏的海报通不过——见 [mcp-vs-rag-vs-skills](../syntheses/mcp-vs-rag-vs-skills.zh.md)。
4. **Loop 胜过 prompt**——见 [Loop engineering](../concepts/loop-engineering.zh.md)。
5. **Worker 写 / CQRS**——与第 07 课「API 传输、worker 计算」同韵。公开教学帖；本 wiki 仍不摄入其可能影射的私有产品 ADR。
6. **Claims 多 agent 写稿**——[claims-multiagent-rag-poc](claims-multiagent-rag-poc.zh.md) 的叙事同伴；若与 README 冲突，以 POC 树 + ADR 为准。
7. **Scope 不是 policy**（`2026-07-13-mcp-auth-scope-is-not-policy-second-wall` 等）——墙 #1（OAuth）vs 墙 #2（业务规则）。映射 [agent-governance-and-mcp](../concepts/agent-governance-and-mcp.zh.md) 与更长的 [OAuth / OIDC / Azure Identity 目录](../concepts/oauth-oidc-azure-identity/00-overview.zh.md)。
8. **Fail-closed MCP 网关**（Robinhood MCP 等）——后果性工具默认拒绝；人在回路是协议的一部分。
9. **Decision Ledger 作跨产品记忆**（Meal / Learn / Decision Engine 相关帖）——见 [decision-ledger-pattern](../concepts/decision-ledger-pattern.zh.md)。

## 已知

- `raw/xingai-tech-blog/posts/` 于 2026-07-16 扩入七月 MCP 鉴权 / ledger / firewall 教学文（有中文则成对）。
- 上列主张以文件名为据；引用数字/API 前先打开 raw 中的帖。

## 缺失

- 全站约 75 篇英文帖**未**镜像——仅教学优先切片。
- 私有产品 changelog 仍刻意不进综合。

## 需重新思考

- 把 tech blog 当每个 POC 的第二份 README 只会制造噪音；优先 POC + ADR，博客承载*论证*。

## 争议

- 多少 firewall / Robinhood 帖应进学习 wiki，还是留在博客（深度 vs 范围膨胀）。

## 待证

- 精选帖是否仍与后续 POC README 一致。

## 刻意跳过

关于私有应用的产品 changelog（invest 摘要、radar 栈、未公开内部）。优先课程 + POC + 模式包。

## Sources

`raw/xingai-tech-blog/posts/`（精选文件）；跨帖综合，不是目录。
