# Research State

Preserve continuity without carrying the full research history. Keep only what is needed to understand the current problem, choose the next action, and recover important evidence.

## Default to Active Context

For short episodes, keep state in the current context. Do not create files merely because research started.

Externalize state only when the episode becomes long or context-heavy, several branches or agents are involved, important findings may be lost through compaction, work will probably resume later, or the user asks to preserve it.

Use the lightest available storage.

## Keep a Compact Working State

Retain only the semantic roles needed by the episode, such as:

- the real question;
- relevant project goals and constraints;
- current understanding;
- established findings;
- unresolved questions or contradictions;
- active branches;
- provisional judgment;
- next best action.

These are not a mandatory schema.

## Separate State from History

State describes where the research stands. History describes everything that happened.

Do not preserve every query, rejected result, repeated summary, irrelevant failure, raw page, or abandoned reasoning path. Preserve a failed attempt only when it reveals a constraint, rules out an approach, or prevents repeated work.

## Preserve Stable Findings

A useful finding states:

- what was learned;
- why it matters;
- its scope or conditions;
- where supporting evidence can be revisited.

Do not repeatedly rewrite stable findings. When new evidence changes one, update the affected finding, preserve unaffected findings, retain unresolved conflict, and revise dependent judgments.

## Keep Evidence Addressable

Store references to evidence rather than duplicating full source contents. Retain the URL or document identifier, relevant location, supported or challenged claim, and important time, version, or scope information.

Keep detailed excerpts only when they are difficult to recover or necessary for exact verification.

The state should make evidence recoverable, not become an evidence archive.

## Preserve Epistemic Boundaries

When useful, distinguish:

- established fact;
- supported interpretation;
- provisional judgment;
- unresolved uncertainty.

Use the distinction internally to prevent inference from silently becoming fact. Do not force it into the user-facing response when it adds no value.

## Compact by Decision Relevance

Compact when context becomes noisy or the episode changes phase.

Always preserve:

- the user's actual objective;
- project constraints affecting the answer;
- load-bearing findings;
- material contradictions;
- current judgment and its conditions;
- unresolved questions likely to change the answer;
- next intended action;
- evidence references needed for recovery.

Remove duplicates, completed low-value branches, superseded assumptions, routine retrieval details, large tool outputs, and information unrelated to the current decision.

Compaction must reduce detail without changing the meaning of the current state.

## Use Files as a Working Surface

When external state is needed, prefer a small editable Markdown document over a database or append-only log. The Agent should be able to inspect, replace, add, remove, recover, and trace information quickly.

Do not create a hierarchy until the amount or structure of evidence genuinely requires it. Raw sources, evidence notes, and working state may separate for very large episodes, but not by default.

## Coordinate Delegates with Bounded State

Do not pass the full history to a delegate. Provide the branch question, why it matters, relevant project context, constraining findings, evidence needs, and expected return.

A delegate should return compact findings, source references, contradictions or limitations, implications for the parent question, and remaining uncertainty.

The main Agent decides how the result changes shared state.

## Recover Incrementally

When resuming:

1. read the compact state;
2. recover the question and provisional judgment;
3. inspect only the evidence needed for the next action;
4. check whether time-sensitive facts are stale;
5. continue from the highest-value unresolved question.

Do not replay the full history or repeat completed work unless its evidence is missing, stale, or disputed.

## Persist Selectively

Keep external state after the episode only when it will guide later project work, the decision will likely be revisited, findings are reusable, implementation or experiment will follow, or the episode belongs to a larger investigation.

Otherwise let temporary state expire. Do not turn every research interaction into permanent project memory.

## Principle

```text
Keep the current problem clear.
Keep important findings stable.
Keep evidence recoverable.
Keep unresolved questions visible.
Discard what no longer changes the next decision.
```
