# definitions/contracts

Contratos fuente de verdad: especificaciones de interfaz que definen cómo
se comunican los componentes del sistema.

Es la **fuente de verdad** del contrato. Los snapshots, diffs y derivados
viven en `docs/contracts/`.

## Cuándo vive aquí un contrato

- Es la especificación canónica que el sistema honra (no una observación)
- Está versionado y se publica a consumidores
- Cambios sobre este archivo requieren consideración de compatibilidad
  hacia atrás

## Tipos de contrato soportados

- OpenAPI / Swagger (REST)
- AsyncAPI (eventos, queues, websockets)
- Protobuf (gRPC)
- JSON Schema (payloads, configuraciones)
- GraphQL SDL

## Convenciones

- Nombre: `<dominio>-<version>.<ext>` (e.g. `payments-v1.yaml`)
- Idioma: la descripción dentro del contrato sigue el idioma del operador;
  la estructura del formato se respeta tal cual lo define el estándar
- Cambios breaking se acompañan de un ADR en `definitions/adr/`

---

## Ejemplo (OpenAPI 3.1, fragmento)

```yaml
# definitions/contracts/payments-v1.yaml
openapi: 3.1.0
info:
  title: Payments API
  version: 1.0.0
  description: |
    Contrato fuente de verdad para el servicio de pagos. Cualquier
    divergencia entre este contrato y la implementación se trata como bug
    de la implementación, no del contrato.
servers:
  - url: https://api.example.com/v1
paths:
  /payments:
    post:
      summary: Crear un pago
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/PaymentRequest'
      responses:
        '201':
          description: Pago creado
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Payment'
        '400':
          description: Request inválido
components:
  schemas:
    PaymentRequest:
      type: object
      required: [amount, currency]
      properties:
        amount:
          type: integer
          minimum: 1
        currency:
          type: string
          enum: [USD, EUR, CLP]
    Payment:
      type: object
      required: [id, status, amount, currency]
      properties:
        id:
          type: string
          format: uuid
        status:
          type: string
          enum: [pending, completed, failed]
        amount:
          type: integer
        currency:
          type: string
```

Snapshots y comparaciones (e.g. v1 vs v2) viven en `docs/contracts/`.
Análisis de divergencias se generan con la skill `oas-diff-analyzer` y se
publican en `docs/analysis/`.
