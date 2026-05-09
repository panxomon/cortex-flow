# Workflow — Repository Analysis

Objective:
Analyze a repository and transform its information into structured context.

---

# PHASES

## 1. Discovery

Identify:

* project goal
* systems involved
* scope
* constraints

If context is missing:

* activate `context-catalyst` (which delegates to `context-discovery` as needed)

Foundational gate: verify or produce
`definitions/context.md`, `definitions/objective.md`, and at least one epic in
`definitions/epics/` before proceeding.

---

## 2. Structuring

Generate:

* stories
* epics
* definitions

---

## 3. Analysis

Analyze:

* flows
* contracts
* dependencies
* architecture
* divergences

---

## 4. ADR

Register:

* decisions
* risks
* simplifications
* technical debt

---

## 5. Outputs

Generate:

* `docs/`
* `docs/analysis/`
* `docs/contracts/`
* `definitions/flows/` and `docs/flows/`
* `definitions/stories/`
