# Research Control

Control what to investigate, how broadly and deeply to investigate it, and when to return. Do not impose a fixed report structure.

## Frame the Real Problem

Research the problem the user needs to resolve, not only the literal wording.

Determine:

- the intended decision, understanding, design, validation, or implementation;
- the project context and constraints that affect it;
- assumptions or prior decisions already in play;
- what kind of finding could change the next action.

A factual-looking question may be part of a larger decision. Preserve that context.

## Establish the Target

Form a compact internal model of:

- the central question;
- the intended use of the answer;
- the most important unknowns;
- evidence capable of resolving them;
- what must become clear before the answer is useful.

Revise this target when evidence changes the problem. Do not ask the user to define search depth, source count, or output format unless a missing fact blocks meaningful work.

## Maintain a Working Map

Keep a small set of unresolved branches. A branch may be an alternative, mechanism, load-bearing claim, project assumption, constraint, contradiction, failure mode, counterexample, or newly discovered question.

Generate branches from the problem and project context, not a fixed checklist. The map is not a report outline. Merge overlap and remove branches that no longer affect the answer.

## Select by Decision Impact

Choose the next action by its expected effect on the final answer.

Prioritize questions that could:

- reverse the current judgment;
- reveal or eliminate an important alternative;
- expose a missing requirement;
- resolve a material contradiction;
- determine feasibility;
- clarify a load-bearing mechanism;
- show that experiment is more useful than further search.

Use this only as a qualitative guide:

```text
priority = decision impact × uncertainty × resolvability ÷ cost and noise
```

Do not calculate a score. Do not continue a branch merely because more information exists.

## Choose the Control Action

**Expand** when the problem model may be incomplete. Discover distinct alternatives, constraints, mechanisms, or failure modes; do not repeat equivalent searches.

**Deepen** when one branch carries the conclusion. Inspect primary documentation, source code, tests, issues, papers, methods, benchmarks, or production evidence as required.

**Verify** in proportion to the consequence of error. Search snippets and repeated secondary summaries are not independent confirmation.

**Backtrack** when evidence invalidates an assumption or framing. Preserve unaffected findings and revise only dependent branches.

**Synthesize** when the evidence needs interpretation. Update what is established, inferred, disputed, project-relevant, and most uncertain.

**Parallelize** only when branches are bounded and meaningfully independent. Read `deep-research.md` before scaling delegation.

**Experiment** when local inspection, prototype, benchmark, measurement, or execution would reduce more uncertainty than further retrieval.

## Control Breadth and Depth

Do not assign fixed breadth or depth in advance.

Start broad enough to avoid an incomplete problem model. Then deepen the branches with the greatest decision impact.

Increase breadth when important alternatives may be missing, the structure remains unclear, sources share the same assumptions, or new evidence exposes another relevant dimension.

Increase depth when the answer depends on a specific claim or mechanism, sources conflict, version or implementation details matter, evidence may not transfer to the project, or a recommendation rests on an unsupported assumption.

```text
map the space
→ identify load-bearing unknowns
→ investigate them
→ update the map
```

Do not investigate every branch equally.

## Inspect the Remaining Gap

After a meaningful cycle, ask:

- What changed?
- Which uncertainty was reduced?
- What remains unsupported or contradictory?
- Which unexamined alternative could change the answer?
- What next action has the highest decision impact?
- Is further research more useful than synthesis or experiment?

Reflect on specific gaps. Preserve valid findings; do not restart with generic instructions to “think harder.”

## Continue or Return

Continue only when a realistic next action could materially change the answer. Continue especially when the response is still generic, a recommendation depends on an unsupported assumption, only summaries were inspected, an important alternative remains open, a conflict could alter the conclusion, or the facts are known but no useful judgment can yet be formed.

Return when the answer is decision-ready:

- the real problem is framed correctly;
- important alternatives or mechanisms have been considered;
- load-bearing claims have adequate support;
- material contradictions are investigated or retained as uncertainty;
- findings are interpreted for the current project;
- a clear judgment can be formed when needed;
- remaining uncertainty is understood;
- the next plausible research action is unlikely to materially change the answer.

The goal is not exhaustive knowledge. It is enough understanding to advance the user's next action.

Return the best-supported answer without certainty when evidence is inaccessible, credible sources remain in genuine disagreement, further search produces little information gain, proprietary or local data is required, experiment is now necessary, or available resources are exhausted. State what remains uncertain and what would reduce it.

Use time, token, tool, and agent budgets as safety boundaries. Close duplicate or low-impact work before weakening verification of a critical claim.

## Control Loop

```text
frame the real problem
→ establish the research target
→ build the working map
→ select the highest-impact unresolved question
→ expand | deepen | verify | backtrack | synthesize | parallelize | experiment
→ update findings and provisional judgment
→ inspect the remaining gap

if another action could materially change the answer:
    continue
else:
    return a decision-ready response
```
