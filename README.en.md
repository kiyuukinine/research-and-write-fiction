# research-and-write-fiction

> A research-driven fiction-writing skill for Codex and Claude: primary-text reading, traceable literary adaptation, project-aware revision, and structural anti-AI-slop checks.

[中文](README.md)

This Agent Skill is built for fiction and narrative prose. It combines primary-text research, project continuity, narrative-mechanism extraction, traceable adaptation, and staged revision in one workflow.

It is deliberately narrower than a universal writing toolkit. Its job is not to make a model produce prettier sentences by default. Its job is to stop prose generation until the current draft, character causality, scene movement, and—when requested—the actual literary source have been established.

## Core advantages

1. **Primary text before imitation.** Search snippets, summaries, reviews, and model memory may locate a passage, but they do not count as reading it.
2. **Mechanisms before wording.** Sources are analyzed at six levels: quotation, syntax/rhythm, paragraph movement, scene mechanism, macro structure, and negative space.
3. **Latest user edits outrank stale drafts.** A five-column fact ledger tracks known, inferable, unknown, forbidden, and unverified material.
4. **Structural anti-AI review.** The workflow checks causality, information distribution, scene change, dialogue, and paragraph function before lexical cleanup.
5. **Forced rebuild after structural failure.** Repeated errors or invalid premises trigger a new skeleton instead of another local polish pass.

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
$skill-installer https://github.com/kiyuukinine/research-and-write-fiction
```

Or clone it into the user-level Skill location:

```bash
git clone https://github.com/kiyuukinine/research-and-write-fiction.git \
  "$HOME/.agents/skills/research-and-write-fiction"
```

Invoke it explicitly with `$research-and-write-fiction` in Codex CLI or the IDE extension.

### Claude Code

```bash
git clone https://github.com/kiyuukinine/research-and-write-fiction.git \
  "$HOME/.claude/skills/research-and-write-fiction"
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
