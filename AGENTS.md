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

## 提交约定

- 提交信息使用语义化格式：`<type>(<scope>): <subject>`，type 取 feat / fix / docs / chore / refactor 等。
- 一次提交聚焦一件事：新增技能、修改技能、仓库配置分开提交。
