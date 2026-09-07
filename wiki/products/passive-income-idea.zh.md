# 产品：XingAI 被动收入 Idea（`passive.xingai.app`）

English: [passive-income-idea.md](passive-income-idea.md)

公开的决策式每日 Idea 表面——面向既定操作者画像，每天只给 **1 个**个人被动收入/现金流 Idea，并配 FAQ/免责声明。本页依据**线上公开站点**与用户自有桌面截图，不镜像私有仓库。

**权威地址：** [https://passive.xingai.app/](https://passive.xingai.app/)  
**AEO：** [https://passive.xingai.app/llms.txt](https://passive.xingai.app/llms.txt)

## 它在主张什么（公开）

1. **决策卡，不是点子流** — 首页与 FAQ 强调“今日唯一值得动手的 Idea”，不是随机 tip 列表（`llms.txt` + FAQ）。
2. **Fail-closed 诚实** — FAQ：不保证收入；未知标 `未核实`；投资收益与商业收入分开。
3. **不是 Opportunity Radar** — Radar 选 XingAI *产品* 立项；本报告为既定画像选 *个人* 财富积累 Idea（FAQ）。
4. **语言 en / zh / ko** — `llms.txt` 声明；公开 JSON 含 `locales.en|zh|ko`（2026-09-07 快照）。
5. **交付工艺** — FAQ + `llms.txt`：邮件 Summary + A4 PDF；站点亦暴露 `pdf_url` 与归档向数据路径。

## UX（桌面）

深色 Today 导航（顶栏 + 侧栏 + Idea 面板）。2026-09-06 截图反映后续布局/语言打磨前的状态：

![桌面 Today — 双栏 Idea 面板（深色）](../assets/ux/passive-income-idea/desktop-today-two-column.dark.png)

![桌面 Today — EN 壳 + 中文 Idea 正文（深色）](../assets/ux/passive-income-idea/desktop-today-locale-mix.dark.jpg)

**截图能证明：** XingAI chrome 模式在场；Idea 面板是决策面。  
**截图不能证明：** worker 调度、邮件实发成功，或当晚每个语言包已接到 UI（图中可见 EN 壳 + 中文正文）。

## 已知

- 线上 FAQ 与 `llms.txt` 与“教育/非建议”定位一致（`raw/external/2026-09-07-passive-income-idea/`）。
- 2026-09-07 的 `latest-idea.json`：`is_mock: false`，含 `en`/`zh`/`ko` locales、公开来源 URL、`/reports/...pdf`（同 raw 包）。
- 桌面 UX 截图为用户自有，已快照在 `raw/external/2026-09-07-passive-income-idea/assets/ux/`。

## 缺失

- 实现仓库是否**公开**未在本会话确认（`gh` 查询失败）——故不引用私有 ADR。
- 移动端 ~375px、浅色主题成对截图；Archive / How 页截图。
- Resend 实发邮件的证据（站点只描述工艺）。
- 认证故事（公开 FAQ 未声称）。

## 需重新思考

- 若“研究”主要是目录挑选 + URL 可达性探测，却对外叫成市场研究，可能相对 Course 06/07 证据标准过满 — 公开 JSON 的 probe 备注偏可达性，不是市场规模证明。
- 截图里的 EN 壳 + 中文正文，会削弱 `llms.txt` 的三语承诺 — AEO 语言声明应视为**意图**，以 UI 实测为准。

## 争议

- **PDF/邮件（中文）** 是否仍是主决策产物、站点只是镜像，还是多语言网页面板应升为主？公开 FAQ 仍强调邮件+PDF；站点已展示完整 Idea 卡。
- “每天 1 个 Idea”的连续性，在操作者本人也是 XingAI builder 时，如何与 Opportunity Radar 的产品下注划清（FAQ 有线，重叠风险仍在）。

## 待证

- `xingai-passive-income-ideas` 是否 GitHub 公开？（本会话检查受阻。）
- 0.2.5 类部署后，切换 EN/zh/ko 是否改变 Idea **正文**（不只是 chrome）？需新截图对。
- 收入区间是否可能被标为已核实，还是策略上永远估计/`未核实`？

## 故意跳过

私有 ADR、operator YAML、worker 源码、Resend 密钥与未公开路线图。

## 来源

- `raw/external/2026-09-07-passive-income-idea/`（`SOURCE.md`、`content.md`、`llms.txt`、`latest-idea.json`、UX 资源）
- 线上：[passive.xingai.app](https://passive.xingai.app/)、[llms.txt](https://passive.xingai.app/llms.txt)
- 相关概念（仅模式呼应）：[decision-ledger-pattern](../concepts/decision-ledger-pattern.zh.md)、[cache-first-llm-architecture](../concepts/cache-first-llm-architecture.zh.md) — **不要**把本产品页当作这些 schema 已在此实现的证据。
