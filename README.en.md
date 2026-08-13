# Read writers before writing fiction

> `learn-from-writers` makes the model learn from fiction written by actual people instead of imitating its own default AI prose.

[中文](README.md)

I built this because telling a model to “write like X” rarely makes it read X. It usually guesses at an author-shaped mood from memory and then writes the same familiar AI scene: atmosphere first, explained feelings, unusually tidy dialogue, and a final sentence that tells you what it all meant.

`learn-from-writers` changes the source of the writing. Before drafting, the model must find and read the relevant passage by the actual writer, including enough surrounding text to understand how the scene works. It then carries the writer's decisions about character, timing, point of view, information, and omission into a new scene. It does not copy sentences or paste a famous voice over your characters.

## What changes

| A normal writing prompt | This skill |
|---|---|
| Guesses an author's style from model memory | Opens and reads the relevant primary text |
| Writes default AI prose, then changes the vocabulary | Studies how a human writer moves the scene before building a new one |
| Treats adaptation as swapping names and images | Changes relationships, knowledge, medium, order, outcome, and aftermath |
| Uses a blacklist to remove “AI words” | Checks over-explanation, perfect communication, emotional stage directions, and moralizing endings |
| Keeps polishing a failed draft | Abandons the broken skeleton and rebuilds from verified facts |

The latest user-edited draft always outranks earlier model output. Material the user removed cannot quietly return under new wording.

## Use it for

- continuing, expanding, rewriting, or polishing fiction and narrative essays;
- scene design, dialogue, interiority, point of view, pacing, props, humor, and negative space;
- requests to study, reference, or adapt a specific author or work;
- long-running projects backed by existing drafts, Notion pages, timelines, or research;
- drafts that feel generic, over-explained, interview-like, falsely profound, or structurally inert.

It is not a general marketing, academic, technical-documentation, or social-media writing skill.

## Install

### Codex

```text
$skill-installer https://github.com/kiyuukinine/learn-from-writers
```

Or clone it into the user-level Skill location:

```bash
git clone https://github.com/kiyuukinine/learn-from-writers.git \
  "$HOME/.agents/skills/learn-from-writers"
```

Invoke it explicitly with `$learn-from-writers` in Codex CLI or the IDE extension.

### Claude Code

```bash
git clone https://github.com/kiyuukinine/learn-from-writers.git \
  "$HOME/.claude/skills/learn-from-writers"
```

## Design provenance

The repository description and presentation follow conventions observed in real public writing skills rather than an invented feature list:

- [great-writer](https://github.com/d-wwei/great-writer): research-driven positioning, mode routing, staged pipeline, and anti-AI-slop review;
- [paper-writing-skill](https://github.com/SNL-UCSB/paper-writing-skill): project context, stage gates, checklists, and independent review;
- [claude-writing-skills](https://github.com/xiaomoBoy/claude-writing-skills): narrow scope, explicit boundaries, composability, and real-tool workflows;
- [Creative-writing-skill](https://github.com/xbraindance/Creative-writing-skill): natural-language use, persistent project material, research grounding, and benefit-led README structure;
- [OpenAI Build skills](https://learn.chatgpt.com/docs/build-skills): description-based triggering, progressive disclosure, and representative prompt tests;
- [openai/plugins writing-skills](https://github.com/openai/plugins/tree/main/plugins/superpowers/skills/writing-skills): baseline-failure and regression-testing ideas for skill authoring.

Those projects do not endorse this repository. The distinctive workflow here is the combination of primary-text reading, source cards, six adaptation levels, material transformation, latest-edit authority, and mandatory skeleton resets.

See [DESIGN.md](DESIGN.md) for the complete comparison and [SKILL.md](SKILL.md) for the workflow.

## Limitations

- Strict source research requires access to the primary text; otherwise the workflow must disclose a lower-confidence mode.
- A skill can improve process discipline but cannot guarantee a model will match a particular author's literary ability.
- Public visibility is not a license. This repository currently includes no open-source license.
