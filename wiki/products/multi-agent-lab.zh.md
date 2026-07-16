# 产品:multi-agent-lab

English: [multi-agent-lab.md](multi-agent-lab.md)

**仓库:** [xingai-enterprise-ai-pocs](https://github.com/xingaiapp/xingai-enterprise-ai-pocs) · **状态:** 可运行 · 第 1 阶段 MVP

Orchestrator + 专家 agent(Research、Product、Tech、Critic)、模拟 MCP 工具、SQLite 执行轨迹、演示指标。几乎没有保险领域——故意如此。

## README 不会强调的

这是理赔 POC 往上贴肉的**平台骨架**。若直接跳到 workflow-v2,每个失败都像理赔 bug。从这里开始,才能在没有政策/结算噪音时看清交接、轨迹行与 agent 注册表。

轨迹行(`request_id`、agent、input、output、tool、duration)是[决策台账](xingai-engineering-system.zh.md)共享 schema 之前的*直觉*。第 05 课的规则——只为专业化、信任分离或并行才加 agent——是 Critic/Research 拆分究竟是正当还是演戏的评分标准。

## 关联

- [claims-multiagent-rag-poc](claims-multiagent-rag-poc.zh.md)(下一保真度台阶)、[第 05 课](../courses/05-agent-runtime-multi-agent.zh.md)
- [Claims POC 族](../syntheses/claims-poc-family-tradeoffs.zh.md)

## 来源

`raw/pocs/multi-agent-lab/README.md`, `architecture.md`
