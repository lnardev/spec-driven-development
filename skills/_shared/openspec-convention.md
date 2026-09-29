# OpenSpec Convention

File-based persistence for SDD artifacts. Portable, git-friendly, team-shareable.

## Directory Structure

```
openspec/
├── config.yaml              ← Project config: context, strict_tdd, rules
├── specs/                   ← Source of truth (main specs)
│   └── {capability}/spec.md
└── changes/
    ├── {change-name}/       ← Active change
    │   ├── proposal.md
    │   ├── specs/{capability}/spec.md   ← Delta specs
    │   ├── design.md
    │   ├── tasks.md
    │   └── verify-report.md
    └── archive/
        └── YYYY-MM-DD-{change-name}/    ← Completed changes
```

## Rules

- Main specs in `openspec/specs/` are the source of truth — only the archive phase writes to them.
- Active changes live under `openspec/changes/{change-name}/` — one folder per change.
- Delta specs describe ADDED / MODIFIED / REMOVED requirements relative to the main specs.
- `config.yaml` holds project context (max ~10 lines), `strict_tdd`, and per-phase `rules:`.
- Never delete archived changes — the archive is the audit trail.
