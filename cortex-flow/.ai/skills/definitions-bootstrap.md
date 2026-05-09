# Skill — Definitions Bootstrap

Objective:
Initialize and validate the base structure required for Flow-Spec Driven Development.

---

# RESPONSIBILITIES

Validate or create:

* `definitions/`
* `definitions/context.md` (MUST-be)
* `definitions/objective.md` (MUST-be)
* `definitions/epics/` (MUST-be)
* `definitions/stories/`
* `definitions/adr/`
* `definitions/flows/`
* `definitions/contracts/`
* `docs/`
* `docs/analysis/`
* `docs/contracts/`
* `docs/dependencies/`
* `docs/flows/`

---

# FOUNDATIONAL GATE

The runtime must verify before any execution:

* `definitions/context.md` exists and is non-empty
* `definitions/objective.md` exists and is non-empty
* `definitions/epics/` exists and contains at least one epic

If any check fails:

* stop execution
* activate Discovery mode
* point the operator to the corresponding template in `.ai/templates/`

---

# RULES

* Never start execution without the base structure
* Validate workspace consistency
* Maintain clear separation between:
  * AI runtime (`.ai/`)
  * Structured memory (`definitions/`)
  * Operational evidence (`docs/`)

---

# EXPECTED OUTPUT

A workspace prepared for:

* discovery
* analysis
* documentation
* generation of reusable outputs
