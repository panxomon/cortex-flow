# START HERE

Bienvenido a CortexFlow.

---

# Working language

CortexFlow opera con dos capas idiomáticas:

- **Core (siempre inglés):** `SYSTEM_PROMPT.md`, `BOOTSTRAP.md`, `.ai/orchestrator.md`, `.ai/skills/`, `.ai/templates/`, `.ai/workflows/`, `definitions/runtime-modes.md`, `definitions/flow-definition.md`.
- **Periferia (idioma del operador):** este archivo, `README.md`, `examples/`, `docs/`, `definitions/adr/`, `definitions/stories/`, `definitions/epics/`, `definitions/context.md`, `definitions/objective.md`.

**Elige aquí el idioma de la periferia para tu proyecto:**

```
working_language: es   # opciones: es | en | otro
```

El runtime usará este valor para producir outputs en el idioma indicado. El core nunca cambia.

---

# Orden de lectura

Antes de cualquier análisis o ejecución:

1. `README.md`
2. `BOOTSTRAP.md`
3. `SYSTEM_PROMPT.md`
4. `.ai/orchestrator.md`
5. Skills disponibles en `.ai/skills/`

---

# Metodología

Usar siempre: **Flow-Spec Driven Development (FDD)**.

Pipeline canónico:

```
Context
    ↓
Stories
    ↓
Flows
    ↓
ADRs
    ↓
Outputs
```

---

# Artefactos fundacionales (MUST-be)

Antes de ejecutar cualquier flow, deben existir:

- `definitions/context.md`
- `definitions/objective.md`
- `definitions/epics/` (al menos un epic)

Si falta alguno, el runtime se detiene y activa Discovery mode. Templates en `.ai/templates/`.

---

# Reglas importantes

* Nunca ejecutar desde ambigüedad
* Activar Discovery mode si falta contexto
* Máximo 3 preguntas por iteración
* Siempre producir outputs reutilizables
* Registrar decisiones relevantes como ADR

---

# Outputs válidos

* `definitions/` — memoria estructurada (intención)
* `docs/` — evidencia operacional (analysis, contracts, dependencies, flows)
* `examples/` — flows de referencia
* stories, epics, ADRs, flows, contracts

---

# Primera acción esperada

Si no existe contexto suficiente:

1. Activar `context-catalyst` o `context-discovery`
2. Producir `definitions/context.md` y `definitions/objective.md`
3. Esperar definición antes de continuar
