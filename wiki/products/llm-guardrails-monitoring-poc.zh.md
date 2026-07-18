# 产品：llm-guardrails-monitoring-poc

English: [llm-guardrails-monitoring-poc.md](llm-guardrails-monitoring-poc.md)

**仓库：** [xingai-enterprise-ai-pocs](https://github.com/xingaiapp/xingai-enterprise-ai-pocs/tree/main/pocs/llm-guardrails-monitoring-poc) · **状态：** Runnable · Phase 1（ADR-010）

十二步 **Plan → Build → Validate → Operate** 演示，每道墙带 XingAI 纠正。Mock 模型。失败关闭跳过。8020 端口 UI 探针：正常路径、注入、高风险工具、弱证据。

## 已知

- `backend/pipeline.py` 实现 1–12 步，状态含 `passed` / `blocked` / `warned` / `skipped` — 公开 POC README + ADR-010。
- 第 6 步扫描用户 + RAG + 工具文本；第 7 步用模拟 MCP scope 墙拦截 `transfer_funds`；第 12 步写 ledger `ship_answer` / `escalate_human`。
- 2026-07-17 设计文与技术博文已发布并链接本 POC。

## 缺失

- 真实 OAuth / Entra / APIM（交给 [claims-mcp-oauth-poc](claims-mcp-oauth-poc.zh.md)）。
- 真实 LLM、向量库、长任务 MCP 持久运行时。
- 生产 CI 评测硬闸门（演示里仅记录标记）。

## 需重新思考

- 不要把公开海报的 **Tools** 行读成这个 POC 的架构——重点是墙，不是 logo（[综合页](../syntheses/llm-guardrails-monitoring-vs-xingai.zh.md)）。

## 争议

- Validate（8–10）应抽成共享策略服务，还是为教学 POC 留在进程内？

## 待证

- 课堂 / 管理层演示效果超出本地 `pytest` 的证据——仓库内尚未度量。

## 关联

- [llm-guardrails-monitoring-vs-xingai](../syntheses/llm-guardrails-monitoring-vs-xingai.zh.md)
- [claims-mcp-oauth-poc](claims-mcp-oauth-poc.zh.md)、[multi-agent-lab](multi-agent-lab.zh.md)
- [第 03 课](../courses/03-tool-use-ai-agents.zh.md)、[04](../courses/04-mcp-interoperability.zh.md)、[06](../courses/06-production-ai-engineering.zh.md)

## 来源

- https://github.com/xingaiapp/xingai-enterprise-ai-pocs/tree/main/pocs/llm-guardrails-monitoring-poc
- https://github.com/xingaiapp/xingai-enterprise-ai-pocs/blob/main/docs/adr/010-llm-guardrails-monitoring-poc.zh.md
- https://github.com/xingaiapp/xingai-tech-blog/blob/main/posts/2026-07-17-llm-guardrails-twelve-steps-not-tool-stickers.zh.md
- https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-07-17-llm-app-guardrails-plan-build-validate-operate.zh.md
