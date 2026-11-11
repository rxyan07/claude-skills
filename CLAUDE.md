# Repositorio Global de Habilidades y Reglas para Claude & Agentes de IA

Este repositorio contiene la colección unificada de habilidades (**Skills**), reglas (**Rules**) y comandos para Claude (en Claude Web a través de Proyectos, Claude Desktop y Claude Code) así como agentes compatibles (Antigravity, Cursor, etc.).

---

## 🚀 Capacidades y Paquetes Integrados

### 1. Graphify (Grafo de Conocimiento de Código)
- **Propósito**: Convierte cualquier repositorio, arquitectura o conjunto de documentos en un grafo de conocimiento navegable.
- **Archivos de habilidad**: `skills/graphify/SKILL.md` (con referencias en `references/`)
- **Regla activa**: `rules/graphify.md`
- **Uso / Disparadores**:
  - `/graphify`: Ejecuta el análisis y genera el grafo en `graphify-out/`.
  - `/graphify <ruta> --mode deep`: Extracción profunda de dependencias y relaciones entre ficheros.
  - Cuando existe `graphify-out/graph.json`, se debe consultar `graphify query "<pregunta>"` antes de inspeccionar ficheros manualmente.

---

### 2. Ponytail (Modo Senior Minimalista / Lazy Dev)
- **Filosofía**: *"El mejor código es el que no se escribe. Resuelve el problema completo con el menor código posible y cero boilerplate innecesario."*
- **Habilidades disponibles**:
  - `skills/ponytail/SKILL.md`: Modo desarrollador senior minimalista.
  - `skills/ponytail-audit/SKILL.md`: Auditoría rápida de calidad, bugs y riesgos sin alterar código.
  - `skills/ponytail-debt/SKILL.md`: Registro de atajos técnicos (`shortcut:`).
  - `skills/ponytail-gain/SKILL.md`: Estadísticas de ahorro y métricas de impacto.
  - `skills/ponytail-help/SKILL.md`: Guía de referencia rápida de Ponytail.
  - `skills/ponytail-review/SKILL.md`: Revisión profunda de cambios y edge cases.
- **Regla activa**: `rules/ponytail.md`

---

### 3. OmniRoute (Enrutamiento LLM, Compresión y Multi-Herramientas)
- **Propósito**: Integración con el catálogo de proveedores de IA, compresión de contexto de 60-90% (RTK / Caveman), balanceo de carga y suites de pruebas.
- **Habilidades de API**:
  - `omni-auth`, `omni-providers`, `omni-models`, `omni-combos-routing`, `omni-api-keys`, `omni-budget`, `omni-cache`, `omni-compression`, `omni-context-rtk`, `omni-resilience`, `omni-settings`, `omni-mcp`, `omni-agents-a2a`, etc.
- **Habilidades de CLI**:
  - `cli-serve`, `cli-routing`, `cli-compression`, `cli-contexts`, `cli-cost-usage`, `cli-eval`, `cli-health`, `cli-models`, `cli-mcp`, `cli-tunnel`, `cli-backup-sync`, `cli-batches`, etc.

---

### 4. Colección Integral ECC (300+ Habilidades de Ingeniería)
- **Frontend**: `react-patterns`, `vue-patterns`, `nuxt4-patterns`, `vite-patterns`, `frontend-design-direction`, `make-interfaces-feel-better`.
- **Backend & APIs**: `backend-patterns`, `api-design`, `django-patterns`, `nestjs-patterns`, `springboot-patterns`, `golang-patterns`, `dotnet-patterns`, `laravel-patterns`, `postgres-patterns`, `redis-patterns`.
- **Calidad & Testing**: `tdd-workflow`, `verification-loop`, `e2e-testing`, `security-review`, `agent-introspection-debugging`, `conventional-commit-review`.
- **Arquitectura & Ops**: `kubernetes-patterns`, `deployment-patterns`, `github-ops`, `docker-patterns`.

---

## 📌 Guía de Uso Rápido en Claude

1. **En Claude Web (claude.ai) o Claude Desktop**:
   - Crea un **Proyecto** (Project).
   - Conecta este repositorio con **GitHub** en los ajustes del Proyecto, o sube los archivos de habilidades a los conocimientos del proyecto (**Project Knowledge**).
   - Claude tendrá acceso continuo a todas las habilidades y directivas en cada conversación.

2. **En Claude Code (CLI)**:
   - Las habilidades ya están sincronizadas directamente en `~/.claude/skills/` y se cargan automáticamente en cada sesión.

3. **Invocación de Habilidades**:
   - Cada habilidad en `skills/<nombre>/SKILL.md` define su frontmatter y contexto. Puedes activarlas pidiendo la tarea por su nombre (ej: *"usa ponytail para refactorizar esto"*, *"haz un graphify del proyecto"*, *"analiza con omni-compression"*).
