# SDD Phase Common

Shared sections referenced by all `sdd-*` skills. Persistence modes: `openspec | none`.

## Section A: Load Skills

Before executing any phase work:

1. Read `.atl/skill-registry.md` if present — it maps work domains to available skills.
2. Read the project's skills index (`AGENTS.md` or equivalent).
3. Load any skill matching the phase domain (UI work → frontend skill, security review → audit skill, Go code → testing skill, etc.).

## Section B: Retrieve Context

- **openspec**: Read `openspec/config.yaml` (project context, `strict_tdd`, per-phase `rules`) and `openspec/specs/` (source of truth). Read prior artifacts of the change from `openspec/changes/{change-name}/`.
- **none**: Use only the context the orchestrator passed in the prompt.

## Section C: Persist Artifact

- **openspec**: Write the artifact file inside `openspec/changes/{change-name}/` following `openspec-convention.md` (e.g., `proposal.md`, `design.md`, `tasks.md`, `verify-report.md`).
- **none**: Return the artifact inline. Never create or modify project files.

When useful for traceability, record artifact metadata in a header comment:

```
artifact: {name}
change: {change-name}
type: {architecture | config | report}
```

## Section D: Return Envelope

Every phase returns a structured envelope:

```markdown
**status**: success | partial | blocked
**executive_summary**: {one paragraph}
**detailed_report**: {phase-specific tables and evidence}
**artifacts**: {files written, with paths}
**next_recommended**: {next phase or action}
**risks**: {list or "None"}
```
