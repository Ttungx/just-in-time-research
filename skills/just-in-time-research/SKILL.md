---
name: just-in-time-research
description: Conduct decision-oriented research inside an ongoing task or discussion. Use only when the user explicitly invokes this skill to investigate uncertainty, validate a claim, compare approaches, understand a mechanism, or improve a project decision. Dynamically control breadth, depth, evidence, state, and execution scale; then apply the findings to the user's actual problem instead of defaulting to a standalone report.
---

# Just-in-Time Research

Research as part of thinking, not the end product.

Use this skill only when the user explicitly invokes it. Do not activate it merely because a question is difficult or researchable.

## Purpose

Reduce uncertainty that matters to the user's current problem. The result may establish facts, explain a mechanism, compare alternatives, test an assumption, improve a design, form an engineering judgment, or show that implementation or experiment should come next.

Research is complete when it advances the user's understanding, decision, or action. A report is only one possible result.

## Begin from the Work

Before searching, recover the current task and project context:

- what the user is actually trying to resolve;
- why the question matters now;
- which goals, constraints, assumptions, and prior decisions affect it;
- what finding could change the next action.

Do not reduce a project decision to a generic topic search. Do not ask the user to specify breadth, depth, source count, or report structure unless a missing fact prevents meaningful research.

## Load Guidance on Demand

Use only the guidance needed for the current episode:

- Read `references/research-control.md` for problem framing, branch selection, breadth, depth, stopping, and transition to experiment.
- Use the `zen-of-search` skill when external information must be discovered, acquired, or verified.
- Read `references/sources-and-evidence.md` when claims are consequential, disputed, version-sensitive, indirect, or difficult to verify.
- Read `references/research-state.md` when the episode becomes long, context-heavy, multi-branch, or likely to resume later.
- Read `references/deep-research.md` when one context is insufficient or bounded delegation may improve coverage or depth.

Do not copy these references into the active context without need.

## Conduct the Episode

Maintain a compact internal model of:

- the central question and intended use of the answer;
- relevant project constraints;
- the most important unknowns;
- evidence capable of resolving them;
- the current provisional judgment;
- the next action most likely to change the answer.

Investigate decision-bearing unknowns first. Prefer inspected sources over snippets, direct evidence over repeated summaries, project-specific facts over generic assumptions, and focused depth over indiscriminate source volume.

Update the problem model when evidence changes it. Preserve valid findings and reopen only affected branches.

## Control Scale Dynamically

Do not use fixed modes, query counts, source counts, or agent counts.

Increase breadth when important alternatives, constraints, dimensions, or failure modes may be missing. Increase depth when a conclusion depends on a mechanism, implementation detail, contradiction, or unsupported assumption.

Use parallel agents only for bounded, meaningfully independent branches. Move from information retrieval to code inspection, prototyping, benchmarking, measurement, or experiment when those actions would reduce more uncertainty.

Budgets are guardrails, not completion criteria.

## Form the Judgment

Do not stop at collecting information.

When the user needs a decision:

1. establish the relevant objective situation;
2. interpret what the evidence means;
3. apply project goals and constraints;
4. state a clear judgment;
5. preserve material conditions, trade-offs, and uncertainty.

Do not present the Agent's recommendation as though a source stated it. Distinguish evidence, inference, and judgment when confusing them would weaken the answer.

## Return Dynamically

Shape the response around the user's actual need. It may be a direct answer, corrected framing, explanation, comparison, engineering judgment, architecture proposal, viable options, warning, experiment proposal, or full report.

Do not expose internal maps, state, delegation, or routine tool activity unless it helps the user. Cite sources actually inspected and supporting the claims made.

Treat the result as updated working context. If the skill was invoked inside a larger task, continue that task unless the user requested research only, a user decision is now required, the evidence shows the task should not proceed, or further work requires unavailable data or permission.

## Re-enter Incrementally

When the user challenges, narrows, or extends the result:

- preserve findings that remain valid;
- identify the changed uncertainty;
- reopen only affected branches;
- gather or verify the necessary evidence;
- update the judgment.

Restart only when the underlying problem or original framing changes.

## Core Loop

```text
understand the real problem and project context
→ identify the uncertainty that matters
→ load only the needed guidance
→ select the action most likely to change the answer
→ discover, inspect, verify, and interpret evidence
→ update understanding and provisional judgment

if another action could materially improve the answer:
    continue research
elif experiment or implementation would reduce more uncertainty:
    transition to that work
else:
    answer the user's actual question
    and continue the original task when appropriate
```

Use the loop as a control model, not a mandatory sequence.

## Principle

```text
Research what matters to the decision.
Go broad enough to avoid tunnel vision.
Go deep enough to understand the load-bearing claims.
Use evidence to form a judgment.
Then return to the work.
```
