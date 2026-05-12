# Tension: simplicity-vs-abstraction

> The conflict between keeping a system minimal and concrete and introducing abstractions that enable reuse, extension, or conceptual clarity.

---

## Competing concerns

- keeping the system minimal, concrete, and easy to read in isolation
- introducing abstractions that enable reuse, flexibility, or conceptual clarity

---

## Common contexts where it emerges

- recurring patterns emerging in the codebase
- proposed extraction of shared libraries or modules
- early architecture decisions with uncertain future needs
- refactoring sessions after feature maturity

---

## Typical tradeoffs

- favoring simplicity: lower cognitive load, easier onboarding, local clarity, potential duplication, harder reuse later
- favoring abstraction: enables reuse and extension, reduces duplication, raises cognitive load, risk of abstraction misaligned with future needs

---

## Related dimensions

- maintainability
- architectural-alignment

---

## Related tensions

- delivery-speed-vs-maintainability
