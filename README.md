# CortexFlow

> **Transforma ambigüedad en flows ejecutables.**

CortexFlow es un framework de **context engineering** y **orquestación cognitiva**. No genera prompts improvisacionales: estructura intención declarativa, reduce ambigüedad antes de ejecutar, y produce artefactos verificables en lugar de respuestas desechables.

```
Context → Stories → Flows → ADRs → Outputs
```

---

## Cómo se usa 🇨🇱

1. 📁 **Pégale la carpeta** `cortex-flow/` a tu proyecto — puro copy-paste, hermano
2. 🤖 **Dile a tu modelo** (Claude, GPT, lo que tengai) que lea `cortex-flow/START_HERE.md`
3. 💬 **Te va a salir con el famoso**: *"¿Qué flow querí hoy?"* — elegí o descríbele lo que necesitai
4. 🍿 **Explicale la pega y siéntate a mirar**: el runtime estructura, te tinca las preguntas justas, y te deja los artefactos ordenaitos en tu repo

> **Tip de caleta** 🧠: No te pongai a escribir prompts largos pa'l copi. Escribí contexto estructurado nomás. El framework se encarga del resto.

---

## ¿Por qué CortexFlow?

Los sistemas de IA generan bien pero olvidan rápido. La brecha entre *"lo que el usuario quiso decir"* y *"lo que el sistema produjo"* es el problema de ambigüedad.

CortexFlow lo trata como un desafío de **context engineering**, no de prompt engineering:

- Toda ejecución comienza con **contexto estructurado**
- Todo output traza de vuelta a **intención definida**
- Toda decisión trascendental queda **capturada como ADR**

> **Nunca ejecutes desde la ambigüedad.**

---

## Pipeline Canónico

| Etapa | Propósito |
|---|---|
| **Context** | Ground truth del sistema. Input estructurado que define la realidad operacional. |
| **Stories** | Intención cristalizada en forma narrativa. Puente entre ambigüedad y estructura. |
| **Flows** | Rutas de ejecución declarativas. Unidades de orquestación reutilizables. |
| **ADRs** | Architecture Decision Records. Razonamiento capturado para decisiones trascendentales. |
| **Outputs** | Artefactos ejecutables derivados de intención estructurada. |

---

## Modos de Runtime

CortexFlow opera en 8 modos cognitivos. El operador selecciona el modo explícitamente; el runtime nunca lo infiere.

| Modo | Qué hace |
|---|---|
| **Discovery** | Explorar ambigüedad, estructurar incógnitas |
| **Architecture** | Diseñar sistemas, evaluar tradeoffs, producir ADRs |
| **Implementation** | Generar outputs ejecutables desde especificaciones estructuradas |
| **Debugging** | Aislar causas de falla, proponer fixes mínimos |
| **Documentation** | Producir docs reutilizables, capturar contexto |
| **Analysis** | Evaluar sistemas, medir coherencia, detectar drift |
| **Migration** | Transformar preservando intención y minimizando riesgo |
| **Optimization** | Refinar flows, reducir redundancia |

---

## Qué es un Flow

Un Flow es la unidad operativa fundamental de CortexFlow. Es una representación declarativa y estructurada de intención que guía la ejecución cognitiva.

```yaml
flow:
  name: api-contract-migration
  goal: Migrar una API REST interna a OpenAPI 3.1 sin romper consumidores
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

---

## Estructura del Proyecto

El framework completo vive en [`cortex-flow/`](cortex-flow/):

```
cortex-flow/
├── START_HERE.md          ← Empieza aquí
├── BOOTSTRAP.md           ← Contrato de inicio
├── SYSTEM_PROMPT.md       ← Runtime core
├── AGENTS.md              ← Guidelines para agentes
├── .ai/
│   ├── orchestrator.md    ← Orquestador del pipeline
│   ├── skills/            ← Habilidades invocables
│   ├── templates/         ← Plantillas de artefactos
│   └── workflows/         ← Workflows canónicos
├── definitions/
│   ├── flow-definition.md      ← Estructura formal de un Flow
│   ├── runtime-modes.md        ← Definición de modos
│   ├── adr/                    ← Decisiones arquitectónicas
│   ├── stories/                ← Intenciones cristalizadas
│   ├── epics/                  ← Agrupaciones de stories
│   ├── flows/                  ← Definiciones declarativas
│   └── contracts/              ← Contratos fuente de verdad
├── docs/
│   ├── analysis/           ← Reportes de evaluación
│   ├── contracts/          ← Snapshots derivados
│   ├── dependencies/       ← Mapas de dependencias
│   └── flows/              ← Narrativas de ejecución
└── examples/               ← Flows de referencia
```

---

## Identidad

| Atributo | Valor |
|---|---|
| **Sistema** | CortexFlow |
| **Abreviatura** | CF |
| **Runtime** | CortexFlow Runtime |
| **Paradigma** | Flow-Spec Driven Development |
| **Tagline** | *Transforma ambigüedad en flows ejecutables* |
| **Core question** | ¿Qué flow quieres hoy? |

---

## Primeros pasos

1. Lee [`cortex-flow/START_HERE.md`](cortex-flow/START_HERE.md)
2. Activa el runtime: `BOOTSTRAP.md` → `SYSTEM_PROMPT.md` → `.ai/orchestrator.md`
3. Elige tu idioma de periferia en `START_HERE.md`
4. Define tu `definitions/context.md` y `definitions/objective.md`
5. Ejecuta tu primer flow

---

## Principios operacionales

- ✅ Nunca ejecutar desde ambigüedad
- ✅ Activar Discovery mode cuando falte contexto
- ✅ Máximo 3 preguntas por iteración en Discovery
- ✅ Todo output debe ser persistente y reusable
- ✅ Toda decisión importante se registra como ADR
- ✅ El runtime core es inglés; la periferia habla tu idioma

---

*CortexFlow no añade complejidad por su propio bien. Añade estructura donde la estructura reduce riesgo, y permanece ligero donde la flexibilidad sirve al objetivo.*
