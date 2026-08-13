# 先读作家，再写小说

> `learn-from-writers`：让模型从真人作品里学写法，而不是继续模仿自己的 AI 文风。

[English](README.en.md)

我做这个 Skill，是因为“参考某某作家写一段”通常没有什么用。模型多半不会去读那篇作品，只会凭记忆猜一个模糊的“作家风格”，最后还是用自己最熟悉的方式写：气氛先行、心理解释、整齐对话，再来一句像结论的段尾。

`learn-from-writers` 改的是参考来源。写之前，它要先把真正的原文找出来，读具体场景及其前后文，看作家怎样处理人物、停顿、视角、信息和省略；回到你的小说以后，借的是这些处理方法，不是作品里的句子，也不是模型想象出来的“文学感”。

## 它到底改了哪一步

| 直接让模型写 | 使用这个 Skill |
|---|---|
| 凭模型记忆猜测“某作家的风格” | 实际打开作品，阅读相关场景和必要上下文 |
| 先生成一篇默认 AI 小说，再替换几个词 | 先看真人作家怎样组织人物、节奏和信息，再设计自己的场面 |
| 把化用理解成换姓名、地点和意象 | 改变人物关系、知识差、表达载体、顺序、结果和余波 |
| 用禁词表消除 AI 腔 | 检查人物是否被写得过分会沟通、心理是否替潜台词作了解释、段尾是否总在总结意义 |
| 在已经失败的稿子上反复润色 | 同类问题继续出现时，保留事实，放弃旧骨架重写 |

这里说的“向作家学习”不是复制某个人的声音。Skill 会区分句子、节奏、段落运动、场面结构和留白；越靠近原文措辞，越谨慎。真正优先借鉴的是：一场戏为什么这样推进，谁知道什么，谁故意不说，转折在哪里发生，结束后有什么没有被解释。

它也记得当前作品是谁的。用户最新修改的正文优先于模型旧稿；删掉的道具、解释和人物反应，不能换种说法重新混回来。

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
$skill-installer https://github.com/kiyuukinine/learn-from-writers
```

也可以手动克隆到用户级 Skill 目录：

```bash
git clone https://github.com/kiyuukinine/learn-from-writers.git \
  "$HOME/.agents/skills/learn-from-writers"
```

Codex CLI 或 IDE 中可以输入 `$learn-from-writers` 显式调用。

### Claude Code

```bash
git clone https://github.com/kiyuukinine/learn-from-writers.git \
  "$HOME/.claude/skills/learn-from-writers"
```

不同版本或客户端的 Skill 路径可能不同，请以各自当前文档为准。

## 使用示例

```text
使用 $learn-from-writers。
以我刚刚编辑后的正文为唯一底稿，不恢复旧版删掉的道具。
参考契诃夫处理尴尬重逢的场面机制，但不要模仿措辞。
先实际查读原文和上下文，给我一份带来源卡的研究稿。
```

```text
使用 $learn-from-writers。
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

下面这些项目帮助我确定怎样把它做成一个真正可调用、可维护的 Skill：哪些规则应放在主文件，哪些资料按需读取，怎样写边界、阶段和测试。它们提供的是 Skill 的组织方法，不是这套小说写法本身。

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
