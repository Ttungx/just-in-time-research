# Just-in-Time Research

**English** | [简体中文](README.zh-CN.md)

**Research as part of thinking, not the end product.**

Just-in-Time Research is a composable research plugin for coding agents. It activates when the user explicitly requests research, reduces the uncertainty that matters to the current task, forms an evidence-grounded judgment, and returns that understanding to the ongoing discussion, design, or implementation.

The repository contains two cooperating skills:

- **`just-in-time-research`** controls what to research, how broadly and deeply to investigate, how to manage evidence and state, when to scale execution, and when to return.
- **`zen-of-search`** selects and combines available search, retrieval, extraction, repository, and browsing tools according to the information gap.

```text
current task or discussion
        ↓
user explicitly invokes just-in-time-research
        ↓
identify decision-relevant uncertainty
        ↓
use zen-of-search when external information is needed
        ↓
inspect and verify evidence
        ↓
update understanding and form a judgment
        ↓
return to the original task
```

## Why

Most deep-research systems optimize for a terminal report:

```text
research question → search → report
```

This project treats research as an intermediate cognitive operation:

```text
task → uncertainty → research episode → updated judgment → continued work
```

The goal is not exhaustive coverage. The goal is enough reliable understanding to improve the user's next decision or action.

## Design principles

- **Manual activation.** `just-in-time-research` is intended to run only after explicit user invocation.
- **Decision-oriented control.** Investigate the unknowns most likely to change the answer.
- **Dynamic breadth and depth.** Do not use fixed source, query, or agent counts.
- **Claim-level evidence.** A source matters only when it supports, contradicts, or limits a relevant claim.
- **Minimal state.** Preserve current understanding and recoverable evidence, not the full trajectory.
- **Elastic execution.** Use the smallest sufficient system; add external state or subagents only when useful.
- **No fixed deliverable.** Return a fact, explanation, comparison, judgment, design, experiment, or report according to the actual need.
- **Continue the work.** Research updates the task context; it does not automatically end the task.

## Repository structure

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

There is one canonical `skills/` tree shared by Claude Code, Codex, and other Agent Skills hosts. Runtime behavior is maintained once. Platform manifests control discovery, presentation, and any host-specific policy that can be expressed without forking the skill content. References are loaded only when the current research episode needs them. `docs/` is for human maintainers and is not part of the runtime protocol.

## Install

### Claude Code

Add the repository as a marketplace and install the plugin:

```text
/plugin marketplace add Ttungx/just-in-time-research
/plugin install just-in-time-research@just-in-time-research
```

Invoke the research skill explicitly:

```text
/just-in-time-research investigate whether this architecture should use Temporal
```

Claude Code loads the same canonical `skills/` tree as the other hosts. Explicit-only activation is stated directly in the `just-in-time-research` skill instructions; no Claude-specific copy is maintained.

### Codex

Recent Codex builds with plugin marketplace support can install the repository with:

```bash
codex plugin marketplace add Ttungx/just-in-time-research
codex plugin add just-in-time-research@just-in-time-research
```

Invoke the skill explicitly:

```text
$just-in-time-research Investigate whether this architecture should use Temporal.
```

Codex additionally enforces manual invocation through `policy.allow_implicit_invocation: false` in `skills/just-in-time-research/agents/openai.yaml`.

### Install individual skills

Agents that support the Agent Skills directory format can install either directory directly:

```text
skills/just-in-time-research
skills/zen-of-search
```

No MCP provider is bundled or required. The skills use the search, browser, repository, document, code, and execution capabilities available in the host environment.

## How the skills compose

`just-in-time-research` owns epistemic strategy:

- frame the real problem;
- identify decision-bearing unknowns;
- choose breadth, depth, verification, synthesis, or experiment;
- manage research state;
- decide whether to delegate;
- form the project-specific judgment;
- stop when the answer is decision-ready.

`zen-of-search` owns information acquisition strategy:

- identify the retrieval shape;
- choose the primary tool by its actual capability;
- discover candidate sources;
- acquire difficult content;
- combine tools only across distinct stages;
- stop when additional searching is unlikely to change the conclusion.

Neither skill requires a specific MCP provider. Tool schemas and capabilities in the current environment are authoritative.

## Example uses

```text
$just-in-time-research Compare the durable-execution options for this repository and recommend one.
```

```text
$just-in-time-research Verify whether this library actually supports the behavior claimed in its README.
```

```text
$just-in-time-research Research this unresolved design issue, then continue implementing the best-supported solution.
```

```text
$zen-of-search Find the canonical source and current implementation status of this API.
```

## Status

The repository intentionally begins as a prompt-and-reference system. It has no custom search service, database, state machine, or mandatory scripts. Additional machinery should be introduced only when evaluations show that instructions alone are insufficient.

## License

MIT
