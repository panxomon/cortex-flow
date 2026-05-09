# definitions/adr

Architecture Decision Records. Decisiones trascendentales del proyecto con su razonamiento.

## Cuándo crear un ADR

- Existe una divergencia entre opciones razonables
- Hay un tradeoff con consecuencias duraderas
- Cambia el diseño de un componente o contrato
- Se introduce deuda técnica intencional
- Aparece ambigüedad crítica que requiere resolución explícita

## Convenciones

- Nombre: `adr-NNN-titulo-corto.md` (NNN secuencial, 3 dígitos)
- Idioma: el del operador (working_language)
- Inmutabilidad: un ADR no se reescribe; se marca `Superseded by ADR-YYY` y se crea uno nuevo

## Template

Ver `.ai/templates/adr-template.md`.

---

## Ejemplo

```markdown
# ADR-007: Adoptar PostgreSQL como base de datos primaria

## Status

Accepted

## Context

El servicio necesita persistencia transaccional con consultas relacionales
complejas. Las opciones evaluadas fueron PostgreSQL, MySQL y DynamoDB. El
equipo tiene experiencia operativa fuerte con PostgreSQL y la carga esperada
no justifica un motor distribuido.

## Decision

Usar PostgreSQL 16 como base de datos primaria. Acceso vía un único schema
por bounded context. Migraciones gestionadas con `golang-migrate`.

## Consequences

### Positivas
- Soporte transaccional ACID nativo
- Ecosistema maduro de herramientas (pgAdmin, pg_dump, pgBouncer)
- Experiencia interna directa

### Negativas
- Escalado horizontal requiere replicación o sharding manual
- Operación de alta disponibilidad añade complejidad

### Neutras
- DynamoDB queda descartado para este servicio, pero sigue disponible para
  cargas de bajo costo en otros servicios

## Date

2026-05-08
```
