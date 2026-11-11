# Repositorio de Habilidades de Claude & Agentes de IA

Este repositorio reúne las habilidades de programación y automatización para su uso en:
- **Claude Web** (`claude.ai` en el navegador)
- **Claude Desktop** (aplicación de escritorio)
- **Claude Code** (asistente de terminal)
- **Antigravity / Gemini CLI** y agentes basados en el estándar de agentes.

---

## 📦 Contenido del Repositorio

- **`skills/`**: 370+ habilidades listas para ser consumidas por agentes de IA.
  - **Graphify**: Creación y consulta de grafos de conocimiento de código y arquitectura.
  - **Ponytail**: Modo desarrollador senior minimalista ("the least new code that fully works").
  - **OmniRoute**: 45+ habilidades de enrutamiento LLM, compresión de contexto y herramientas MCP.
  - **ECC Suite**: Habilidades de ingeniería frontend, backend, bases de datos, testing y auditoría.
- **`rules/`**: Directivas de comportamiento permanente (`graphify.md`, `ponytail.md`, etc.).
- **`CLAUDE.md`**: Directivas de proyecto que Claude lee automáticamente en proyectos de Claude.ai.

---

## 🌐 Cómo usar estas habilidades en Claude Web (Navegador) y Claude Desktop

Claude en el navegador y Claude Desktop acceden a conocimientos y habilidades a través de la función **Proyectos (Projects)** de Claude.

### Opción 1: Conectar con GitHub (Recomendado para sincronización en la nube)
1. Sube este repositorio a tu cuenta de GitHub (ejemplo: `github.com/tu-usuario/claude-skills`).
2. Entra en [claude.ai](https://claude.ai) (o abre Claude Desktop).
3. Ve a la sección **Projects** y haz clic en **Create Project**.
4. En la configuración del proyecto, haz clic en **Connect to GitHub** y selecciona este repositorio.
5. ¡Listo! Cualquier chat que inicies dentro de ese Proyecto tendrá acceso a todas tus habilidades tanto en el navegador como en Claude Desktop.

### Opción 2: Subir directamente a Conocimientos del Proyecto (Project Knowledge)
1. En tu proyecto de Claude (Web o Desktop), ve a la pestaña **Project Knowledge**.
2. Arrastra y suelta los archivos `CLAUDE.md`, las reglas de la carpeta `rules/` o las habilidades específicas de `skills/` que quieras activar para ese proyecto.
3. Se ha generado un archivo comprimido `claude-skills-bundle.zip` para facilitar la subida en lote.

---

## 💻 Uso Local (Claude Code y Antigravity)

Las habilidades de este repositorio ya están instaladas y activas en tus directorios locales del sistema:
- **Claude Code**: `%USERPROFILE%\.claude\skills`
- **Antigravity**: `%USERPROFILE%\.gemini\config\skills`

Cualquier cambio que realices o habilidad que añadas a este repositorio se puede sincronizar con un solo comando.
