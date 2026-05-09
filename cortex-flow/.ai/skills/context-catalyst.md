# Skill — Context Catalyst

Objective:
Transform ambiguous requirements into reusable structured context. Acts as the entry-point orchestrator for the Discovery phase.

---

# RESPONSIBILITIES

* discovery orchestration
* ambiguity reduction
* context normalization
* problem-definition generation
* foundational artifact bootstrapping (`context.md`, `objective.md`, first epic)

---

# WHEN TO ACTIVATE

* The operator opens a new project with no `definitions/context.md` or `definitions/objective.md`
* A request arrives without enough ground truth to map to a flow
* Multiple incompatible interpretations of the requirement exist
* The runtime detects drift between stated intent and observable artifacts

---

# OPERATIONAL FLOW

1. **Inventory.** Scan workspace for existing context (README, prior ADRs, prior stories, code structure).
2. **Gap detection.** Identify missing foundational artifacts and undefined boundaries.
3. **Discovery delegation.** Invoke `context-discovery` for at most 3 high-value questions per iteration.
4. **Normalization.** Consolidate operator answers into:
   * `definitions/context.md` (using `.ai/templates/context-template.md`)
   * `definitions/objective.md` (using `.ai/templates/objective-template.md`)
5. **Story bridging.** Hand off to `story-formatter` once context is sufficient.
6. **Decision capture.** Invoke `adr-writer` when normalization produces consequential choices (e.g. scope boundaries, source-of-truth assignment).

---

# INTEGRATIONS

| Skill | Relationship |
|---|---|
| `context-discovery` | Delegated for question-driven elicitation |
| `definitions-bootstrap` | Verifies workspace structure before delegating |
| `story-formatter` | Receives normalized context to crystallize into stories |
| `adr-writer` | Records boundary, scope, and source-of-truth decisions |

---

# RULES

* Never produce stories or flows before `context.md` and `objective.md` exist
* Never invent context: ambiguity is a stop signal, not a fill-in
* Maximum 3 questions per iteration (inherited from `context-discovery`)
* Every consequential framing decision is captured as ADR
* Output language follows the operator's working language

---

# OUTPUTS

* `definitions/context.md`
* `definitions/objective.md`
* optional: `definitions/epics/00-bootstrap.md` as scope seed
* optional: `definitions/adr/adr-NNN-*.md` for framing decisions
