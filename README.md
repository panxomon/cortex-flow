# CortexFlow

> Transforma ambigüedad en flows ejecutables — antes de que el modelo improvise por ti.

CortexFlow es un **protocolo de context engineering para LLMs**. No es un binario, no es una librería, no es un runtime. Es un conjunto de convenciones en Markdown que el modelo lee y obedece: estructura intención, baja la ambigüedad antes de ejecutar, y deja artefactos verificables en tu repo.

```
Context → Stories → Flows → ADRs → Outputs
```

---

## El problema que resuelve

Los LLMs generan rápido pero olvidan rápido. Pasan tres cosas seguido:

- **Pides A, te entrega B** — porque "interpretó" sin preguntar.
- **El output no se puede auditar** — quedó en el chat, no en el repo.
- **La decisión clave no se registró** — y a la siguiente iteración nadie sabe por qué se hizo así.

CortexFlow ataca eso con tres reglas duras:

1. **Toda ejecución parte de contexto estructurado.**
2. **Todo output traza a una intención definida.**
3. **Toda decisión trascendental queda como ADR en el repo.**

> Nunca ejecutes desde la ambigüedad.

---

## Cómo se usa (4 pasos)

1. 📁 **Copia la carpeta `cortex-flow/`** a tu proyecto. Puro copy-paste, hermano.
2. 🤖 **Dile a tu modelo** (Claude, GPT, lo que tengai) que lea `cortex-flow/START_HERE.md` y respete el protocolo.
3. 💬 **Te va a preguntar:** *"¿Qué flow querí hoy?"*. Eligí modo (Discovery, Architecture, etc.) y describele la pega.
4. 🍿 **Mira y revisa.** El modelo va a estructurar, preguntar lo justo, y dejar artefactos en `definitions/` y `docs/`.

**Tip de caleta** 🧠: no escribas prompts largos. Escribí **contexto estructurado** en `definitions/context.md` y `definitions/objective.md`. El protocolo hace el resto.

---

## Cómo funciona por dentro

CortexFlow es **documentación que actúa como sistema operativo del modelo**. Los archivos clave:

| Archivo | Rol |
|---|---|
| `SYSTEM_PROMPT.md` | Reglas duras del agente |
| `BOOTSTRAP.md` | Contrato de inicio (qué leer y en qué orden) |
| `.ai/orchestrator.md` | Coordinación de skills y modos |
| `.ai/skills/` | 10 prompts especializados invocables por nombre |
| `.ai/templates/` | Plantillas Markdown rellenables |
| `definitions/` | Memoria estructurada (context, objective, stories, epics, flows, ADRs, contratos) |
| `docs/` | Evidencia operacional (analysis, contracts, dependencies, flows) |

**Flujo real cuando lo activas:**

1. El modelo lee `START_HERE → BOOTSTRAP → SYSTEM_PROMPT → orchestrator`.
2. Verifica el **gate fundacional**: `definitions/context.md`, `definitions/objective.md`, al menos un epic.
3. Si falta algo → activa **Discovery mode**, máx 3 preguntas, genera `problem-definition.md`.
4. Si está todo → te pide elegir runtime mode + flow.
5. Ejecuta dentro del modo seleccionado, deja artefactos donde corresponde.

---

## Pipeline canónico

| Etapa | Propósito |
|---|---|
| **Context** | Ground truth. Define la realidad operacional. |
| **Stories** | Intención cristalizada como narrativa ejecutable. |
| **Flows** | Rutas declarativas reutilizables. |
| **ADRs** | Decisiones trascendentales capturadas con razonamiento. |
| **Outputs** | Artefactos verificables en `docs/` o `definitions/`. |

---

## Runtime modes (9)

| Modo | Para qué |
|---|---|
| **Discovery** | Estructurar lo desconocido |
| **Architecture** | Diseñar, decidir, escribir ADRs |
| **Implementation** | Construir desde spec |
| **Debugging** | Aislar causa, fix mínimo |
| **Documentation** | Producir docs reusables |
| **Analysis** | Medir drift, evaluar coherencia |
| **Migration** | Transformar sin romper |
| **Optimization** | Refinar, simplificar |
| **Mediation** | Mediar tensiones contextuales (ver sección Mediation) |

Selección **explícita**. El modelo no infiere modo.

---

## Qué es un Flow

Unidad operativa fundamental. Declarativa, no imperativa.

```yaml
flow:
  name: api-contract-migration
  goal: Migrar una API REST a OpenAPI 3.1 sin romper consumidores
  context: legacy-api-v2
  inputs:
    - documentación de endpoints existentes
    - ejemplos de request/response
    - suite de tests de integración
  constraints:
    - sin breaking changes en paths
    - todos los campos existentes permanecen válidos
  steps:
    - inventariar endpoints
    - inferir schemas
    - generar spec OpenAPI 3.1
    - validar compatibilidad
  expected_outputs:
    - openapi-3.1.yaml
    - adr-migration.md
  validations:
    - todos los tests pasan contra el nuevo contrato
  artifacts:
    - definitions/contracts/openapi-3.1.yaml
    - definitions/adr/adr-001-api-migration.md
```

Spec formal completa en [`cortex-flow/definitions/flow-definition.md`](cortex-flow/definitions/flow-definition.md). Ejemplo ejecutable en [`cortex-flow/examples/api-contract-migration.md`](cortex-flow/examples/api-contract-migration.md).

---

## Mediation (subsistema transversal)

Mediation **no es parte del pipeline canónico**. Es un eje separado para tratar **tensiones contextuales** sobre artefactos ya producidos.

**Qué hace conceptualmente:**

- Detecta tensiones (ej. *velocidad de entrega vs mantenibilidad*) en un artefacto bajo un contexto declarado.
- Las interpreta a través de una **policy** activa (`startup-mvp`, `strict-system`, etc.).
- Propone una **posición contextual** con racional, o levanta que se requiere **mediación humana**.

**Qué NO hace:**

- No aprueba ni rechaza.
- No produce scores como output principal.
- No reemplaza el juicio humano.
- No se autoinvoca: requiere solicitud explícita del operador.

**Estado actual:** *Phase 1 — Ontología*. Lo que existe hoy en `mediation/`:

- `FOUNDATIONS.md` — constitución del subsistema (invariantes, vocabulario, failure modes).
- 3 skills (`tension-detector`, `policy-interpreter`, `context-arbitrator`) como prompts.
- Catálogos de tensions canónicas, dimensions, policies y resolutions.
- Phases 2–4 (modelo semántico, runtime, memoria organizacional) están **pending**.

Antes de invocar Mediation: leer [`cortex-flow/mediation/FOUNDATIONS.md`](cortex-flow/mediation/FOUNDATIONS.md). No es opcional — sin esa base, las skills hacen drift semántico.

---

## Estructura del repo

```
cortex-flow/
├── START_HERE.md              ← Empieza aquí
├── BOOTSTRAP.md               ← Contrato de inicio
├── SYSTEM_PROMPT.md           ← Reglas del agente
├── AGENTS.md                  ← Guidelines extendidas
├── .ai/
│   ├── orchestrator.md
│   ├── skills/                10 skills invocables
│   ├── templates/             6 plantillas
│   └── workflows/             repo-analysis.md
├── definitions/
│   ├── flow-definition.md
│   ├── runtime-modes.md
│   ├── context.md             ← lo creas tú
│   ├── objective.md           ← lo creas tú
│   ├── adr/                   ← decisiones
│   ├── stories/               ← intención cristalizada
│   ├── epics/                 ← agrupación de stories
│   ├── flows/                 ← definiciones declarativas
│   └── contracts/             ← contratos fuente de verdad
├── docs/
│   ├── analysis/              ← reportes, auditorías
│   ├── contracts/             ← snapshots derivados
│   ├── dependencies/
│   └── flows/                 ← narrativa de ejecución
├── mediation/                 ← subsistema de mediación contextual
└── examples/
```

---

## Primeros pasos concretos

1. Leer [`cortex-flow/START_HERE.md`](cortex-flow/START_HERE.md).
2. Activar runtime: `BOOTSTRAP.md` → `SYSTEM_PROMPT.md` → `.ai/orchestrator.md`.
3. Elegir idioma de periferia en `START_HERE.md` (`working_language: es | en | ...`).
4. Crear `definitions/context.md` y `definitions/objective.md` desde los templates en `.ai/templates/`.
5. Ejecutar tu primer flow.

---

## Principios operacionales

- ✅ Nunca ejecutar desde ambigüedad.
- ✅ Activar Discovery si falta contexto.
- ✅ Máximo 3 preguntas por iteración en Discovery.
- ✅ Todo output debe ser persistente y reusable.
- ✅ Toda decisión importante = un ADR.
- ✅ Core en inglés (system prompt, skills, templates). Periferia en tu idioma.

---

## Identidad

| Atributo | Valor |
|---|---|
| **Sistema** | CortexFlow |
| **Abreviatura** | CF |
| **Paradigma** | Flow-Spec Driven Development |
| **Tagline** | *Transforma ambigüedad en flows ejecutables* |
| **Core question** | *¿Qué flow querí hoy?* |

---

## Honestidad de scope

CortexFlow es **un protocolo, no un motor**. La "ejecución" la hace el LLM que lee estos archivos y se autoimpone las reglas. No hay parser, no hay CLI, no hay validador automático. La disciplina la pone el modelo + el operador.

Esto es deliberado: la propuesta de valor está en la **estructura discursiva compartida**, no en una máquina. Si querés capa ejecutable encima (linter de flows, validador de YAML, CLI de bootstrap), es trabajo futuro y aún no existe.

Auditoría técnica completa del estado real del repo: [`cortex-flow/docs/analysis/audit-2026-05-13.md`](cortex-flow/docs/analysis/audit-2026-05-13.md).

> Añade estructura donde la estructura reduce riesgo, y se mantiene liviano donde la flexibilidad sirve al objetivo.
