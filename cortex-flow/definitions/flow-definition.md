# What Is a Flow

A Flow is the fundamental operational unit of CortexFlow. It is a declarative, structured representation of intent that guides cognitive execution.

---

## Purpose

Flows exist to reduce ambiguity. They make intent explicit, constrain reasoning to productive paths, and produce execution evidence instead of opaque outputs.

A Flow does not replace thinking. It structures it.

---

## Formal Structure

```yaml
flow:
  name: identifier
  goal: declarative statement of intent
  context: reference to ground truth
  inputs: required inputs
  constraints: non-negotiable limits
  assumptions: things taken for granted
  steps: ordered operational sequence
  expected_outputs: what the flow must produce
  validations: how to verify correctness
  artifacts: where outputs are stored
```

---

## Field Definitions

### `name`
A stable identifier for the flow. Must be descriptive and unique within its domain.

Example: `api-contract-migration`, `onboarding-user-journey`, `database-schema-evolution`

### `goal`
A single declarative sentence stating what the flow intends to achieve. It is the north star against which all steps are evaluated.

Example: *Migrate an internal REST API to OpenAPI 3.1 without breaking existing consumers*

### `context`
Reference to the structured ground truth informing this flow. Can be a document, a repository state, a prior ADR, or an external system description.

Example: `legacy-api-v2`, `system-context-adr-004`

### `inputs`
List of specific inputs required for the flow to execute. The absence of any input is a blocker, not a workaround opportunity.

Example:
```yaml
inputs:
  - existing endpoint documentation
  - current request/response examples
  - consumer integration test suite
```

### `constraints`
Non-negotiable limits the flow must respect. Constraints shape the solution space by exclusion.

Example:
```yaml
constraints:
  - no breaking changes to path structures
  - all existing fields must remain valid
  - migration must be reversible
```

### `assumptions`
Things taken for granted. Assumptions are risks made explicit. If an assumption proves false, the flow must be re-evaluated.

Example:
```yaml
assumptions:
  - consumer behavior is documented in tests
  - no deprecated fields are in active use
```

### `steps`
Ordered operational sequence. Each step is an action, not an aspiration. Steps should be verifiable and atomic when possible.

Example:
```yaml
steps:
  - inventory existing endpoints
  - infer schemas from examples and tests
  - generate OpenAPI 3.1 spec
  - validate backward compatibility
  - produce migration ADR
```

### `expected_outputs`
Concrete deliverables the flow must produce. These are commitments, not hopes.

Example:
```yaml
expected_outputs:
  - openapi-3.1.yaml
  - adr-migration.md
  - compatibility-report.md
```

### `validations`
Criteria for verifying the flow succeeded. Validations may be automated (tests) or manual (reviews).

Example:
```yaml
validations:
  - all consumer integration tests pass against the new contract
  - no previously optional field becomes required
```

### `artifacts`
Filesystem paths or references where outputs are stored. Artifacts are the persistent evidence of flow execution.

Example:
```yaml
artifacts:
  - definitions/contracts/openapi-3.1.yaml
  - definitions/adr/adr-001-api-migration.md
```

---

## Flow Characteristics

| Characteristic | Description |
|---|---|
| **Declarative** | Declares intent, not implementation details |
| **Context-aware** | Anchored in defined context, not assumptions |
| **Reusable** | Can be instantiated with different inputs and contexts |
| **Inspectable** | Structure is readable, reviewable, versionable |
| **Evolvable** | Can be incrementally refined without losing intent |
| **Evidence-producing** | Generates artifacts, not disposable replies |

---

## Relationship to Other Concepts

| Concept | How the Flow Relates |
|---|---|
| **Context** | The Flow executes within defined context. Context is the ground; the flow is the path through it. |
| **Story** | Stories crystallize intent. Flows operationalize stories into executable structure. |
| **Epic** | Epics group stories. Flows execute the work that fulfills the epic. |
| **ADR** | Consequential decisions within a flow are captured in ADRs. The Flow references ADRs; ADRs do not replace flows. |
| **Output** | Flows produce outputs as defined artifacts. Outputs are evidence of flow completion. |

---

## Anti-Patterns

A Flow is **not**:

- A prompt template
- A rigid script with no room for reasoning
- A wishlist without validation criteria
- A description of what someone *should* do without defining *how to know it was done*

A bad flow is indistinguishable from a task list. A good flow constrains reasoning while preserving room for intelligence to operate within those constraints.
