# definitions/epics

Agrupaciones coordinadas de stories. Un epic organiza el alcance del
proyecto en bloques temáticos con un objetivo común.

Es uno de los tres artefactos fundacionales (MUST-be) del framework, junto
con `definitions/context.md` y `definitions/objective.md`.

## Cuándo crear un epic

- Existen múltiples stories que comparten un mismo objetivo de alto nivel
- Necesitas un horizonte de avance que abarque varias unidades de trabajo
- El alcance del proyecto se beneficia de agruparse por área temática

## Convenciones

- Nombre: `NN-nombre-corto.md` (NN secuencial, 2 dígitos)
- Idioma: el del operador
- Cada epic referencia las stories que lo componen

## Template

Ver `.ai/templates/epic-template.md`.

---

## Ejemplo

```markdown
# Epic 01 — Pipeline de catalogación

## Goal

Documentar y formalizar el pipeline end-to-end que cataloga repositorios y
produce los artefactos derivados (README, OpenAPI, metadata).

## Scope

Incluye:
- Flujo de ejecución de los steps del pipeline
- Inputs y outputs de cada step
- Mecanismos de persistencia intermedia
- Manejo de errores y reintentos

Excluye:
- Generación de documentación con IA (cubierto en Epic 05)
- Visualización del progreso en frontend (cubierto en Epic 03)

## Stories

- `stories/01-pipeline-catalogacion.md` — flujo end-to-end del pipeline
- `stories/04-generacion-artefactos.md` — outputs del pipeline
- `stories/08-persistencia-estado.md` — almacenamiento intermedio

## Success criteria

- El pipeline está documentado en `docs/pipeline/flow.md`
- Cada step tiene contrato de input/output declarado
- Los gaps detectados durante el análisis están registrados como ADR

## Dependencies

- Epic 02 (Contratos backend) — los contratos de los steps se declaran allí
```
