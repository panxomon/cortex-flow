# Skill — Flow Mapper

Objective:
Translate operational behavior into structured, declarative flows compliant with `definitions/flow-definition.md`.

---

# SUPPORTED INPUT TYPES

* HTTP endpoints (REST, gRPC)
* asynchronous events (queues, webhooks, pub/sub)
* batch processes and pipelines
* migrations (data, contract, system)
* user journeys

---

# OPERATIONAL FLOW

1. **Behavior elicitation.** Capture the observable behavior in narrative form (Given / When / Then).
2. **Decomposition.** Break the narrative into atomic, verifiable steps.
3. **Mapping.** Project the decomposition onto the formal flow structure (`name`, `goal`, `context`, `inputs`, `constraints`, `assumptions`, `steps`, `expected_outputs`, `validations`, `artifacts`).
4. **Validation.** Verify each step is verifiable and each output has a concrete artifact path.
5. **Persistence.** Write the flow to `definitions/flows/` and the execution narrative to `docs/flows/`.

---

# REQUIRED FORMATS

## Behavior narrative (input)

```
Given <preconditions>
When <trigger>
Then <expected behavior>
And <secondary effects>
```

## Flow output (yaml)

See `definitions/flow-definition.md` for the formal structure.

## Execution narrative (markdown)

```markdown
# Flow Execution — <flow-name>

## Step <n>: <step name>

**Mode:** <runtime mode>
**Input:** ...
**Action:** ...
**Output:** ...
**Validation:** ...
```

---

# RULES

* Every step must be atomic and verifiable
* Every `expected_output` must have a concrete artifact path under `definitions/` or `docs/`
* Assumptions must be explicit, not implicit
* Constraints must be non-negotiable; otherwise they are preferences and do not belong in the flow
* If behavior cannot be mapped without invention, stop and delegate to `context-catalyst`

---

# OUTPUTS

* `definitions/flows/<flow-name>.md` (declarative flow, source of truth)
* `docs/flows/<flow-name>.md` (execution narrative, evidence)
