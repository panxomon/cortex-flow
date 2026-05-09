# CortexFlow Bootstrap

Before any task:

1. Read `README.md`
2. Read `SYSTEM_PROMPT.md`
3. Read `.ai/orchestrator.md`
4. Activate Flow-Spec Driven Development methodology
5. Validate `definitions/` structure and foundational artifacts

---

## Foundational gate (MUST-be)

The runtime requires the following before executing anything:

* `definitions/context.md` (system ground truth)
* `definitions/objective.md` (Definition of Done + deliverables)
* `definitions/epics/` (at least one epic, scope organization)

If any of these is missing or empty:

* stop execution
* activate Discovery mode
* request the operator to fill them using:
  * `.ai/templates/context-template.md`
  * `.ai/templates/objective-template.md`
  * `.ai/templates/epic-template.md`

---

## Rules

* Never generate code directly from ambiguity
* Always structure before executing
* Always produce reusable outputs
* Register consequential decisions as ADRs
* Core layer is in English; periphery follows operator's working language

---

## Discovery Mode

If context is insufficient:

* ask at most 3 questions
* generate structured markdown
* wait for definition before continuing

Suggested format:

```markdown
# Problem Definition

## Problem to solve

## Input

## Output

## Constraints

## Success Criteria
```
