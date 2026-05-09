# definitions/flows

Definiciones declarativas de flows: rutas de ejecución cognitiva
estructurada. Unidad operativa fundamental de CortexFlow.

Cada archivo aquí es una unidad de orquestación reutilizable que sigue la
estructura formal definida en `definitions/flow-definition.md`.

Estos son la fuente de verdad. La evidencia de su ejecución vive en
`docs/flows/`.

## Cuándo crear un flow

- El comportamiento operacional necesita ser declarativo y reproducible
- Existen inputs, constraints y outputs concretos verificables
- El proceso se va a ejecutar más de una vez con variaciones de input

## Convenciones

- Nombre: `nombre-corto.md` o `nombre-corto.yaml`
- Idioma: el del operador para descripción; estructura YAML estándar
- Cada `expected_output` debe tener un `artifact` con ruta concreta

## Especificación

Ver `definitions/flow-definition.md`.

---

## Ejemplo

```yaml
flow:
  name: documentar-endpoints-backend
  goal: Producir un inventario verificable de endpoints expuestos por el backend
  context: backend-idp
  inputs:
    - código fuente del backend
    - configuración de routing
    - tests de integración existentes
  constraints:
    - no modificar código fuente del backend
    - el inventario debe regenerarse de forma idempotente
  assumptions:
    - los endpoints están registrados en código, no inyectados en runtime
    - los tests de integración cubren los endpoints principales
  steps:
    - escanear definiciones de rutas en el código
    - extraer método, path, parámetros y schema asociado
    - cruzar con tests de integración para validar cobertura
    - identificar endpoints sin contrato declarado
    - generar inventario en docs/backend/endpoints.md
  expected_outputs:
    - inventario de endpoints
    - lista de gaps (endpoints sin contrato)
  validations:
    - todo endpoint del código aparece en el inventario
    - los gaps están explícitamente listados, no omitidos
  artifacts:
    - docs/backend/endpoints.md
    - docs/analysis/endpoints-gaps.md
```

La narrativa de ejecución de este flow vive en `docs/flows/documentar-endpoints-backend.md`.
