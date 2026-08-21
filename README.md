# AI 技术笔记

面向 Agent 底层逻辑与 LangGraph 工作流的学习笔记。仓库配置了两个 Cursor 工作流：**笔记体例优化（Command）** 与 **自动提交推送（Skill）**。

请在 Cursor 中打开本仓库**根目录**（含 `.cursor/` 的那一层）。只打开子目录时，Command / Skill 可能不会出现。

## 目录结构

```text
AI/
├── README.md
├── Agent底层逻辑/           # Agent 运行时、工具调用、消息循环等
├── LangGraph工作流开发/     # 状态图、节点、边与工作流编排
├── .cursor/
│   ├── commands/
│   │   └── optimize-note.md # 笔记体例优化
│   └── skills/
│       └── auto-commit/     # 自动提交并推送
└── .gitignore
```

建议阅读顺序：`Agent底层逻辑` → `LangGraph工作流开发`。

### Agent底层逻辑

Agent 运行时与核心机制（笔记待补充）。

### LangGraph工作流开发

LangGraph 状态图与工作流编排（笔记待补充）。

---

## 1. 笔记体例优化（Command）

| 项 | 说明 |
|----|------|
| 类型 | Cursor **Command**（不是 Skill / Rule） |
| 文件 | `.cursor/commands/optimize-note.md` |
| 聊天触发 | `/optimize-note` |

### 做什么

把指定笔记改成与已优化样本一致的体例，并统一代码格式：

- 以同目录已优化笔记为锚点，不另发明体例
- **不补语言类比**，不补对照侧代码
- **代码缩进统一为 2 空格**，去掉 Tab，不混用 4 空格
- 去掉多余的 `---` 章节分隔线；连续空行默认压成 1 个
- 保留原有章节逻辑与练习，不删减教学内容

### 怎么用

1. 打开 Agent / Chat
2. 输入 `/`，选择 `optimize-note`
3. `@` 要优化的笔记后回车，例如：

```text
/optimize-note @Agent底层逻辑/01. 示例.md
```

可一次多个：

```text
/optimize-note @Agent底层逻辑/01. a.md @LangGraph工作流开发/02. b.md
```

Agent 会**直接改文件**，不只输出 Diff。

### 改规范

编辑 `.cursor/commands/optimize-note.md`，保存后下次 `/optimize-note` 即生效。

---

## 2. 自动提交并推送（Skill）

| 项 | 说明 |
|----|------|
| 类型 | Cursor **Skill** |
| 文件 | `.cursor/skills/auto-commit/SKILL.md` |
| 触发话术 | `提交` / `commit` / `自动提交` / `帮我提交` |

### 做什么

用户明确要求提交时，Agent 会：

1. 查看 `git status` / `diff` / 近期 commit 风格
2. 按 **Conventional Commits** 起草中文说明并 `commit`
3. **默认 `git push` 到 `origin`**（首次分支用 `git push -u origin HEAD`）
4. 回报 commit message、涉及文件、push 结果

未明确要求提交时，**不会**自动 commit / push。

### Commit message 格式

```text
<type>(<scope>): <中文简述>

<可选正文：1～2 句说明 why，中文>
```

常用 `type`：

| type | 用途 |
|------|------|
| `docs` | 笔记、说明、示例（本仓库默认） |
| `fix` | 纠正错误内容或错误示例 |
| `refactor` | 结构调整、体例统一 |
| `chore` | `.cursor`、`.gitignore` 等配置 |
| `feat` | 新增一整篇笔记或新主题 |

### 推送规则

- 提交成功后**默认 push**，不必再单独说 push
- 说「只提交不推送 / 不要 push」时跳过 push
- 不 force push；不改 git config；不提交 `.env` 等密钥文件

### 改行为

编辑 `.cursor/skills/auto-commit/SKILL.md` 即可。
