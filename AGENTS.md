# Repository Guidance

This repository contains agent-facing runtime instructions. Edit for behavioral precision, not explanatory flourish.

## Boundaries

- `skills/just-in-time-research/SKILL.md` is the compact research entrypoint.
- `research-control.md` decides what to investigate and when to stop.
- `research-state.md` preserves continuity without retaining the full trajectory.
- `sources-and-evidence.md` decides whether information can carry a claim.
- `deep-research.md` controls execution scale and delegation topology.
- `skills/zen-of-search/SKILL.md` controls information acquisition, not research judgment.
- `docs/` is human-facing and may explain rationale in more detail.

There is one `skills/` tree. Do not add platform-specific copies of the Skill instructions.

Do not duplicate substantial guidance across files. Move detail to the narrowest relevant reference and keep the entry skill short.

## Chinese mirror

- `skills-zh/` is a local-use Chinese mirror, not part of the repo's distributable skill content. Never reference it in `.claude-plugin/` or `.codex-plugin/` manifests or in the canonical `skills/` tree.
- Keep `skills-zh/just-in-time-research/` in sync whenever `skills/just-in-time-research/` changes: `SKILL.md`, `references/`, `agents/openai.yaml`.
- Only `just-in-time-research` is mirrored for now; add other skills only when the user asks.

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

The canonical Skill frontmatter must remain valid for the shared Agent Skills format and Codex validation. Codex-specific invocation policy belongs in `agents/openai.yaml`. Claude Code loads the same canonical Skill and follows its explicit-invocation instruction; do not create a separate Claude wrapper.

When changing behavior:

1. update the file that owns the behavior;
2. check `SKILL.md` routing language;
3. check both `README.md` and `README.zh-CN.md`;
4. check `docs/architecture.md` for stale claims;
5. keep Claude and Codex manifests at the same version;
6. verify every referenced path and skill name.

Use `zen-of-search`, never `zen-of-skill`, as the skill identifier.
