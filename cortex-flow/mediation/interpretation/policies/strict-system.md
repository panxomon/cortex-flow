# Policy: strict-system

> Contextual position for systems where operational predictability, auditability, and integrity outweigh speed of delivery and capability expansion.

---

## Context of application

- regulated domains
- systems with external dependents or contractual obligations
- infrastructure and security-critical components
- long-lived systems with multiple maintainer generations
- environments where failures carry organizational, legal, or human cost

---

## Position on canonical tensions

- tension: delivery-speed-vs-maintainability — position: favor maintainability
  - rationale: long-term comprehensibility is a precondition for safe operation; speed is subordinate to structural integrity

- tension: innovation-vs-stability — position: favor stability
  - rationale: operational predictability is a core obligation; innovation must pass through explicit architectural review

- tension: simplicity-vs-abstraction — position: balance, favor explicit abstraction when it improves auditability
  - rationale: implicit patterns resist review; explicit abstraction aligned with the domain improves long-term verification

---

## Priorities

1. security and integrity of system behavior
2. auditability and traceability of decisions
3. architectural alignment with declared boundaries
4. operational predictability over velocity

---

## Tolerances

- tolerates slower delivery in exchange for traceable reasoning
- tolerates explicit complexity when it improves auditability
- tolerates duplication only when extraction would blur trust boundaries

---

## Limits

- does not accept undocumented trust assumptions
- does not accept boundary violations without an accompanying ADR
- does not accept untraceable changes in critical paths
- does not accept debt without an explicit expiration and revisit condition
- does not accept innovation outside declared change channels
