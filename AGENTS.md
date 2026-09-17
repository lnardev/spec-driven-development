# Agent Skills Index
When working on this project, load the relevant skill(s) BEFORE writing any code.

## How to Use
1. Check the trigger column to find skills that match your current task.
2. Load skill immediately using `activate_skill` tool (or reading `skills/<name>/SKILL.md`).
3. Follow ALL patterns and rules from loaded skill.
4. Multiple skills can apply simultaneously.

## Skills Matrix

| Skill | Trigger / Use Case | Path |
|-------|-------------------|------|
| `caveman` | Chat responses, brevity, compact output (`/caveman ultra`). | [`skills/caveman/SKILL.md`](skills/caveman/SKILL.md) |
| `humanizer` | Documentation, PR descriptions, markdown prose, commit notes (strip AI fluff). | [`skills/humanizer/SKILL.md`](skills/humanizer/SKILL.md) |
| `diagram-design` | Architecture diagrams, flows, sequence, state, ER, charts (HTML/SVG). | [`skills/diagram-design/SKILL.md`](skills/diagram-design/SKILL.md) |
| `impeccable` | Frontend UI design, layout, styling, polishing CSS/components. | [`skills/impeccable/SKILL.md`](skills/impeccable/SKILL.md) |
| `security-audit` | Vulnerability review, auth checks, threat modeling, security review. | [`skills/security-audit/SKILL.md`](skills/security-audit/SKILL.md) |
| `go-testing` | Go unit tests, Bubbletea TUI, table-driven tests, teatest coverage. | [`skills/go-testing/SKILL.md`](skills/go-testing/SKILL.md) |
| `sdd-init` | Initialize SDD context, testing capabilities, and OpenSpec structure. | [`skills/sdd-init/SKILL.md`](skills/sdd-init/SKILL.md) |
| `sdd-explore` | Deep codebase and architectural exploration before proposing changes. | [`skills/sdd-explore/SKILL.md`](skills/sdd-explore/SKILL.md) |
| `sdd-propose` | Create structured change proposals (`proposal.md`) with intent and scope. | [`skills/sdd-propose/SKILL.md`](skills/sdd-propose/SKILL.md) |
| `sdd-spec` | Write BDD Given/When/Then requirements and capability specifications. | [`skills/sdd-spec/SKILL.md`](skills/sdd-spec/SKILL.md) |
| `sdd-design` | Produce technical architecture design, data flow, and trade-offs. | [`skills/sdd-design/SKILL.md`](skills/sdd-design/SKILL.md) |
| `sdd-tasks` | Break down design into atomic, ordered implementation tasks (`tasks.md`). | [`skills/sdd-tasks/SKILL.md`](skills/sdd-tasks/SKILL.md) |
| `sdd-apply` | Implement tasks in code following specs, design, and TDD constraints. | [`skills/sdd-apply/SKILL.md`](skills/sdd-apply/SKILL.md) |
| `sdd-verify` | Verify implementation against spec scenarios and run test checks. | [`skills/sdd-verify/SKILL.md`](skills/sdd-verify/SKILL.md) |
| `sdd-archive` | Archive completed changes and update master specifications. | [`skills/sdd-archive/SKILL.md`](skills/sdd-archive/SKILL.md) |

## Custom Subagents

| Subagent | Role | Tools | Path |
|----------|------|-------|------|
| `tony-stark` | Read-only analysis, trade-offs, architecture, and step-by-step design. | Read-only & search (`read_file`, `grep`, `glob`, `web_search`) | [`agents/planner.md`](agents/planner.md) |
| `orchestrator` | Task coordination, skill delegation, code changes, and DoD validation. | Full edit, tasks & execution (`edit_file`, `write_file`, `todo_write`, `powershell`) | [`agents/orchestrator.md`](agents/orchestrator.md) |

## Custom Slash Commands

| Command | Usage | Action | Path |
|---------|-------|--------|------|
| `/plan-flow` | `/plan-flow <task>` | Explora arquitectura y diseña plan de ejecución sin tocar código. | [`.commandcode/commands/plan-flow.md`](.commandcode/commands/plan-flow.md) |
| `/orchestrate` | `/orchestrate <task>` | Ejecuta tarea paso a paso con checklists, skills y validación DoD. | [`.commandcode/commands/orchestrate.md`](.commandcode/commands/orchestrate.md) |
| `/audit-code` | `/audit-code [path]` | Dispara auditoría de vulnerabilidades con `security-audit`. | [`.commandcode/commands/audit-code.md`](.commandcode/commands/audit-code.md) |

## Agent Execution Rules

1. **Communication Style**:
   - Colombian coastal accent, direct, confident.
   - Apply `caveman` (ultra mode) for conversation: direct facts, zero filler, short sentences.
   
2. **Text & Documentation**:
   - When generating human-facing prose (README, docs, guides, changelogs), load and apply `humanizer`.

3. **Frontend & Design**:
   - When creating or refining UI components, layouts, or CSS, load `impeccable`.

4. **Architecture & Visuals**:
   - When diagram requested or needed to explain complex architecture, load `diagram-design`.

5. **Security & Review**:
   - When reviewing code security, APIs, endpoints, or data handling, load `security-audit`.

6. **Go & Testing**:
   - When writing or fixing Go code, Bubbletea TUIs, or unit/integration tests, load `go-testing`.

7. **Definition of Done (DoD)**:
   - Validate changes before closing task (syntax, lint, tests if exist).
   - Never commit AI attribution or `Co-Authored-By`.
   - Never run build automatically after changes unless explicitly ordered.
   - Keep answers terse, verified against real code first.