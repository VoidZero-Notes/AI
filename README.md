# AI 技术笔记

面向 Agent 底层逻辑、LangGraph 工作流与 LangChain Agent 工程的学习笔记。仓库配置了两个 Cursor 工作流：**笔记体例优化（Command）** 与 **自动提交推送（Skill）**。

请在 Cursor 中打开本仓库**根目录**（含 `.cursor/` 的那一层）。只打开子目录时，Command / Skill 可能不会出现。

## 目录结构

```text
AI/
├── README.md
├── Agent底层逻辑/           # 已完成：从模型到 Agent 运行单元
├── LangGraph/               # 已完成：状态图、节点、边与工作流编排
├── LangChain+DeepAgent/     # 已完成：create_agent 与 Agent 工程
├── .cursor/
│   ├── commands/
│   │   └── optimize-note.md # 笔记体例优化
│   └── skills/
│       └── auto-commit/     # 自动提交并推送
└── .gitignore
```

建议阅读顺序：`Agent底层逻辑` → `LangGraph` → `LangChain+DeepAgent`。三条主线均已完成。

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

### LangGraph（已完成）

| # | 笔记 |
|---|------|
| 01 | [langgraph核心概念](LangGraph/01.%20langgraph核心概念.md) |
| 02 | [模型](LangGraph/02.%20模型.md) |
| 03 | [消息](LangGraph/03.%20消息.md) |
| 04 | [Reducer](LangGraph/04.%20Reducer.md) |
| 05 | [Agent Server](LangGraph/05.%20Agent%20Server.md) |
| 06 | [超步](LangGraph/06.%20超步.md) |
| 07 | [线程和检查点](LangGraph/07.%20线程和检查点.md) |
| 08 | [工具节点](LangGraph/08.%20工具节点.md) |
| 09 | [Mock Model](LangGraph/09.%20Mock%20Model.md) |
| 10 | [模型配置的动态切换](LangGraph/10.%20模型配置的动态切换.md) |
| 11 | [RunnableConfig](LangGraph/11.%20RunnableConfig.md) |
| 12 | [Runtime](LangGraph/12.%20Runtime.md) |
| 13 | [Assistant API](LangGraph/13.%20Assistant%20API.md) |
| 14 | [Thread API](LangGraph/14.%20Thread%20API.md) |
| 15 | [Run API](LangGraph/15.%20Run%20API.md) |
| 16 | [Cron API](LangGraph/16.%20Cron%20API.md) |
| 17 | [协议与运维](LangGraph/17.%20协议与运维.md) |
| 18 | [子图](LangGraph/18.%20子图.md) |
| 19 | [时间旅行](LangGraph/19.%20时间旅行.md) |
| 20 | [容错机制](LangGraph/20.%20容错机制.md) |
| 21 | [Command](LangGraph/21.%20Command.md) |
| 22 | [中断](LangGraph/22.%20中断.md) |
| 23 | [人在回路](LangGraph/23.%20人在回路.md) |
| 24 | [动态扇出](LangGraph/24.%20动态扇出.md) |
| 25 | [事件流](LangGraph/25.%20事件流.md) |
| 26 | [Store](LangGraph/26.%20Store.md) |
| 27 | [长期记忆](LangGraph/27.%20长期记忆.md) |
| 28 | [A2A 协议](LangGraph/28.%20A2A%20协议.md) |
| 29 | [Agent部署](LangGraph/29.%20Agent部署.md) |

### LangChain + DeepAgent（已完成）

在 LangGraph 图之上用 `create_agent` 与 Deep Agents 落地可 `invoke` 的 Agent，覆盖中间件、文件系统与沙箱、人在回路、Skills 与 MCP、记忆与上下文压缩、多智能体编排，以及身份认证、授权与资源隔离。

| # | 笔记 |
|---|------|
| 01 | [认识 Agent](LangChain+DeepAgent/01.%20认识%20Agent.md) |
| 02 | [结构化输出](LangChain+DeepAgent/02.%20结构化输出.md) |
| 03 | [中间件](LangChain+DeepAgent/03.%20中间件.md) |
| 04 | [动态提示词与动态模型](LangChain+DeepAgent/04.%20动态提示词与动态模型.md) |
| 05 | [预置中间件](LangChain+DeepAgent/05.%20预置中间件.md) |
| 06 | [DeepAgent](LangChain+DeepAgent/06.%20DeepAgent.md) |
| 07 | [文件系统工具](LangChain+DeepAgent/07.%20文件系统工具.md) |
| 08 | [沙箱](LangChain+DeepAgent/08.%20沙箱.md) |
| 09 | [实现服务端CodingAgent](LangChain+DeepAgent/09.%20实现服务端CodingAgent.md) |
| 10 | [HITL中间件](LangChain+DeepAgent/10.%20HITL中间件.md) |
| 11 | [文件操作权限](LangChain+DeepAgent/11.%20文件操作权限.md) |
| 12 | [后端路由](LangChain+DeepAgent/12.%20后端路由.md) |
| 13 | [多模态消息](LangChain+DeepAgent/13.%20多模态消息.md) |
| 14 | [Skills 中间件](LangChain+DeepAgent/14.%20Skills%20中间件.md) |
| 15 | [MCP 工具注入](LangChain+DeepAgent/15.%20MCP%20工具注入.md) |
| 16 | [Memory 中间件](LangChain+DeepAgent/16.%20Memory%20中间件.md) |
| 17 | [上下文压缩](LangChain+DeepAgent/17.%20上下文压缩.md) |
| 18 | [先计划再行动](LangChain+DeepAgent/18.%20先计划再行动.md) |
| 19 | [验收和评审](LangChain+DeepAgent/19.%20验收和评审.md) |
| 20 | [解释器](LangChain+DeepAgent/20.%20解释器.md) |
| 21 | [多智能体](LangChain+DeepAgent/21.%20多智能体.md) |
| 22 | [SubAgent](LangChain+DeepAgent/22.%20SubAgent.md) |
| 23 | [Handoff模式](LangChain+DeepAgent/23.%20Handoff模式.md) |
| 24 | [路由模式](LangChain+DeepAgent/24.%20路由模式.md) |
| 25 | [身份认证](LangChain+DeepAgent/25.%20身份认证.md) |
| 26 | [授权](LangChain+DeepAgent/26.%20授权.md) |
| 27 | [资源隔离](LangChain+DeepAgent/27.%20资源隔离.md) |

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
- **书面语**：笔记正文与完成后的结论使用专业技术书面语，将「吃」「收」等口语改为规范术语
- **不补语言类比**，不补对照侧代码
- **代码缩进统一为 2 空格**，去掉 Tab，不混用 4 空格
- 去掉多余的 `---` 章节分隔线；连续空行默认压成 1 个
- 保留原有章节逻辑与练习，不删减教学内容

### 怎么用

1. 打开 Agent / Chat
2. 输入 `/`，选择 `optimize-note`
3. `@` 要优化的笔记后回车，例如：

```text
/optimize-note @LangChain+DeepAgent/01. 认识 Agent.md
```

可一次多个：

```text
/optimize-note @LangChain+DeepAgent/01. 认识 Agent.md @LangGraph/02. 模型.md
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
