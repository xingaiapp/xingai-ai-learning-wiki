# 综合:MCP vs A2A vs ACP(智能体如何互相说话)

English: [mcp-vs-a2a-vs-acp.md](mcp-vs-a2a-vs-acp.md)

ByteByteGo 三栏海报 **MCP | A2A | ACP**(2026-07-19 用户附图)加上此前粘贴。第三方原图仅作 **raw 参考**,wiki **只嵌入 XingAI 纠正后地图**(评估 → 修正 → 补全 → 重绘):

![XingAI 地图 — 组合工具跳(MCP + 双墙)与对等跳(A2A + 信任);ACP 作谱系脚注](../assets/ux/mcp-vs-a2a-vs-acp/xingai-map.png)

素材:`raw/external/2026-07-19-mcp-vs-a2a-vs-acp/`(`verified: partial`)。

## 已知

- **海报(视觉,仅参考):** 三座等高塔——MCP host→client→server→DB/API/文件贴纸;A2A registry→Agent Card→Agent B +「需要更多信息」;ACP REST/manifest→同步/异步。页脚:ByteByteGo。引用 `raw/.../assets/bytebytego-mcp-a2a-acp-reference.png` 与 `notes.md` 评估。
- **粘贴分工:** 同类跳类型;称 ACP 已并入 A2A;生产上互补。引用 `content.md`。
- **公开 A2A 站点:** MCP 管工具、A2A 管对等体——互补而非竞争。引用 [a2a-protocol.org](https://a2a-protocol.org/dev/)。
- **XingAI 第 04 / 05 课:** MCP 是受治理的能力边界;仅在专业化 / 信任隔离 / 并行时加智能体。引用 [第 04 课](../courses/04-mcp-interoperability.zh.md)、[第 05 课](../courses/05-agent-runtime-multi-agent.zh.md)。
- **公开 POC 双墙 MCP:** scope + 独立业务策略。引用 [Agent 治理](../concepts/agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.zh.md)。
- 相邻「vs」翻车:[mcp-vs-rag-vs-skills](mcp-vs-rag-vs-skills.zh.md)。

## 缺失(海报没有 — XingAI 地图有)

- **MCP 双墙**在工具结果之前(OAuth/scope + 业务策略)。
- **对等信任闸门**(identity / audience / allowlist)在 Agent B 之前。
- **第 05 课 STOP**——何时*不要*加对等体;禁止循环委派。
- **ACP 降级**为谱系脚注(不是第三等高栏)。
- **Ledger / HITL**对高影响副作用(海报与地图都仍偏薄——开放)。
- **ACP→A2A 一手合并材料**尚未进 `raw/`。

## 需重新思考

- **「vs」+ 三塔是错框架。** 一个任务选*哪一种跳*;常常两种都要。XingAI 地图用 Compose → Tool hop → Peer hop 横带。
- **厂商贴纸 ≠ 架构。** PostgreSQL / GitHub / Drive / IDE logo 教的是购物清单,不是治理。
- **Agent Card 发现 ≠ 已授权动作。** 与第 04 课对 MCP token 点名的 confused-deputy 同类。
- **按海报把 ACP 与 A2A 并排上线**会冻结粘贴自己已说「已合并」的过渡态。

## 争议(保持开放)

| 问题 | 海报倾向 | XingAI 公开倾向 | 状态 |
|---|---|---|---|
| MCP 与 A2A 是替代吗? | 三栏暗示二选一 | 互补跳 + 墙 | 倾向组合 |
| 今天还该实现 ACP 吗? | 等高绿栏 | 脚注 / 合并谱系 | 一手文档入库前开放 |
| 走 A2A 线协议还是进程内 + MCP? | 暗示总有 registry/card | 公开 POC 强调 MCP + 可恢复工作流 | 开放 |
| Agent Card 能否取代网关白名单? | 注册表发现 | 企业侧仍要身份 + 白名单 | 开放 |

## 待证

- 该图的 ByteByteGo 规范帖 URL。
- LF/IBM ACP→A2A 一手公告 + 迁移指南入库。
- 是否有公开 XingAI 仓库暴露 A2A Agent Card(绘制时本 wiki 未找到)。
- 海报「Agent Registry」措辞与 well-known Agent Card URL 是否规范对齐。

## 怎么用

- 第 04↔05 课追问:从左到右走 XingAI 地图;若有人只背过 ByteByteGo 三塔,问墙画在哪里。
- 不要把 ByteByteGo PNG 嵌进产品或 wiki 教学页。

## 来源

`raw/external/2026-07-19-mcp-vs-a2a-vs-acp/`(粘贴 + ByteByteGo 参考 + `notes.md`);wiki 仅嵌入:`wiki/assets/ux/mcp-vs-a2a-vs-acp/xingai-map.png`;[a2a-protocol.org/dev](https://a2a-protocol.org/dev/);第 04/05 课;agent-governance + claims MCP 页。`verified: partial`。
