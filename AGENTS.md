# AGENTS.md

本仓库是一个 Agent Skills 集合，用 `npx skills` 安装。此文件记录编写与维护技能时的长期约定。

## 仓库约定

- 每个技能放在 `skills/<skill-name>/` 下，入口固定为 `SKILL.md`。
- 技能目录名必须与 `SKILL.md` frontmatter 的 `name` 字段一致。
- `name` 使用小写英文与连字符（kebab-case）。
- `description` 用一句话说明技能用途与触发场景，供助手判断何时加载。
- 技能可附带 `scripts/`（辅助脚本）和 `references/`（参考文档）。
- 新增技能后在 `README.md` 的技能列表中登记。

## SKILL.md 结构

```markdown
---
name: <skill-name>
description: <用途与触发场景>
---

# <标题>

## 适用场景
## 执行步骤
## 禁止事项
```

正文按需组织，保持步骤可执行、边界清晰。

## SKILL.md 编写要点

- **保持精简**：`SKILL.md` 建议控制在 500 行以内，过长时把细节拆到 `references/` 或写进 `scripts/`。
- **描述要具体**：`description` 决定技能何时被加载，写清触发场景与关键词，不要泛泛而谈。
- **渐进式披露**：`SKILL.md` 只放主线流程，需要时才用相对路径引用 `references/`、`scripts/` 里的内容。
- **能用脚本就别内联**：把需要执行的逻辑写进 `scripts/`，脚本本身不占上下文，只有输出会进上下文。
- **引用只写一层**：从 `SKILL.md` 直接链到支撑文件，不要让文件之间再层层引用。

## 脚本约定

- Shell 脚本用 `#!/bin/bash` 并以 `set -e` 开头；Node 脚本用 `#!/usr/bin/env node` 且后缀为 `.mjs`。
- 状态信息写到 stderr，机器可读结果（JSON 等）写到 stdout。
- 用相对路径引用脚本，例如 `node scripts/xxx.mjs`。

## 分发与安装

对外说明安装方式：

```bash
# 安装全部技能
npx skills add shijianjs/dev-agent-skills

# 只安装某个技能
npx skills add shijianjs/dev-agent-skills --skill <skill-name>
```

## 提交约定

- 提交信息使用语义化格式：`<type>(<scope>): <subject>`，type 取 feat / fix / docs / chore / refactor 等。
- 一次提交聚焦一件事：新增技能、修改技能、仓库配置分开提交。
