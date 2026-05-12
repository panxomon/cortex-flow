# Policy: startup-mvp

> Contextual position for early-stage products operating under time-to-market pressure, where learning from real users takes precedence over long-term structural optimality.

---

## Context of application

- pre-product-market-fit stage
- small teams with high cognitive continuity
- short delivery cycles
- reversibility of most decisions in the short term
- limited external dependents on the system

---

## Position on canonical tensions

- tension: delivery-speed-vs-maintainability — position: favor delivery speed
  - rationale: learning from real usage outweighs long-term maintainability costs at this stage; debt is acceptable if traceable

- tension: innovation-vs-stability — position: favor innovation
  - rationale: capability exploration is a survival trait for early-stage products; operational risk is bounded by small user base

- tension: simplicity-vs-abstraction — position: favor simplicity
  - rationale: future needs are unknown; premature abstraction is a higher risk than local duplication

---

## Priorities

1. security for any user data handled by the system
2. ability to deliver and iterate quickly
3. traceability of accepted tradeoffs
4. recoverability from wrong decisions

---

## Tolerances

- tolerates duplication until a pattern is observed at least three times
- tolerates technical debt when the debt is recorded and has a revisit condition
- tolerates deviation from surrounding conventions when context is documented
- tolerates partial test coverage in exploratory paths

---

## Limits

- does not accept implicit handling of user credentials or sensitive data
- does not accept untraceable accepted tradeoffs
- does not accept deviations from declared security boundaries
- does not accept debt without a revisit condition
