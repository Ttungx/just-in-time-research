# Repository Guidance

This repository contains agent-facing runtime instructions. Edit for behavioral precision, not explanatory flourish.

## Boundaries

- `skills/just-in-time-research/SKILL.md` is the canonical compact entrypoint.
- `claude-skills/` contains invocation wrappers only; never copy the method into them.
- `research-control.md` decides what to investigate and when to stop.
- `research-state.md` preserves continuity without retaining the full trajectory.
- `sources-and-evidence.md` decides whether information can carry a claim.
- `deep-research.md` controls execution scale and delegation topology.
- `skills/zen-of-search/SKILL.md` controls information acquisition, not research judgment.
- `docs/` is human-facing and may explain rationale in more detail.

Do not duplicate substantial guidance across files. Move detail to the narrowest relevant reference and keep the entry skill short.

## Design constraints

Preserve these decisions unless the project explicitly changes direction:

- `just-in-time-research` is manually invoked.
- Research is an intermediate process inside ongoing work, not a report pipeline.
- Breadth, depth, source count, and agent count are dynamic.
- Evidence state remains lightweight; do not add a database by default.
- Tools and MCP providers are selected by capability, not hard-coded as dependencies.
- Multiple agents are used only for bounded, meaningfully independent branches.
- Final output adapts to the user's actual question.

## Cross-file changes

The Claude wrapper may carry `disable-model-invocation: true`; the canonical skill must remain Codex-valid and relies on `agents/openai.yaml` for Codex invocation policy.

When changing behavior:

1. update the file that owns the behavior;
2. check `SKILL.md` routing language;
3. check `README.md` and `docs/architecture.md` for stale claims;
4. keep Claude and Codex manifests at the same version;
5. verify every referenced path and skill name.

Use `zen-of-search`, never `zen-of-skill`, as the skill identifier.
