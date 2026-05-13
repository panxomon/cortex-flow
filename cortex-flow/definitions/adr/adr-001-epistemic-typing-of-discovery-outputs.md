# ADR-001: Tipado epistemológico de los outputs de Discovery

## Status

Proposed

## Context

El gate de entrada de CortexFlow (Discovery mode) está implementado por:

- `.ai/skills/context-discovery.md`
- `.ai/workflows/repo-analysis.md`
- Templates literales: `context-template.md`, `objective-template.md`,
  `epic-template.md`

El 2026-05-12 se ejecutó un test de Discovery contra un repositorio real
(`dopamain-app`, Angular 21 SPA) bajo protocolo controlado:

- Sólo estructura observable + las 3 priority questions del skill + templates
  as-is.
- Sin contaminación de outputs previos.
- Sin parchear el skill durante el test.

Se compararon los artefactos generados (`context.md` / `objective.md` /
`epic-001.md`) contra los artefactos pre-existentes en
`definitions/dopamain-app/` para el mismo repo.

Hallazgo central observado en los datos:

El framework actual **no contiene primitiva para distinguir el origen
epistemológico** de cada afirmación que produce. Cuatro tipos de información
se aplanan en una sola superficie sintáctica:

| Tipo | Definición |
|------|------------|
| **observado** | derivable de la estructura observable del repo |
| **contextual** | provisto por el operador, frameworks paralelos, memoria externa |
| **inferido** | deducido por el modelo sin verificación |
| **intencional** | proyectado como futuro o deseado, no presente |

Evidencia cuantitativa del `objective.md` pre-existente de `dopamain-app`:
de 15 pantallas listadas en su "Definition of Done" con checkbox `[ ]`,
**9 no existen como código en el repo**. Aparecen mezcladas indistinguiblemente
con las 6 que sí existen.

Evidencia cuantitativa del `context.md` pre-existente: 5 discrepancias
factuales contra el repo (versión de TypeScript, librerías de charts,
dependencias declaradas, mecanismos de persistencia), no detectables por el
flujo actual.

---

## Decision

Se reconoce, sin todavía implementar la corrección, que el modo Discovery —
y por extensión todos los modos que consumen sus outputs — opera bajo una
falla estructural: **ausencia de eje de origen epistemológico en los
artefactos generados**.

Este ADR fija el hallazgo. No introduce cambios en skills, templates o
workflows. La corrección queda como trabajo posterior, condicionada a:

1. Validación cruzada en al menos un segundo repositorio independiente,
   para confirmar que el patrón es propiedad del framework y no del
   dataset específico (`dopamain-app` + contexto Letargico).
2. Rediseño formal de los templates y del skill `context-discovery` con
   tipado epistemológico explícito, sólo después de (1).

Hasta entonces, cualquier output de Discovery debe leerse con el supuesto
de que mezcla las 4 capas sin trazabilidad.

---

## Consequences

### Reales (observables hoy)

- Los modos downstream (Architecture, Implementation) que consumen
  `context.md` / `objective.md` operan sobre artefactos parcialmente
  ficticios sin saberlo. Implementation puede tratar pantallas inventadas
  como backlog real.
- ADRs producidos en modos posteriores heredan la mezcla epistemológica
  sin marcarla.
- La validación interna del framework (test metacircular previo del
  subsistema Mediation) no detectó este fallo porque opera dentro del
  mismo plano sintáctico.

### Deuda técnica registrada

- `context-discovery.md` produce topología plana cuando no hay operador
  con contexto externo; produce narrativa no verificada cuando sí lo hay.
  Modos de falla opuestos según el input.
- `repo-analysis.md` workflow no contiene heurística de lectura de
  sistemas reales (historia, evolución, deuda, fricción estructural).
- Templates (`context-template.md`, `objective-template.md`) son
  receptores pasivos: no obligan a tipar el origen de cada afirmación.

### Riesgos si no se corrige

- Erosión silenciosa de confianza en los outputs del framework a medida
  que se acumulan artefactos con mezcla epistemológica no detectada.
- Cascada de errores en Implementation: trabajo construido sobre
  intenciones tratadas como hechos.
- Imposibilidad de auditar a posteriori qué parte de un artefacto
  reflejaba realidad vs. proyección.

### Beneficios de tener este hallazgo registrado

- Toda decisión futura sobre Discovery, templates y skills queda
  encuadrada por este diagnóstico.
- El test ejecutado queda como evidencia reproducible.
- La distinción entre los 4 tipos de información (observado / contextual
  / inferido / intencional) entra al lenguaje del framework, aunque
  todavía no esté implementada.

### Tradeoff aceptado

Se prioriza fijar el hallazgo antes de corregirlo. Esto deja al framework
operando con el defecto conocido durante el período entre este ADR y el
rediseño posterior. El tradeoff es deliberado: corregir antes de
validar en un segundo repo arriesga sobre-ajuste al caso `dopamain-app`.

---

## Date

2026-05-12
