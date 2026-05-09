# CortexFlow

> *¿Qué flow quieres hoy?*

CortexFlow es un framework de context engineering y sistema de orquestación cognitiva. Proporciona una metodología estructurada para transformar la ambigüedad en intención ejecutable.

El framework guía el razonamiento estructurado a través de flujos declarativos en lugar de prompts improvisacionales. Cada operación deriva de contexto definido, no de suposición.

---

## Filosofía

> **Nunca ejecutes desde la ambigüedad.**

La ambigüedad no es un estado temporal que hay que apresurarse a superar. Es el riesgo principal en cualquier operación de conocimiento. CortexFlow trata la reducción de ambigüedad como una preocupación de primera clase, no como una retrospectiva.

Toda ejecución comienza con contexto estructurado. Todos los outputs trazan de vuelta a intención definida.

---

## ¿Qué Flow Quieres Hoy?

Esta frase define la mentalidad de runtime de CortexFlow.

En lugar de preguntar "¿qué quieres que construya?", el framework pregunta "¿qué proceso cognitivo deberíamos ejecutar?" El operador selecciona o define un flow, y el sistema restringe su razonamiento, outputs y artefactos en consecuencia.

Esto cambia la interacción de solicitudes abiertas a orquestación cognitiva estructurada.

---

## Conceptos Core

| Concepto | Rol |
|---|---|
| **Contexto** | El activo principal. Input estructurado que define la ground truth operacional. |
| **Stories** | Intención cristalizada en forma narrativa. Puente entre ambigüedad y estructura. |
| **Flows** | Rutas de ejecución declarativas. Unidades de orquestación reutilizables que guían el razonamiento. |
| **ADRs** | Architecture Decision Records. Razonamiento capturado para decisiones trascendentales. |
| **Outputs** | Artefactos ejecutables derivados de intención estructurada, no de generación improvisada. |

---

## ¿Qué Es un Flow?

Un Flow es una ruta de ejecución cognitiva estructurada. Es la unidad operativa fundamental de CortexFlow.

Un Flow es:

- una representación declarativa de intención
- una secuencia operacional consciente de contexto
- una unidad de orquestación reutilizable
- un mecanismo de reducción de ambigüedad

Los flows no reemplazan el pensamiento. Lo restringen productivamente. Un flow bien definido preserva la consistencia de intención a través de la ejecución, permite la evolución incremental, y produce evidencia de razonamiento en lugar de outputs opacos.

Ve la [Definición de Flow](definitions/flow-definition.md) para la estructura formal.

---

## Modos de Runtime

CortexFlow opera como un entorno de runtime cognitivo. El modo moldea el comportamiento, restringe los outputs, y define los artefactos esperados.

Modos de runtime disponibles:

| Modo | Propósito |
|---|---|
| **Discovery** | Explorar ambigüedad, estructurar incógnitas, generar definiciones de problema. |
| **Architecture** | Diseñar sistemas, evaluar tradeoffs, producir ADRs. |
| **Implementation** | Generar outputs ejecutables desde especificaciones estructuradas. |
| **Debugging** | Aislar causas de falla, trazar estado, proponer fixes mínimos. |
| **Documentation** | Producir docs reutilizables, explicar sistemas, capturar contexto. |
| **Analysis** | Evaluar sistemas existentes, medir coherencia, identificar drift. |
| **Migration** | Transformar sistemas preservando intención y minimizando riesgo. |
| **Optimization** | Refinar flows, reducir redundancia, mejorar claridad. |

Ve [Modos de Runtime](definitions/runtime-modes.md) para comportamiento detallado por modo.

---

## Ejemplo de Flow

```yaml
flow:
  name: api-contract-migration
  goal: Migrar una API REST interna a OpenAPI 3.1 sin romper consumidores existentes
  context: legacy-api-v2
  inputs:
    - documentación de endpoints existentes
    - ejemplos actuales de request/response
    - suite de tests de integración de consumidores
  constraints:
    - sin breaking changes en estructuras de path
    - todos los campos existentes deben permanecer válidos
    - la migración debe ser reversible
  assumptions:
    - el comportamiento del consumidor está documentado en tests
    - no hay campos deprecados en uso activo
  steps:
    - inventariar endpoints existentes
    - inferir schemas desde ejemplos y tests
    - generar spec OpenAPI 3.1
    - validar compatibilidad hacia atrás
    - producir ADR de migración
  expected_outputs:
    - openapi-3.1.yaml
    - adr-migration.md
    - compatibility-report.md
  validations:
    - todos los tests pasan contra el nuevo contrato
    - no se introducen nuevos campos requeridos
  artifacts:
    - /definitions/contracts/openapi-3.1.yaml
    - /definitions/adr/adr-001-api-migration.md
```

Ve [Ejemplos](examples/) para más flows prácticos.

---

## Por Qué Existe CortexFlow

Los sistemas de IA excellen en generación pero fallan en preservación de intención. La brecha entre "lo que el usuario quiso decir" y "lo que el sistema produjo" es el problema de ambigüedad.

Los enfoques existentes tratan esto como un desafío de prompt engineering. CortexFlow lo trata como un desafío de context engineering y orquestación.

El framework existe porque:

- los prompts no estructurados producen outputs inconsistentes
- las cadenas de llamadas pierden intención entre pasos
- el razonamiento sin estructura produce resultados no verificables
- el contexto se desvía silenciosamente cuando no se gestiona explícitamente

CortexFlow no añade complejidad por su propio bien. Añade estructura donde la estructura reduce riesgo, y permanece ligero donde la flexibilidad sirve al objetivo.

---

## Arquitectura

```
Contexto
    ↓
Stories (intención cristalizada)
    ↓
Flows (ejecución declarativa)
    ↓
ADRs (razonamiento capturado)
    ↓
Outputs (artefactos ejecutables)
```

Este pipeline es el núcleo de Flow-Spec Driven Development.

---

## Identidad

**Sistema:** CortexFlow  
**Abreviatura:** CF  
**Runtime:** CortexFlow Runtime  
**Paradigma:** Flow-Spec Driven Development  
**Tagline:** *Transforma ambigüedad en flows ejecutables*
