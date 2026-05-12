# Dimension: security

> Observes the exposure of an artifact to misuse, unauthorized access, data leakage, and integrity compromise under a given context.

---

## Signals it observes

- handling of inputs from untrusted sources
- authentication and authorization boundaries
- presence of secrets, credentials, or sensitive data in the artifact
- treatment of sensitive data in transit and at rest
- trust assumptions expressed or implied
- failure behavior under adversarial conditions

---

## Interpretation heuristics

- trust assumptions that are implicit are concerns regardless of context
- handling of sensitive data must be evaluated against the declared context of the artifact
- absence of authorization boundaries is a concern in systems with multiple actors, regardless of maturity
- security signals carry weight that does not scale linearly with policy tolerance

---

## Confidence notes

- high confidence: explicit threat model, defined trust boundaries, known data classifications
- low confidence: implicit trust assumptions, undefined data classifications, unclear actor model

---

## Related tensions

- innovation-vs-stability
