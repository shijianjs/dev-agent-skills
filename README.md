# dev-agent-skills

我自用的 [Agent Skills](https://agentskills.io/) 集合，可用于 Claude Code、Codex、Cursor、OpenCode 等支持 Agent Skills 的编码助手。

## 安装

用 [`npx skills`](https://github.com/vercel-labs/skills) 从本仓库安装：

```bash
# 安装全部技能
npx skills add shijianjs/dev-agent-skills

# 只安装指定技能
npx skills add shijianjs/dev-agent-skills --skill long-task-tracking

# 安装前先列出仓库里有哪些技能
npx skills add shijianjs/dev-agent-skills --list
```

## 技能列表

| 技能 | 说明 |
| --- | --- |
| [ktjs-type-mapping](skills/ktjs-type-mapping/SKILL.md) | 把上游 npm 包的 TypeScript 声明翻译成 Kotlin/JS `external` 声明时的建模规范（kotlin-wrappers 风格），供 `ktjs-*` 各 wrapper 仓库共用。 |
| [long-task-tracking](skills/long-task-tracking/SKILL.md) | 为跨多个 AI 对话上下文的长期 Git 开发任务建立和维护持久化进度清单，确保任务范围、完成状态、排除事项和后续工作可以准确恢复。 |
| [intellij-mcp-plugins](skills/intellij-mcp-plugins/SKILL.md) | 用脚本或命令行调用 IntelliJ IDEA 的 MCP server，查类型继承树（父类链 + 子实现）、实现列表与覆盖方法（Java / Kotlin/JVM / Kotlin/JS），含通用 MCP 客户端与继承树渲染脚本。 |
| [ui-code-style](skills/ui-code-style/SKILL.md) | 原生 DOM 写 UI 的组织与样式规范：按业务语义切分（可递归）而非技术类型、保留模式而非 state→render、样式优先内联且 CSS 不堆成大字符串、`adoptedStyleSheets` 只给真正共享、图标用 `iconify-icon`；含 TS 与 Kotlin/JS 两套落地写法。 |

## 仓库结构

```text
dev-agent-skills/
├── skills/
│   └── <skill-name>/
│       ├── SKILL.md        # 技能说明（必需，含 YAML frontmatter）
│       ├── scripts/        # 辅助脚本（可选）
│       └── references/     # 参考文档（可选）
├── AGENTS.md               # 本仓库的技能编写约定
├── LICENSE                 # MIT
├── README.md
├── .gitattributes          # 统一换行符为 LF
└── .gitignore
```

每个技能一个子目录，目录名与 `SKILL.md` frontmatter 中的 `name` 保持一致。

## 新增技能

1. 在 `skills/` 下新建目录 `skills/<skill-name>/`。
2. 编写 `SKILL.md`，开头为 YAML frontmatter：

   ```yaml
   ---
   name: <skill-name>
   description: <一句话说明技能用途与触发场景>
   ---
   ```

3. 正文用清晰的步骤描述工作流程，按需补充 `scripts/` 或 `references/`。
4. 在 README 的技能列表中登记。
5. 提交并推送。

## License

[MIT](LICENSE) © 2026 shijianjs
