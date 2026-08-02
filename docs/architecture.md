# Architecture

## Thesis

Just-in-Time Research is not a smaller report generator. It is a research control layer embedded in ongoing human–Agent work.

```text
traditional deep research
question → retrieval → report

just-in-time research
task → decision-relevant uncertainty → research episode
     → updated problem model and judgment → continued work
```

The distinction determines the architecture. A report system can optimize for topic coverage and presentation. An embedded research system must optimize for intervention timing, decision value, context continuity, evidence quality, and return to action.

## First-principles model

Research exists to reduce uncertainty. In this project, uncertainty matters only when it affects understanding, judgment, or the next action.

The system therefore separates three layers:

```text
world model
What is externally true?

explanatory model
Why does it behave that way?

project judgment
Given this project's goals and constraints, what should be done?
```

Retrieval can update the world model. Evidence synthesis updates the explanatory model. Neither automatically determines the project judgment. The Agent remains responsible for connecting evidence to the user's situation.

## Two-skill composition

The repository contains two skills because research control and information acquisition are different problems.

### Just-in-Time Research

Owns the epistemic strategy:

- frame the real problem;
- identify decision-bearing unknowns;
- generate problem-specific research branches;
- choose breadth and depth;
- determine evidence burden;
- preserve state;
- decide whether to delegate;
- synthesize a project-specific judgment;
- decide when research is sufficient.

It answers:

> What should be researched, why does it matter, and when should the Agent return?

### Zen of Search

Owns the retrieval strategy:

- identify whether the dominant difficulty is semantic discovery, precise fresh lookup, structured retrieval, source acquisition, or repository inspection;
- choose the primary available tool;
- combine tools only across distinct stages;
- inspect original sources;
- stop low-yield search.

It answers:

> How should the needed information be found and acquired in this environment?

The research skill calls or loads `zen-of-search` instead of copying retrieval rules into its own prompt. This preserves modularity and allows the search skill to evolve independently.

## Runtime layers

```text
user intent and project context
        ↓
just-in-time-research/SKILL.md
        ↓
research-control.md
        ├── research-state.md        when continuity becomes difficult
        ├── sources-and-evidence.md  when claim support matters
        ├── deep-research.md         when execution must scale
        └── zen-of-search skill      when external information is needed
        ↓
available host tools and MCPs
        ↓
evidence-grounded judgment
        ↓
current discussion, design, or implementation
```

The entry skill stays compact. Detailed rules are loaded only at the point where they improve a decision. This is Just-in-Time Context applied to the research system itself.

## Manual activation

The primary research skill is intentionally user-invoked.

Reasons:

- research can be expensive in time, tokens, and tool use;
- automatic activation can interrupt ordinary collaboration;
- the user is best positioned to decide when the task merits an explicit research episode;
- manual invocation gives a clear boundary for deeper external investigation.

Claude Code and Codex express manual invocation differently. Codex uses `policy.allow_implicit_invocation: false` in `agents/openai.yaml`. Codex plugin validation does not accept Claude's `disable-model-invocation: true` in the canonical skill, so the Claude marketplace exposes a thin wrapper under `claude-skills/` that applies the flag and then loads the canonical skill. The method remains single-source; only invocation metadata is platform-specific.

`zen-of-search` may remain implicitly available because it is a narrow retrieval skill and can serve ordinary current-information questions outside a full research episode.

## Dynamic research control

The research process is not a fixed pipeline. The Agent maintains a small frontier of unresolved branches and selects the next action by expected decision impact.

```text
priority ≈ impact on judgment × uncertainty × resolvability ÷ cost and noise
```

This is a qualitative control heuristic, not a scoring system. It prevents two common failures:

- exhaustive research into branches that cannot change the answer;
- premature synthesis before a load-bearing uncertainty is resolved.

The main control actions are expansion, deepening, verification, backtracking, synthesis, parallelization, and experiment. The action set is stable; the research perspectives are generated from the specific problem rather than from a fixed checklist.

## Decision readiness

The stopping rule is not source count, search count, elapsed time, or context exhaustion.

Research returns when:

- the real problem is framed correctly;
- important alternatives or mechanisms have been considered;
- load-bearing claims have adequate evidence;
- contradictions are resolved or bounded;
- findings have been interpreted for the project;
- a useful judgment can be stated;
- the next plausible investigation is unlikely to materially change it.

This is decision readiness rather than exhaustive knowledge.

The same rule permits an honest incomplete result. Research can end because evidence is inaccessible, sources genuinely disagree, local data is required, or an experiment now dominates further web retrieval.

## State model

The project rejects both extremes:

- keeping the entire trajectory in context;
- constructing a heavy evidence database for every episode.

State is separated from history. The active state contains only what is needed to continue coherently: objective, constraints, stable findings, material conflict, provisional judgment, active branch, next action, and recoverable source references.

Short episodes remain entirely in context. Longer episodes may externalize a compact Markdown working state. Persistence is selective and temporary by default.

This gives most of the value of file-centric long-horizon agents without imposing their infrastructure on ordinary research.

## Evidence model

A citation is not evidence merely because its URL resolves or its topic matches the text. Evidence is claim-relative.

```text
discovered → accessible → inspected → relevant → supports the claim
```

The Agent matches source type to the claim, preserves scope and version, checks source independence, retains contradictions, and escalates from summaries to passages, full documents, code, tests, datasets, or experiments only when necessary.

The final judgment remains distinct from the sourced facts. Sources support premises; they do not outsource project decision-making.

## Deep Research as elastic topology

Deep Research is an execution mode, not a separate methodology.

The system scales through a continuum:

```text
one short context
→ extended single Agent
→ externalized state
→ one delegated branch
→ independent parallel branches
→ bounded research waves
```

Delegation is based on independent uncertainty, not report sections or decorative roles. The main Agent retains the central objective and final synthesis. Delegates receive bounded questions and return compact findings with provenance and uncertainty.

The system contracts again when synthesis becomes more valuable than retrieval.

## Tool neutrality

The plugin bundles no MCP server and declares no mandatory provider dependency. Search tools change rapidly, and host environments differ.

`zen-of-search` therefore reasons from capabilities first. It recognizes common strengths of tools such as Exa, Tavily, AnySearch, and Firecrawl when present, but the current tool schemas remain authoritative.

Direct repository, document, and local-code connectors take precedence when the evidence lives there. Generic web search is not an abstraction layer over data that the Agent can inspect directly.

## Distribution architecture

One repository serves several hosts without duplicating runtime logic:

```text
.claude-plugin/plugin.json          Claude Code plugin metadata
.claude-plugin/marketplace.json     Claude Code marketplace and wrapper path
claude-skills/*                     thin Claude invocation wrappers
.codex-plugin/plugin.json           Codex plugin metadata
.agents/plugins/marketplace.json    Codex marketplace entry
skills/*                            canonical shared skills
```

Platform files control discovery and presentation. The shared `skills/` tree remains the source of behavior.

## Non-goals

The initial version deliberately does not provide:

- an automatic research trigger;
- a fixed research report template;
- a source-count or query-count rubric;
- a persistent evidence database;
- a custom search service;
- a mandatory multi-agent hierarchy;
- provider-specific MCP configuration;
- duplicated Claude and Codex skill implementations.

These are not missing features. They are constraints that protect the core design from ceremony and premature infrastructure.

## Evolution rule

Add machinery only after a concrete failure is observed and evaluated.

Examples:

- add scripts when deterministic validation is repeatedly needed;
- add persistent artifacts when context compaction loses critical state;
- add evaluators when claim–evidence misalignment remains frequent;
- add provider metadata when a host requires it for installation;
- add examples when Agents systematically misinterpret a control rule.

The repository should remain a small set of high-leverage instructions until evidence shows that a heavier system improves outcomes.
