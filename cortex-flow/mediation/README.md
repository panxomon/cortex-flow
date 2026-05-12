# Mediation Subsystem

This subsystem is the contextual mediation layer of CortexFlow.

Before reading anything else here, read `FOUNDATIONS.md`.

`FOUNDATIONS.md` defines what this subsystem is, what it is not, and the invariants that govern its evolution. The rest of this folder is implementation. The foundations are constitutional.

---

## Reading order

1. `FOUNDATIONS.md` — operational constitution. Required.
2. This README — navigational entry point.
3. The subdirectories — incremental phases of construction.

---

## Current state

The subsystem is being constructed in phases. The current phase is **Phase 1 — Ontology**, which establishes only the conceptual foundations and the directory skeleton.

Subsequent phases will populate semantic models, runtime behavior, and organizational memory. No phase begins until the previous one is stable.

---

## Phases

| Phase | Focus | Status |
|---|---|---|
| 1 — Ontology | Foundational invariants and structure | In progress |
| 2 — Semantic model | Templates and canonical content for tensions, dimensions, policies, precedents | Pending |
| 3 — Mediation runtime | Skills, orchestration, mediation mode, resolution runtime | Pending |
| 4 — Organizational memory | Active precedents, temporality, decay models, adaptive recalibration | Pending |

---

## Structure

```
mediation/
├── FOUNDATIONS.md
├── README.md
└── interpretation/
    ├── tensions/
    │   ├── canonical/
    │   └── emergent/
    ├── dimensions/
    ├── policies/
    └── precedents/
```

`interpretation/` is the conceptual core of the subsystem. Tensions, dimensions, policies, and precedents are the materials that contextual interpretation operates on.

Folders that do not yet exist (`temporality/`, `signals/`, `resolutions/`) will be introduced only when their phase begins. They are intentionally absent now to avoid premature structure.

---

## Operating principle for contributors

Do not introduce abstractions, folders, or runtime behavior that contradict `FOUNDATIONS.md`.

If a contribution requires changing an invariant, the change is a foundational event and must be recorded as a foundational ADR before any structural change is made.
