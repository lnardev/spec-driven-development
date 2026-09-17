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