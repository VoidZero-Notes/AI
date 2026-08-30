# AI 技术笔记

面向 Agent 底层逻辑与 LangGraph 工作流的学习笔记。仓库配置了两个 Cursor 工作流：**笔记体例优化（Command）** 与 **自动提交推送（Skill）**。

请在 Cursor 中打开本仓库**根目录**（含 `.cursor/` 的那一层）。只打开子目录时，Command / Skill 可能不会出现。

## 目录结构

```text
AI/
├── README.md
├── Agent底层逻辑/           # 已完成：从模型到 Agent 运行单元
├── LangGraph工作流开发/     # 待写：状态图、节点、边与工作流编排
├── .cursor/
│   ├── commands/
│   │   └── optimize-note.md # 笔记体例优化
│   └── skills/
│       └── auto-commit/     # 自动提交并推送
└── .gitignore
```

建议阅读顺序：`Agent底层逻辑` → `LangGraph工作流开发`。

### Agent 底层逻辑（已完成）

| # | 笔记 |
|---|------|
| 01 | [AI的分类与底层逻辑](Agent底层逻辑/01.%20AI的分类与底层逻辑.md) |
| 02 | [神经网络基础](Agent底层逻辑/02.%20神经网络基础.md) |
| 03 | [词元与分词](Agent底层逻辑/03.%20词元与分词.md) |
| 04 | [Transformer](Agent底层逻辑/04.%20Transformer.md) |
| 05 | [Ollama](Agent底层逻辑/05.%20Ollama.md) |
| 06 | [系统提示词](Agent底层逻辑/06.%20系统提示词.md) |
| 07 | [会话](Agent底层逻辑/07.%20会话.md) |
| 08 | [Tool Calling](Agent底层逻辑/08.%20Tool%20Calling.md) |
| 09 | [工具注册与执行](Agent底层逻辑/09.%20工具注册与执行.md) |
| 10 | [ReAct](Agent底层逻辑/10.%20ReAct.md) |
| 11 | [Agent](Agent底层逻辑/11.%20Agent.md) |
| 12 | [Agent 搜索引擎](Agent底层逻辑/12.%20Agent%20搜索引擎.md) |
| 13 | [SKILL](Agent底层逻辑/13.%20SKILL.md) |
| 14 | [MCP](Agent底层逻辑/14.%20MCP.md) |
| 15 | [Skill VS MCP](Agent底层逻辑/15.%20Skill%20VS%20MCP.md) |
| 16 | [子代理](Agent底层逻辑/16.%20子代理.md) |
| 17 | [从 Prompt 到 Graph](Agent底层逻辑/17.%20从%20Prompt%20到%20Graph.md) |

### LangGraph 工作流开发（待写）

尚未开写。计划接在 17 之后，讲状态图、节点、边与工作流编排。

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
