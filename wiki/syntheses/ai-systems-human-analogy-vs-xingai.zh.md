# 综合:「AI Systems: A Human Analogy」vs XingAI 任务地图

English: [ai-systems-human-analogy-vs-xingai.md](ai-systems-human-analogy-vs-xingai.md)

Aiswarya Venkitesh 海报:**把 AI 想成人的身体**——LLM=大脑、RAG=大脑+书、AI Agent=大脑+手、MCP=神经系统/「连接一切的基础层」。画框图有作者关注号召。第三方原图仅作 **raw 参考**。wiki **只嵌入 XingAI 纠正后地图**:

![XingAI 地图 — LLM/RAG/Agent/MCP 作为可组合任务并带闸门;不是身体器官](../assets/ux/ai-systems-human-analogy/xingai-map.png)

素材:`raw/external/2026-07-19-ai-systems-human-analogy/`(`verified: partial`)。

## 已知

- **海报四行(视觉):** 上述隐喻;MCP「Connects everything / Foundation connecting layer」。引用 `assets/aiswarya-venkitesh-human-analogy-reference.png`、画框 `assets/aiswarya-venkitesh-frame-reference.png` 与 `notes.md`。
- **方向重叠:** LLM 生成;RAG 加外部知识;Agent 用工具/记忆行动;MCP 关乎连接能力——对初学者标签友好。引用第 [02](../courses/02-rag-knowledge-systems.zh.md)–[04](../courses/04-mcp-interoperability.zh.md) 课。
- **XingAI 已拒绝 MCP/RAG/Skills 的对等「vs」栏:**[mcp-vs-rag-vs-skills](mcp-vs-rag-vs-skills.zh.md)。MCP≠A2A:[mcp-vs-a2a-vs-acp](mcp-vs-a2a-vs-acp.zh.md)。

## 缺失(海报没有 — XingAI 地图有)

- RAG:排序前 ACL、引用、忠实度评测。
- Agent:Validate → Approve/Execute、硬停止、HITL——不是自由的手。
- MCP:双墙;**不是** LLM/RAG 的基础;对等跳 → A2A。
- LLM:模型外的 eval/grounding——不是产品的「核心智能」。
- Ledger / 不可信工具与 RAG 文本攻击面(仍偏薄——开放)。

## 需重新思考

- **身体类比会藏住控制面。** 器官不需要 OAuth audience;工具跳需要。
- **MCP 当「神经系统」过度宣称。** 公开 A2A 文档与第 04 课把 MCP 当作 agent↔tool;说它是连接*一切*的基础,会把对等智能体、RAG 管线与鉴权压成一张贴纸。
- **用「大脑」称呼 LLM 抬高了模型。** 产品决策还要检索策略 + 门控行动 + ledger——见地图上的 generator 卡片。

## 争议(保持开放)

| 问题 | 海报倾向 | XingAI 公开倾向 | 状态 |
|---|---|---|---|
| 身体隐喻适不适合教学? | 中心框架 | 直觉可选;作架构不安全 | ADR 倾向任务 + 闸门 |
| MCP 是不是「基础」? | 是 | 对**工具访问**基础,不是 RAG/LLM 存在的前提 | 倾向收窄表述 |
| Agent = 手? | 是 | 没有 Validate→Execute 的手正是第 03 课点名的失败模式 | 倾向门控 loop |

## 待证

- 该图的规范帖 URL。
- 是否有更长帖文软化「nervous system / foundation」(仅有截图)。

## 怎么用

- 面试追问:「去掉身体部位重画;给 MCP 加墙、给 Agent 加停止。」
- 不要把 Aiswarya PNG 嵌进 wiki 教学页。

## 来源

`raw/external/2026-07-19-ai-systems-human-analogy/`;第 02–05 课;[agent-governance](../concepts/agent-governance-and-mcp.zh.md);兄弟综合 mcp-vs-rag-vs-skills / mcp-vs-a2a-vs-acp。`verified: partial`。
