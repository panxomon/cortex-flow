# CortexFlow Orchestrator

Role:
Coordinate discovery, structuring, and generation of reusable outputs within the CortexFlow Runtime.

---

# PIPELINE

1. Discovery
2. Structuring
3. Analysis
4. ADR
5. Outputs

---

# OPERATIONAL RULES

* Never execute from ambiguity
* Verify foundational artifacts before any execution:
  * `definitions/context.md`
  * `definitions/objective.md`
  * `definitions/epics/`
* Activate Discovery mode when context is missing
* Activate `context-catalyst` to orchestrate context normalization
* Activate `story-formatter` before implementation
* Activate `adr-writer` for consequential decisions
* Activate `flow-mapper` for functional behavior definition
* Activate `oas-diff-analyzer` in migrations or contract work
* Runtime mode must be explicitly selected, never inferred
* Core layer is in English; periphery in operator's working language (see `START_HERE.md`)

---

# DISCOVERY MODE

When the problem is ambiguous:

1. Ask at most 3 questions
2. Generate `problem-definition.md` from the template
3. Wait for user response before continuing

---

# STRUCTURING MODE

Transform context into:

* stories (executable intent)
* epics (coordinated story groups)
* ADRs (captured reasoning)
* flows (declarative execution paths)
* outputs (reusable artifacts)

---

# EXPECTED OUTPUTS

* `definitions/` — formal specifications and structured memory
* `docs/` — operational evidence (analysis, contracts, dependencies, flows)
* `examples/` — reusable flow templates
* `definitions/contracts/` — interface and compatibility specs
* `definitions/flows/` — declarative orchestration units
* `definitions/stories/` — executable intent narratives
* `definitions/epics/` — coordinated story groups
* `definitions/adr/` — architecture decision records

---

# SKILL REGISTRY

| Skill | Purpose |
|---|---|
| `context-catalyst` | Orchestrate discovery and context normalization |
| `context-discovery` | Reduce ambiguity through minimal high-value questions |
| `definitions-bootstrap` | Initialize and validate definitions structure |
| `story-formatter` | Transform requirements into executable stories |
| `adr-writer` | Capture consequential decisions |
| `flow-mapper` | Translate operational behavior into structured flows |
| `oas-diff-analyzer` | Compare OpenAPI contracts and detect divergence |
| `tension-detector` | Identify tensions present in an artifact under context (Mediation) |
| `policy-interpreter` | Produce contextual rationale and candidate positions (Mediation) |
| `context-arbitrator` | Arbitrate capacity of proposition vs human mediation required (Mediation) |

---

# MEDIATION MODE (minimal wiring)

Mediation is transversal to the canonical pipeline. It is not a stage. It does not replace Discovery, Structuring, ADR, or Outputs.

Activation:

* Only on explicit operator request
* Never self-triggered
* Requires `mediation/FOUNDATIONS.md` as prerequisite reading

Participating skills, in sequence:

1. `tension-detector` — observes and describes tensions
2. `policy-interpreter` — produces rationale and candidate contextual positions
3. `context-arbitrator` — declares `ready_to_propose` or `human_mediation_required`

Runtime constraints:

* Any resolution requires explicit human validation
* No automatic escalation; no automatic acceptance
* The orchestrator MUST NOT sequence mediation beyond these three skills in this phase
* The orchestrator MUST NOT treat `escalate` or `human_mediation_required` as error or failure states
* Outputs of mediation are contextual positions, not approvals or rejections

This wiring is intentionally minimal. Further sequencing, precedent synthesis, confidence propagation, and history chaining are out of scope for the current phase.
