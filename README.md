# Agent Skill Workspace

Entorno de trabajo estructurado para desarrollo con agentes de IA autónomos (Command Code, Claude Code, OpenCode, Cursor, Pi). Sigue un enfoque **Spec-Driven Development (SDD)** con subagentes especializados y un catálogo modular de skills.

---

## 🏛️ Estructura del Proyecto

```text
.
├── .atl/                    # Registros globales y metadatos de skills (skill-registry.md)
├── .commandcode/            # Configuración local de Command Code (commands, agents)
├── agents/                  # Subagentes especializados de alto nivel
│   ├── planner.md           # Análisis de arquitectura y diseño sin efectos secundarios
│   └── orchestrator.md      # Coordinación paso a paso, checklist y cumplimiento de DoD
├── commands/                # Comandos rápidos slash (/plan-flow, /orchestrate, /audit-code)
├── openspec/                # Framework de especificaciones SDD (OpenSpec)
│   ├── config.yaml          # Configuración del proyecto, linters y suites de test
│   ├── specs/               # Especificaciones maestras del sistema (Source of Truth)
│   └── changes/             # Propuestas activas e histórico de cambios
├── skills/                  # Catálogo de habilidades modulares (SKILL.md)
│   ├── sdd-*                # Pipeline SDD completo (init, explore, propose, spec, etc.)
│   ├── caveman/             # Respuestas ultracompactas para ahorro de tokens
│   ├── humanizer/           # Redacción técnica natural sin clichés de IA
│   ├── diagram-design/      # Diagramas técnicos en HTML y SVG
│   ├── impeccable/          # Diseño UI, maquetación CSS y componentes
│   ├── security-audit/      # Auditoría de vulnerabilidades y seguridad
│   └── go-testing/          # Patrones de testing y componentes Bubbletea en Go
├── AGENTS.md                # Fuente única de verdad y directivas para agentes
├── CLAUDE.md                # Puente de compatibilidad para Claude Code
└── .gitignore               # Exclusión de temporales, binarios y artefactos
```

---

## 🚀 Flujo de Trabajo: Spec-Driven Development (SDD)

El flujo garantiza que ninguna funcionalidad compleja se programe sin antes tener especificaciones y diseño aprobados:

1. **Exploración (`sdd-explore`)**: Análisis del código sin modificaciones para mapear dependencias.
2. **Propuesta (`sdd-propose`)**: Creación de `proposal.md` con intención, alcance, riesgos y plan de rollback.
3. **Especificación (`sdd-spec`)**: Definición de requerimientos con formato BDD (*Given / When / Then*).
4. **Diseño (`sdd-design`)**: Arquitectura técnica y diagramas de componentes o flujo.
5. **Tareas (`sdd-tasks`)**: Desglose en tareas atómicas y secuenciales (`tasks.md`).
6. **Implementación (`sdd-apply`)**: Escritura del código tarea por tarea con soporte para TDD estricto.
7. **Verificación (`sdd-verify`)**: Comprobación del código contra los escenarios de la especificación.
8. **Archivo (`sdd-archive`)**: Consolidación del cambio en el registro maestro.

---

## 🤖 Subagentes

- **`planner`**: Agente analítico de solo lectura. Inspecciona dependencias y plantea planes óptimos sin modificar archivos.
- **`orchestrator`**: Conductor de ejecución. Gestiona checklists (`todo_write`), delega a los skills indicados y valida la Definición de Terminado (DoD) antes de cerrar cualquier tarea.

---

## ⚡ Comandos Slash

- `/plan-flow <objetivo>`: Activa el flujo de planificación y análisis sin riesgo sobre el código.
- `/orchestrate <tarea>`: Ejecuta una tarea compleja paso a paso con validaciones continuas.
- `/audit-code [ruta]`: Corre una revisión de seguridad y sanitización con `security-audit`.

---

## 🛠️ Compatibilidad Multi-Agente

Este repositorio está preparado para funcionar sin configuración extra en:
- **Claude Code**: Conecta mediante `CLAUDE.md` hacia `AGENTS.md`.
- **OpenCode / Cursor / Pi**: Utilizan `AGENTS.md` como instrucción de contexto base.
