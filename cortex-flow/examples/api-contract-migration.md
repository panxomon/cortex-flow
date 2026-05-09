# Ejemplo de Flow: Migración de Contrato API

Un ejemplo práctico de un CortexFlow para migrar una API REST legacy a un contrato OpenAPI 3.1 sin romper consumidores existentes.

---

## Contexto

Tu organización tiene una API REST legacy (v2) que creció orgánicamente durante años. Carece de un contrato formal. Los consumidores dependen del comportamiento observado. Necesitas introducir una especificación OpenAPI 3.1 sin romper nada.

---

## El Flow

```yaml
flow:
  name: api-contract-migration
  goal: Migrar una API REST interna a OpenAPI 3.1 sin romper consumidores existentes
  context: legacy-api-v2
  inputs:
    - documentación de endpoints existentes (aunque sea informal)
    - ejemplos actuales de request/response desde logs o tests
    - suite de tests de integración de consumidores
    - muestras de tráfico de producción (si disponibles)
  constraints:
    - sin breaking changes en estructuras de path
    - todos los campos existentes deben permanecer válidos
    - la migración debe ser reversible dentro de 48 horas
    - sin cambios requeridos en código de consumidores
  assumptions:
    - el comportamiento del consumidor está documentado en tests
    - no hay campos deprecados en uso activo por consumidores principales
    - el tráfico de producción representa patrones de uso típicos
  steps:
    - inventariar todos los endpoints y métodos existentes
    - recolectar ejemplos de request/response por endpoint
    - inferir schemas desde ejemplos, tests y tráfico
    - generar especificación OpenAPI 3.1 draft
    - validar compatibilidad hacia atrás contra tests de consumidores
    - identificar y resolver brechas de contrato
    - producir ADR de migración con plan de rollback
    - publicar especificación y notificar consumidores
  expected_outputs:
    - openapi-3.1.yaml
    - adr-migration.md
    - compatibility-report.md
    - consumer-notification.md
  validations:
    - todos los tests de integración de consumidores pasan contra el nuevo contrato
    - ningún campo previamente opcional se vuelve requerido
    - ningún tipo de campo se estrecha (string → integer)
    - la especificación valida con swagger-parser o equivalente
  artifacts:
    - /definitions/contracts/openapi-3.1.yaml
    - /definitions/adr/adr-001-api-migration.md
    - /definitions/analysis/compatibility-report.md
    - /docs/consumer-notification.md
```

---

## Narrativa de Ejecución

### Paso 1: Inventario

El runtime activa modo Discovery. Le pide al operador cualquier documentación existente, escanea el codebase en busca de definiciones de rutas, y produce un inventario estructurado.

### Paso 2: Inferencia de Schemas

El runtime activa modo Analysis. Examina ejemplos de request/response e infiere tipos, campos requeridos, y valores de enum. Marca inferencias inciertas como assumptions para validar.

### Paso 3: Generación de Especificación

El runtime activa modo Implementation. Genera el YAML OpenAPI 3.1 desde los schemas inferidos. No inventa campos. Solo formaliza lo que fue observado.

### Paso 4: Validación de Compatibilidad

El runtime ejecuta la suite de tests de consumidores contra el nuevo contrato. Si los tests fallan, activa modo Debugging, traza el mismatch, y propone un fix o una relajación de constraints.

### Paso 5: ADR y Rollback

El runtime activa modo Architecture. Captura la decisión de migrar, los constraints honrados, las assumptions hechas, y el procedimiento exacto de rollback.

### Paso 6: Publicación

El runtime activa modo Documentation. Produce documentación orientada a consumidores y una notificación describiendo qué cambió y qué no.

---

## Por Qué Este Es un Buen Flow

- **La intención es explícita:** El goal es inequívoco. El éxito es definible.
- **Los inputs están listados:** El runtime sabe qué necesita antes de comenzar.
- **Los constraints moldean la solución:** El requerimiento de cero cambios en consumidores elimina muchos atajos tentadores.
- **Las assumptions están expuestas:** Si los tests de consumidores son inadecuados, el operador lo sabe inmediatamente.
- **La validación es concreta:** Tests pasando es la gate, no un vago "se ve bien."
- **Los artefactos son localizables:** Los outputs tienen rutas definidas. Son descubribles y revisables.

---

## Variaciones

| Variación | Cambio |
|---|---|
| API Greenfield | Remover constraints de backward-compatibility. Agregar "diseñar para versionado futuro" como goal. |
| API Pública | Agregar paso de revisión de gobernanza. Agregar constraint de política de deprecación. |
| Migración a GraphQL | Cambiar formato de output. Agregar paso de mapeo de resolvers. |

Estas variaciones reus la misma estructura de flow con diferentes inputs y constraints. Esto es lo que hace a los flows reutilizables.
