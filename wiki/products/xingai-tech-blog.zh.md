# 产品族:xingai-tech-blog(精选)

English: [xingai-tech-blog.md](xingai-tech-blog.md)

**仓库:** [xingai-tech-blog](https://github.com/xingaiapp/xingai-tech-blog)

Raw 里有九篇英文帖。本页**不是**那份文件清单——而是这些帖合起来论证、而课程/POC 单独留下未明说的内容。

## 横切主张(来自精选集)

1. **决策引擎 ≠ 聊天机器人**(`2026-07-01-xingai-decision-engine-not-chatbot`)——与第 07 课、以及理赔「助手不是自动裁决」姿态同一极。若 UI 是聊天记录,你大概把产品搞反了。
2. **MCP 分阶段,不是大爆炸网关**(`mcp-phased-rollout`, `mcp-architecture-best-practices`)——匹配 oauth-vs-coverage 拆分:在薄表面上证明鉴权,在另一表面上证明覆盖,以后再组合([族综合](../syntheses/claims-poc-family-tradeoffs.zh.md))。
3. **Skills vs MCP**(`2026-06-14-cursor-skills-vs-mcp-when-to-use-which`)——不同信任与分发边界;第 04 课的能力协商是 MCP 形的,而 agent skills 是编写时的包。不要用对方的清单给这一方打分。把它们当成互斥的营销「MCP vs RAG vs Skills」海报通不过这道测试——见 [mcp-vs-rag-vs-skills](../syntheses/mcp-vs-rag-vs-skills.zh.md)。

4. **Loop 胜过提示词**(`loop-engineering-enterprise-ai-runtime`,外加设计文章)——见[Loop 工程](../concepts/loop-engineering.zh.md)。
5. **Worker 写入 / CQRS**(`cqrs-sqlite-worker-writes`)——与第 07 课「API 做传输,worker 做计算」同韵。公开教学帖;本 wiki 仍不摄入它可能暗指的私有产品 ADR。
6. **理赔多 agent 写记**(`2026-06-25-...`)——[claims-multiagent-rag-poc](claims-multiagent-rag-poc.zh.md) 的叙事伴侣,不是第二真相源;若 README 与帖不一致——优先 POC 树 + ADR。

## 故意跳过

关于私有应用的产品变更日志帖(firewall、learn 内部、invest 摘要、radar 栈)。那些是公开文本,但会把本 wiki 拖向私有产品考古。优先课程 + POC + 模式包。

## 来源

`raw/xingai-tech-blog/posts/`(九个精选文件);跨帖综合,不是目录。
