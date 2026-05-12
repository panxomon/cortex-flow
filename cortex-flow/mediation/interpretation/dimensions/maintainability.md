# Dimension: maintainability

> Observes how comprehensible, modifiable, and safely changeable an artifact is for future work, under a given context.

---

## Signals it observes

- clarity of intent expressed by the artifact
- coupling between components
- cohesion within components
- presence or absence of contextual documentation
- consistency with surrounding conventions
- depth of implicit knowledge required to modify the artifact

---

## Interpretation heuristics

- high coupling raises future modification cost; whether this matters depends on the expected lifetime of the artifact
- low cohesion suggests the artifact carries more than one responsibility; this may be acceptable in early exploration
- missing contextual documentation is a concern when the artifact lives in a system with multiple maintainers
- deviation from surrounding conventions is a signal of friction, not necessarily of wrong design

---

## Confidence notes

- high confidence: stable codebase, known conventions, clear ownership
- low confidence: early exploration, rapidly changing requirements, no established conventions yet

---

## Related tensions

- delivery-speed-vs-maintainability
- simplicity-vs-abstraction
