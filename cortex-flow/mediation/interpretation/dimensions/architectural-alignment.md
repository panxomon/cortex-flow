# Dimension: architectural-alignment

> Observes the degree to which an artifact is coherent with the declared architecture, its boundaries, and its intent.

---

## Signals it observes

- respect for declared layer or module boundaries
- coherence with existing architectural decisions (ADRs)
- direction of dependencies
- consistency with defined interfaces and contracts
- conceptual fit with the domain model

---

## Interpretation heuristics

- a boundary crossing is not a failure; it is a signal that either the artifact or the boundary needs re-examination
- deviation from an ADR is a signal that either the ADR is outdated or the artifact is misplaced
- unexpected dependency directions often indicate missing abstractions or missing context
- alignment without rationale is not alignment; it is conformity

---

## Confidence notes

- high confidence: architecture is documented, ADRs exist, boundaries are explicit
- low confidence: architecture is implicit, no ADRs, boundaries are inferred from usage

---

## Related tensions

- delivery-speed-vs-maintainability
- innovation-vs-stability
- simplicity-vs-abstraction
