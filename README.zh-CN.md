# Just-in-Time Research

[English](README.md) | **简体中文**

**让研究成为思考的一部分，而不是最终产物。**

Just-in-Time Research 是一个面向 Coding Agent 的可组合研究插件。它只在用户明确要求研究时介入，围绕当前任务中真正影响判断的不确定性展开调查，形成有证据支撑的理解与结论，再把这些认识带回正在进行的讨论、设计或实现。

仓库包含两个相互协作的 Skill：

- **`just-in-time-research`**：决定研究什么、需要多大广度与深度、如何管理证据和研究状态、何时扩展执行规模，以及何时结束研究并返回当前任务。
- **`zen-of-search`**：根据具体信息缺口，选择和组合当前环境中的搜索、检索、内容提取、代码仓库和浏览工具。

```text
当前任务或讨论
      ↓
用户显式调用 just-in-time-research
      ↓
识别真正影响决策的不确定性
      ↓
需要外部信息时使用 zen-of-search
      ↓
检查并验证证据
      ↓
更新理解并形成判断
      ↓
返回原始任务继续工作
```

## 为什么需要它

多数 Deep Research 系统面向一个终点式报告：

```text
研究问题 → 搜索 → 报告
```

本项目把研究视为任务过程中的中间认知操作：

```text
任务 → 不确定性 → 研究片段 → 更新判断 → 继续工作
```

目标不是穷尽所有资料，而是获得足够可靠的理解，从而改善用户下一步的判断或行动。

## 设计原则

- **手动激活。** `just-in-time-research` 只应在用户显式调用后运行。
- **面向决策。** 优先调查最可能改变最终答案的未知因素。
- **动态广度与深度。** 不预设固定来源数、查询数、研究轮数或 Agent 数量。
- **论断级证据。** 来源只有在能够支持、反驳或限定某项相关论断时才构成证据。
- **最小研究状态。** 保留当前理解和可回查证据，而不是完整执行轨迹。
- **弹性执行规模。** 默认使用最小可行系统，只在确有价值时外置状态或分派子 Agent。
- **不固定交付物。** 根据实际问题返回事实、解释、比较、判断、设计、实验建议或完整报告。
- **研究后继续工作。** 研究更新任务上下文，不自动把整个任务视为已经结束。

## 仓库结构

```text
.
├── .claude-plugin/
│   ├── plugin.json
│   └── marketplace.json
├── .codex-plugin/
│   └── plugin.json
├── .agents/plugins/
│   └── marketplace.json
├── skills/
│   ├── just-in-time-research/
│   │   ├── SKILL.md
│   │   ├── agents/openai.yaml
│   │   └── references/
│   │       ├── research-control.md
│   │       ├── research-state.md
│   │       ├── sources-and-evidence.md
│   │       └── deep-research.md
│   └── zen-of-search/
│       ├── SKILL.md
│       └── agents/openai.yaml
└── docs/
    └── architecture.md
```

仓库只有一份 canonical `skills/` 目录，由 Claude Code、Codex 和其他兼容 Agent Skills 的宿主共同使用。运行行为只维护一次；平台清单只负责发现、展示以及无需复制 Skill 内容即可表达的平台策略。reference 仅在当前研究片段确实需要时按需加载。`docs/` 面向人类维护者，不属于运行时协议。

## 安装

### Claude Code

将仓库添加为 Marketplace，并安装插件：

```text
/plugin marketplace add Ttungx/just-in-time-research
/plugin install just-in-time-research@just-in-time-research
```

显式调用研究 Skill：

```text
/just-in-time-research 深入研究这个架构是否应该使用 Temporal
```

Claude Code 与其他宿主直接加载同一份 `skills/`。`just-in-time-research` 的 Skill 指令中已经明确规定仅在用户显式调用时启用，不再维护 Claude 专用副本。

### Codex

支持插件 Marketplace 的较新 Codex 版本可使用：

```bash
codex plugin marketplace add Ttungx/just-in-time-research
codex plugin add just-in-time-research@just-in-time-research
```

显式调用 Skill：

```text
$just-in-time-research 深入研究这个架构是否应该使用 Temporal。
```

Codex 还会通过 `skills/just-in-time-research/agents/openai.yaml` 中的 `policy.allow_implicit_invocation: false` 在平台层面禁止隐式调用。

### 单独安装 Skill

支持 Agent Skills 目录格式的 Agent 可以直接安装任一目录：

```text
skills/just-in-time-research
skills/zen-of-search
```

仓库不捆绑也不强制依赖任何 MCP Provider。两个 Skill 会使用当前宿主已经提供的搜索、浏览器、代码仓库、文档、代码执行等能力。

## 两个 Skill 如何协作

`just-in-time-research` 负责认知与研究控制：

- 界定真实问题；
- 识别影响决策的关键未知；
- 选择扩展、深入、验证、综合或实验；
- 管理研究状态；
- 判断是否需要分派子 Agent；
- 形成适用于当前项目的判断；
- 在答案达到 decision-ready 时停止。

`zen-of-search` 负责信息获取策略：

- 识别问题需要怎样的检索形态；
- 根据实际能力选择主工具；
- 发现候选来源；
- 获取难以读取的内容；
- 只在不同阶段之间组合工具；
- 当继续搜索不再可能改变结论时停止。

两个 Skill 都不依赖某个固定 MCP Provider。当前环境中实际暴露的工具 schema 和能力始终是权威依据。

## 使用示例

```text
$just-in-time-research 比较这个仓库可采用的 durable execution 方案，并给出推荐。
```

```text
$just-in-time-research 验证这个库是否真的支持 README 中声称的行为。
```

```text
$just-in-time-research 研究这个尚未解决的设计问题，然后继续实现证据最充分的方案。
```

```text
$zen-of-search 找到这个 API 的权威来源和当前实现状态。
```

## 当前状态

仓库有意从纯 Skill 指令和 reference 体系开始，不包含自建搜索服务、数据库、状态机或强制脚本。只有当评估证明单靠指令无法解决某个具体问题时，才应增加新的基础设施。

## 许可证

MIT
