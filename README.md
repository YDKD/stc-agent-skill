# stc Agent Skill

[English](#english) · [中文](#中文)

Official public distribution repository for the Agent Skill bundled with [skill-tui-cli](https://www.npmjs.com/package/skill-tui-cli).

This repository contains only the public Agent Skill and its documentation. The private stc CLI source code is not mirrored here.

## English

### Install with stc (recommended)

```bash
npx skill-tui-cli agent install --agent codex
```

Supported targets: `codex`, `agents`, `claude`, and `cursor`.

Compatible GitHub Skill installers may also install this repository directly:

```bash
npx skills add YDKD/stc-agent-skill
```

The Skill guides an AI agent through project analysis, recommendation, read-only inspection, explicit install planning, and user-approved installation with stc.

## 中文

这是 `skill-tui-cli` 内置 Agent Skill 的官方公开分发仓库。

本仓库只包含公开 Skill 及其说明，不会同步私有的 stc CLI 源代码。

### 使用 stc 安装（推荐）

```bash
npx skill-tui-cli agent install --agent codex
```

支持 `codex`、`agents`、`claude` 和 `cursor`。

兼容 GitHub Skill 仓库的安装器也可以直接安装：

```bash
npx skills add YDKD/stc-agent-skill
```

该 Skill 会指导 AI 使用 stc 完成项目分析、Skill 推荐、只读检查、安装计划生成，以及经过用户明确授权后的安装。

## Managed content

The private stc release workflow manages only:

`skills/manage-project-skills-with-stc/`

Root-level repository files remain independently maintained.
