# definitions/stories

Intención cristalizada en forma narrativa. Cada story es una unidad de
trabajo ejecutable con outputs concretos y criterios de validación.

## Cuándo crear una story

- Tienes un requerimiento que cabe en una unidad pequeña de trabajo
- El requerimiento tiene outputs verificables
- La story se puede asociar a un epic existente

## Convenciones

- Nombre: `NN-nombre-corto.md` (NN secuencial, 2 dígitos)
- Idioma: el del operador
- Tamaño: si una story crece demasiado, dividir antes de ejecutar

## Template

Ver `.ai/templates/story-template.md`.

---

## Ejemplo

```markdown
# Story 03 — Documentar consumo del frontend

## Name

Documentar cómo el frontend consume los endpoints del backend.

## Context

El frontend (`bech-idp`) consume múltiples endpoints REST y eventos
WebSocket del backend (`backend-idp`). No existe documentación que mapee
qué vista consume qué endpoint, lo cual dificulta el análisis de impacto
ante cambios de contrato.

## Action

- Inventariar las llamadas HTTP y suscripciones WebSocket en el frontend
- Mapear cada llamada al endpoint backend correspondiente
- Identificar consumos que no tienen contrato declarado
- Documentar el resultado en `docs/frontend/consumption.md`

## Expected Output

- `docs/frontend/consumption.md` con tabla vista → endpoint → contrato
- Lista de gaps (consumos sin contrato) en la misma documentación

## Validation Criteria

- Toda vista del frontend aparece mapeada al menos a un endpoint o evento
- Los gaps quedan registrados como hallazgo y, si son trascendentales,
  como ADR
- El documento es revisable por alguien sin acceso al código frontend
```
