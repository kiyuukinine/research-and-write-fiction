# 设计依据、借鉴边界与独有能力

## 1. 为什么不是“再写一份提示词”

这个项目把成熟 Writing Skill 里反复出现的工程结构用于文学写作：

- description 负责准确触发；
- 主文件只保留边界、路由、阶段和门槛；
- references 按任务条件读取；
- 项目上下文约束跨会话连续性；
- 输出契约防止分析、研究笔记和净稿互相污染；
- 评测用例验证触发、边界和关键行为；
- 失败恢复规则阻止模型在错误骨架上无限润色。

这些结构不等同于文学方法本身。真正的文学方法仍需要从用户文本、实际原文和具体叙事问题中建立。

## 2. 公开 Skill 对照

| 项目 | 实际可见的设计 | 本项目借鉴 | 本项目没有照搬 |
|---|---|---|---|
| [great-writer](https://github.com/d-wwei/great-writer) | “research-driven”定位、模式路由、六阶段 pipeline、research gate、多轮 polish、anti-AI-slop | 明确阶段、门槛、反 AI 复查和能力导向简介 | 九种通用写作模式、句长统计、通用禁词表与读者 CTA |
| [paper-writing-skill](https://github.com/SNL-UCSB/paper-writing-skill) | project context、固定阶段、分节 rhetorical moves、mechanical/semantic gates、red-team、compression | 项目上下文模板、先骨架后正文、分轮 gate、可执行验收 | 论文结构、LaTeX 检查、领域作者 profile、自动独立审稿 |
| [claude-writing-skills](https://github.com/xiaomoBoy/claude-writing-skills) | one skill, one job、in/out scope、required reads、real tools、output contract | 单一任务边界、条件化读取、真实原文工具优先、输出契约 | 多 Skill 套件、网页发布与搜索 CLI |
| [Creative-writing-skill](https://github.com/xbraindance/Creative-writing-skill) | natural-language interface、persistent wiki、research foundation、benefit-led README、before/after | 自然语言触发、持续项目材料、研究依据和 README 的优势表达 | Verbalized Sampling、自动项目 wiki、随机多候选采样 |
| [OpenAI Build skills](https://learn.chatgpt.com/docs/build-skills) | description 触发、渐进式披露、Skill 目录标准、代表性测试提示 | description 前置触发词、按需 references、官方目录结构、触发回归测试 | 插件打包和连接器依赖 |
| [openai/plugins writing-skills](https://github.com/openai/plugins/tree/main/plugins/superpowers/skills/writing-skills) | baseline failure → rules → pass → refactor 的 Skill 测试思路 | 失败用例、边界用例和回归矩阵 | 将文学质量假装成完全可自动化的单一通过/失败指标 |

## 3. 本项目的独有组合

### A. 最新编辑权威

多数通用 Writing Skill 强调持久记忆，但文学项目真正危险的是“错误内容也被持久化”。本项目因此使用权威顺序和五栏事实账本：最新正文、用户项目资料和确认版本优先；旧助手草稿仅可作为待审材料。

### B. 来源卡

每个实际使用的文学片段必须记录场面前提、人物目标、知识差、压力、信息载体、微变、转折、退出状态、可迁移部分和过近风险。来源卡把“我参考了某作家”变成可核验步骤。

### C. 六层化用

化用被拆成：直接引用、句法节奏、段落运动、场面机制、宏观结构、负空间。层级越接近词句，越需要标记和谨慎；优先迁移场面、结构与负空间。

### D. 实质转换

只有改变关系、知识、载体、视角、顺序、时间、结果、余波或意象系统，才算化用。表面换皮不通过因果检验与声线检验。

### E. 结构性反 AI

反 AI 不是“少用某些词”，而是检查：

- 人物是否被模型自动写得善于沟通；
- 场面是否靠争吵、表白和身体反应制造廉价张力；
- 环境与道具是否自动字幕化情绪；
- 心理是否翻译潜台词；
- 段尾是否整齐总结意义；
- 每一段是否真实改变事实、判断、关系、节奏或余波。

### F. 强制重建

同类错误连续出现说明局部优化目标已经失效。此时 Skill 要求清空旧顺序，只保留核实事实与明确保留句，从“本场必须发生什么性质变化”重新建立骨架。

## 4. 为什么拆成多个 references

旧版把资料管理、查读、化用、场景、对话、反 AI 和验收全部放在一个长文件中，任何任务都要加载整份规范。新版根据公开 Skill 的渐进式披露和 required-reads 结构拆分为：

- `task-routing-and-output.md`：所有实质任务必读；
- `project-context.md`：连续项目与既有正文；
- `source-research-and-adaptation.md`：外部原文与化用；
- `fiction-craft.md`：正文生成和场景问题；
- `revision-and-evaluation.md`：返修、反 AI、连续性；
- `evaluation-cases.md`：只给维护者测试 Skill。

局部润色不必加载完整来源研究；单纯来源分析也不必读取所有场景技法。

## 5. 设计上的克制

- 不声称 Skill 能复制任何作家的天赋或声音；
- 不把“参考”包装成未经验证的版权豁免；
- 不用来源数量制造权威感；
- 不为每次写作强制浏览，用户明确要求纯自由创作时尊重边界；
- 不把主观文学判断伪装成完全机械评分；
- 不把评测表输出给只要正文的用户。

## 6. 简介的形成

仓库一句话简介采用公开 Writing Skill 常见的“定位 + 关键能力”句式：

> A research-driven fiction-writing skill for Codex and Claude: primary-text reading, traceable literary adaptation, project-aware revision, and structural anti-AI-slop checks.

其中：

- “research-driven” 与 “anti-AI-slop” 是对 [great-writer](https://github.com/d-wwei/great-writer) 仓库定位方式的明确借鉴；
- “for Codex and Claude” 依据多个跨客户端 Skill 的分发习惯，以及 OpenAI 官方的 Agent Skills 标准；
- 冒号后的四项不是宣传性形容词，而是本仓库已有文件和门槛能够逐项对应的能力。

因此，这句简介不是从空白处自由发挥，也没有直接复制某个项目的完整描述。
