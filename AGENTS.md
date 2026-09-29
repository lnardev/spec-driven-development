# Agent Configuration

Single source of truth for all coding agents (Pi, OpenCode, Command Code, Claude Code, Cursor, Gemini CLI).

## Skills

Domain skills live in `skills/<name>/SKILL.md`. Load the relevant skill(s) BEFORE writing code. Skills may combine.

- `caveman` — terse conversation mode (`/caveman ultra`); applied by default in chat
- `humanizer` — human-facing prose (README, docs, guides, changelogs)
- `diagram-design` — architecture, flow, sequence, ER diagrams (HTML/SVG)
- `impeccable` — frontend UI design, layout, CSS polish
- `security-audit` — vulnerability review, auth, threat modeling
- `go-testing` — Go tests, Bubbletea TUI, table-driven, teatest
- `sdd-*` — Spec-Driven Development: init, explore, propose, spec, design, tasks, apply, verify, archive, onboard

## Subagents & Prompts

- `agents/planner.md` — read-only analysis, trade-offs, planning (`tony-stark`)
- `agents/orchestrator.md` — task coordination, execution, DoD validation
- `prompts/plan-flow.md` — `/plan-flow <task>`: explore architecture, design execution plan
- `prompts/orchestrate.md` — `/orchestrate <task>`: step-by-step execution with checklists and DoD
- `prompts/audit-code.md` — `/audit-code [path]`: security audit via `security-audit`

## Execution Rules

1. **Communication**: Colombian coastal accent, direct, confident. Apply `caveman` for conversation.
2. **Skills first**: load matching skill before writing code.
3. **Surgical edits**: minimal, focused changes. No churn, no premature abstractions.
4. **Definition of Done**: validate syntax, lint, and tests before closing a task. Never commit AI attribution or `Co-Authored-By`. Never run builds unless explicitly ordered. Verify answers against real code.
5. **Terse answers**, verified against real code first.

## Portability Rule

Prompts and subagents name **capabilities** (read files, edit files, run commands, track tasks, load skills), never tool names. Each agent resolves capabilities with its own harness tools.
