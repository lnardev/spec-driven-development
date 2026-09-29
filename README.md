# Spec-driven development

Configuración compartida para agentes de código: Pi, OpenCode, Command Code, Claude Code, Cursor y Gemini CLI. Un solo directorio con las reglas, skills, subagentes y prompts que todos los agentes leen, para que cada uno se comporte igual sin importar la herramienta.

El punto de entrada es `AGENTS.md`. Es la fuente única de verdad: skills disponibles, subagentes, prompts y reglas de ejecución. `CLAUDE.md` existe porque Claude Code busca ese nombre, y solo apunta a `AGENTS.md`.

## Estructura

```
AGENTS.md            fuente única de verdad para todos los agentes
CLAUDE.md            shim que redirige a AGENTS.md
agents/              subagentes (planner, orchestrator)
prompts/             flujos reutilizables (/plan-flow, /orchestrate, /audit-code)
commands/            mismos flujos con formato de comando para los harness que lo usan
skills/              instrucciones por dominio, cada una en skills/<nombre>/SKILL.md
skills/_shared/      convenciones compartidas entre skills SDD
```

## Skills

Cada skill es un `SKILL.md` que el agente carga antes de escribir código. Varias pueden combinarse en una misma tarea.

| Skill | Para qué sirve |
|---|---|
| `caveman` | Modo de conversación comprimido, niveles lite a ultra. Aplicado por defecto en chat |
| `humanizer` | Prosa para humanos: README, docs, guías, changelogs |
| `diagram-design` | Diagramas de arquitectura, flujo, secuencia, ER, y más, como HTML/SVG |
| `impeccable` | Diseño de interfaces: layout, CSS, accesibilidad, pulido visual |
| `security-audit` | Revisión de vulnerabilidades, autenticación, modelado de amenazas |
| `go-testing` | Tests en Go, TUI con Bubbletea, tablas de casos, teatest |
| `sdd-*` | Ciclo completo de Spec-Driven Development |

El ciclo SDD cubre diez fases: `init` (arranca SDD en un proyecto), `explore` (investigar una idea), `propose` (propuesta de cambio), `spec` (especificaciones con escenarios), `design` (diseño técnico), `tasks` (desglose en checklist), `apply` (implementación), `verify` (validación contra specs), `archive` (sync y cierre del cambio) y `onboard` (recorrido guiado del flujo completo).

## Subagentes

- `agents/planner.md`, alias `tony-stark`. Análisis de solo lectura: arquitectura, trade-offs, plan de implementación paso a paso. Nunca edita archivos.
- `agents/orchestrator.md`. Coordinación de tareas, ejecución secuencial con checklist, y validación de Definition of Done antes de cerrar.

## Prompts y comandos

- `/plan-flow <tarea>`: explora la arquitectura y produce un plan de ejecución.
- `/orchestrate <tarea>`: ejecución paso a paso con checklists y DoD.
- `/audit-code [ruta]`: auditoría de seguridad sobre un objetivo, o sobre todo el workspace.

`commands/` contiene los mismos flujos en formato de comando para los harness que distinguen entre prompts y comandos.

## Uso

Copia o enlaza este directorio en la raíz del proyecto donde trabaje el agente. Lo mínimo que necesita es `AGENTS.md`; el resto (`skills/`, `agents/`, `prompts/`) se carga bajo demanda según la tarea.

Los prompts y subagentes nombran capacidades (leer archivos, editar archivos, ejecutar comandos, trackear tareas, cargar skills) y nunca nombres de herramientas. Cada agente resuelve esas capacidades con las suyas, así la configuración viaja entre harness sin cambios.

## Reglas de ejecución

1. Comunicación con acento costeño colombiano, directa y segura. `caveman` para conversación.
2. Cargar la skill que corresponda antes de escribir código.
3. Ediciones quirúrgicas: cambios mínimos y enfocados, sin churn ni abstracciones prematuras.
4. Definition of Done: validar sintaxis, lint y tests antes de cerrar una tarea. Nunca atribución de IA ni `Co-Authored-By` en commits. Nunca correr builds salvo orden explícita. Verificar respuestas contra el código real.
5. Respuestas breves, verificadas contra el código real primero.
