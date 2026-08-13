# research-and-write-fiction

> A research-driven fiction-writing skill for Codex and Claude: primary-text reading, traceable literary adaptation, project-aware revision, and structural anti-AI-slop checks.

[English](README.en.md)

这是一个面向小说与叙事散文的 Agent Skill。它把外部原文查读、项目连续性、叙事机制拆解、实质化用和分轮返修放进同一条工作流，用来完成续写、重写、扩写、润色、场景重建与人物声线校准。

它的目标不是让模型“更会写漂亮句子”，而是限制模型在没有材料、没有人物因果、没有场面运动时直接生成一篇看似完整的小说。

## 为什么需要它

通用写作模型在文学任务中常见四类问题：

1. 只凭模型记忆模仿作家，实际没有查读原文；
2. 所谓“化用”只是替换人物、地点、意象和措辞；
3. 旧草稿污染新版本，用户删掉的解释和道具换一种写法又回来；
4. “去 AI 腔”退化为删词表，人物因果、信息分配和场面结构没有改变。

本 Skill 为这些问题设置了可执行的门槛：先锁定最新底稿，建立事实账本；需要外部参考时实际取得原文并建立来源卡；先设计无文采骨架，再按人物因果写初稿；反复失败时停止局部修补，从事实和场面功能重建。

## 它自己的优势

### 1. 原文先于仿写

评论、梗概、搜索摘要和模型记忆只能帮助定位。只有实际打开并阅读完整场面及必要前后文，才能声称“参考了某作品”。

### 2. 化用可追溯，也必须发生实质转换

来源被拆成六个层级：直接引用、句法节奏、段落运动、场面机制、宏观结构和负空间。每个来源先建立来源卡，再改变人物关系、知识分配、表达载体、视角、顺序、时间比例、结果或余波。只换姓名地点不算化用。

### 3. 用户最新编辑拥有最高权威

项目上下文使用“已知 / 可推导 / 未知 / 禁止 / 待核验”五栏账本。旧模型草稿不是事实；用户已经删除或否定的道具、解释、人物反应与情节支架不能靠改写重新出现。

### 4. 反 AI 从结构开始

Skill 先检查人物欲望、知识差、场面前后变化、段落功能、对话错位和心理重复，再处理词句。它会拦截环境字幕、完美沟通、格言式段尾、自动治愈、通用道具等生成习惯，但不把文学质量简化成禁词数量。

### 5. 错误骨架不再局部抢救

同类错误被连续指出、事实理解错误、主要转折被否定或场面前后无变化时，旧骨架必须废弃。只保留核实事实和用户明确留下的句子，从新的场面性质变化重新设计。

## 适用范围

- 小说与叙事散文的续写、扩写、重写和润色；
- 场景、章节时序、对话、心理、视角、道具、幽默与留白；
- “参考某作家”“借鉴某作品”“化用这一场”的研究型写作；
- 依赖既有长篇正文、Notion 设定、历史地域职业资料的连续创作；
- 对普通、假深沉、问答化、过度解释或反复失效的草稿进行结构性返修。

不适用于营销文案、论文、技术文档、新闻摘要，也不会为纯错字和机械排版强制启动完整研究流程。

## 工作流

1. **路由与材料**：判定续写、扩写、重写、润色、诊断或研究化用，并锁定交付边界。
2. **事实账本与问题建模**：区分已知、未知和禁止项，把审美要求转成技术问题。
3. **查读与机制提取**：需要外部参考时读取原文上下文，建立来源卡和实质转换计划。
4. **无文采骨架**：设计进入、压力、微变、转折、变调、退出和余波。
5. **人物因果初稿**：先让人物自身成立，再迁移来源机制。
6. **分轮复查**：结构 → 人物 → 来源 → 声线 → 反 AI → 连续性 → 输出契约。

详细规则见 [SKILL.md](SKILL.md)，设计依据与借鉴边界见 [DESIGN.md](DESIGN.md)。

## 安装

### Codex

OpenAI 官方文档建议用 `$skill-installer` 从其他仓库安装 Skill：

```text
$skill-installer https://github.com/kiyuukinine/research-and-write-fiction
```

也可以手动克隆到用户级 Skill 目录：

```bash
git clone https://github.com/kiyuukinine/research-and-write-fiction.git \
  "$HOME/.agents/skills/research-and-write-fiction"
```

Codex CLI 或 IDE 中可以输入 `$research-and-write-fiction` 显式调用。

### Claude Code

```bash
git clone https://github.com/kiyuukinine/research-and-write-fiction.git \
  "$HOME/.claude/skills/research-and-write-fiction"
```

不同版本或客户端的 Skill 路径可能不同，请以各自当前文档为准。

## 使用示例

```text
使用 $research-and-write-fiction。
以我刚刚编辑后的正文为唯一底稿，不恢复旧版删掉的道具。
参考契诃夫处理尴尬重逢的场面机制，但不要模仿措辞。
先实际查读原文和上下文，给我一份带来源卡的研究稿。
```

```text
使用 $research-and-write-fiction。
这已经是第三版，前两版都把对话写成了采访。
不要继续修句子，废弃旧骨架；只保留我明确留下的事实，重写这一场。
最终只给净稿。
```

## 仓库结构

```text
.
├── SKILL.md
├── DESIGN.md
├── README.md
├── README.en.md
├── agents/
│   └── openai.yaml
├── assets/
│   └── icon.svg
└── references/
    ├── task-routing-and-output.md
    ├── project-context.md
    ├── source-research-and-adaptation.md
    ├── fiction-craft.md
    ├── revision-and-evaluation.md
    └── evaluation-cases.md
```

## 设计来源与致谢

简介中的 “research-driven”、分阶段 pipeline、清晰的适用边界、项目上下文、复查 gate 和回归测试，并不是凭空造出的宣传词，而是依据下列公开项目的实际组织方式重新组合，并只保留与本 Skill 功能相符的部分：

- [d-wwei/great-writer](https://github.com/d-wwei/great-writer)：research-driven、分模式路由、六阶段 pipeline、多轮 polish 与 anti-AI-slop 的仓库表达方式；
- [SNL-UCSB/paper-writing-skill](https://github.com/SNL-UCSB/paper-writing-skill)：project context、阶段门槛、分项 checklist、压缩与独立复查的设计；
- [xiaomoBoy/claude-writing-skills](https://github.com/xiaomoBoy/claude-writing-skills)：one skill, one job、明确 in-scope / out-of-scope、真实工具优先和可组合资源；
- [xbraindance/Creative-writing-skill](https://github.com/xbraindance/Creative-writing-skill)：自然语言调用、持续项目资料、研究基础和“为什么选择这个 Skill”的 README 结构；
- [OpenAI Build skills](https://learn.chatgpt.com/docs/build-skills)：基于 description 的触发、渐进式披露、按需 references 与代表性提示测试；
- [openai/plugins: writing-skills](https://github.com/openai/plugins/tree/main/plugins/superpowers/skills/writing-skills)：先观察失败、再写规则、最后做回归测试的 Skill 测试思路。

这些项目没有为本仓库背书。本 Skill 没有照搬它们的正文规则：它的独有部分是“文学原文查读—来源卡—六层化用—实质转换—用户最新编辑优先—错误骨架强制重建”这一整套小说工作流。

## 限制

- 只有在能取得原文时，才能完成严格的原文级研究；取不到时必须明确降级。
- Skill 提供方法和约束，不保证任何模型自动达到特定作家的文学水平。
- 来源卡和化用标记主要用于研究稿；公开成稿仍应遵守版权与合理引用边界。
- 当前仓库未附开源许可证；公开可见不等于获得复制、修改或再分发授权。
