# Deep Research

Use this document when a short investigation in the main context is no longer sufficient. Deep Research changes execution scale and topology; it does not replace research control, state, evidence, or search principles.

Do not assume that Deep Research requires multiple agents or a long report.

## Escalate Only When Needed

Escalation may be useful when:

- several high-impact branches can be investigated independently;
- one branch requires a long discovery and verification chain;
- evidence volume can no longer be handled reliably in active context;
- the answer spans several systems, repositories, domains, or bodies of literature;
- important sources conflict and need independent investigation;
- the consequence of error justifies broader or deeper verification;
- the user explicitly requests extensive research and the problem benefits from it.

Do not escalate merely because a topic is broad or difficult to explain.

## Scale the Smallest Sufficient System

Possible forms include:

```text
main-Agent research
→ extended single-Agent research
→ single Agent with externalized state
→ main Agent with one delegated branch
→ several parallel branches
→ multiple bounded research waves
```

Scale breadth, depth, duration, external state, agent count, and parallelism independently. More depth does not necessarily require more agents; more agents do not guarantee deeper research.

## Decompose by Uncertainty

Delegate research questions, not report sections.

A useful branch:

- resolves a distinct uncertainty;
- matters to the central question;
- can be understood without the full trajectory;
- has identifiable evidence needs;
- returns a bounded result;
- overlaps minimally with other branches.

Avoid vague tasks such as “research the background,” “investigate everything,” “write the security section,” or “find more information.”

Prefer a branch such as:

```text
Determine whether framework X can recover an interrupted workflow
without application-managed checkpoints, and identify the conditions.
```

The decomposition may change after evidence returns.

## Give a Bounded Brief

Provide only the context required to execute the branch:

- precise question;
- why it matters;
- relevant project constraints;
- established findings that constrain it;
- evidence to seek;
- exclusions or boundaries;
- expected return.

The delegate should return principal findings, source references, supporting and contradicting evidence, scope conditions, implications for the central question, and remaining uncertainty. Do not request its full trajectory or hidden reasoning.

## Keep Central Control

The main Agent owns the user's objective, central question, shared map, provisional judgment, relationship among branches, conflict resolution, and final synthesis.

Delegates investigate bounded branches. They may report that the parent framing is wrong, but they do not silently replace the objective or make unrelated project decisions.

Delegation transfers investigation effort, not responsibility for the answer.

## Use Agents as Context Boundaries

Delegation should reduce pressure on the main context. Let a delegate inspect large source sets or follow a deep branch in isolation, then return only key findings, conditions, contradictions, source locations, implications, and unresolved gaps.

Do not copy complete source collections or trajectories back into the main context. Use `research-state.md` when results must remain recoverable.

## Parallelize Independent Work

Parallelize when branches can progress without waiting for one another: separate technologies, products, bodies of literature, implementation mechanisms, stakeholder perspectives, or intentional independent verification.

Use sequential research when each step depends on the previous finding, branches require constant shared state, the problem is one causal or implementation chain, or coordination costs more than it saves.

Duplicate investigation only when independent verification or adversarial checking is intentional.

## Work in Bounded Waves

When several agents are needed, use waves rather than uncontrolled recursive expansion.

After each wave:

1. inspect returned results;
2. remove duplicates;
3. compare scopes and assumptions;
4. identify conflicts;
5. update the research map;
6. revise the provisional judgment;
7. decide whether another wave is justified.

A new wave must target a newly identified decision-relevant gap, not merely continue activity.

## Limit Recursive Delegation

Allow recursive delegation only when a branch contains genuinely independent sub-branches, cannot be handled reliably in one context, gains meaningful context or parallelism benefits, remains integrable, and is bounded.

Do not recursively delegate vague work or use delegation to avoid reasoning.

## Integrate Before Concluding

Treat delegated results as inputs, not final answers. Trace load-bearing findings to evidence, compare versions and assumptions, distinguish true agreement from shared dependence, preserve unresolved conflict, and determine how each branch affects the project.

The main Agent may need to verify a delegate's critical claim directly.

## Recover and Contract

When a branch fails, diagnose whether the question was too broad, context was missing, the evidence target was wrong, acquisition failed, branches should split or merge, sequential work is preferable, or the branch no longer matters. Do not repeat the same request unchanged.

As the problem becomes clearer, reduce parallelism. Return to a smaller form when most branches are resolved, one dependent investigation remains, additional work would overlap, local experiment is required, or synthesis has become more valuable than retrieval.

The final synthesis should normally be controlled by one Agent using consolidated state.

## End Deep Research

End expansion when the central question is decision-ready, remaining branches are unlikely to change the answer, uncertainty is bounded, progress now requires local data or experiment, credible evidence is unavailable, or expected research value no longer justifies cost.

The result may be a clear answer, provisional judgment, revised framing, implementation proposal, experiment recommendation, or unresolved disagreement. Do not default to a long report.

## Principle

```text
Scale the research, not the ceremony.
Use the fewest agents that can resolve the important uncertainties.
Give each agent a bounded question and isolated context.
Integrate every result into one shared understanding.
Expand only when expansion may change the answer.
Contract when synthesis becomes more valuable than further search.
```
