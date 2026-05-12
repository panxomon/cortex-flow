# Runtime Modes

CortexFlow operates as a cognitive runtime environment. A mode is not a label. It is a behavioral contract that shapes reasoning, constrains outputs, and defines expected artifacts.

The runtime mode must be selected explicitly. It is never inferred.

---

## Mode Selection

The operator selects a mode by declaring it. The runtime then enforces the corresponding behavioral contract.

The core prompt of CortexFlow expresses this:

> *What flow do you want today?*

This is shorthand for: *In which cognitive mode should the runtime operate, and which flow should it execute within that mode?*

---

## Available Modes

### Discovery

**Purpose:** Explore ambiguity, structure unknowns, generate problem definitions.

**Behavior:**
- Ask questions instead of proposing solutions
- Generate structured markdown (Problem Definition format)
- Map existing context, identify gaps
- Resist the urge to solve before defining

**Artifacts:**
- Problem definitions
- Context maps
- Gap analyses
- Structured questions for the operator

**Example prompt:**
> "We need a new payments system."
> Response: Activate Discovery mode. Generate problem definition. Ask clarifying questions about currencies, compliance, existing integrations.

---

### Architecture

**Purpose:** Design systems, evaluate tradeoffs, produce decisions.

**Behavior:**
- Propose designs, not implementations
- Evaluate alternatives against constraints
- Capture consequential decisions as ADRs
- Define interfaces and contracts before building

**Artifacts:**
- Architecture Decision Records (ADRs)
- System diagrams and component maps
- Interface contracts
- Risk assessments

**Example prompt:**
> "Design the auth service."
> Response: Activate Architecture mode. Generate auth-service-adr.md comparing OAuth2 vs custom token strategies. Define API contract. Do not generate code.

---

### Implementation

**Purpose:** Generate executable outputs from structured specifications.

**Behavior:**
- Build only from defined flows and stories
- Produce code, configuration, tests
- Validate against constraints stated in the flow
- Stop immediately if the specification is ambiguous

**Artifacts:**
- Source code
- Configuration files
- Test suites
- Deployment manifests

**Example prompt:**
> "Build the auth API."
> Response: Verify existing flow. If none, stop and request Architecture mode first. If a flow exists, activate Implementation mode and generate code against the spec.

---

### Debugging

**Purpose:** Isolate failure causes, trace state, propose minimal fixes.

**Behavior:**
- Gather evidence before hypothesizing
- Trace execution path and state changes
- Propose the smallest change that resolves the issue
- Validate that the fix does not violate existing constraints

**Artifacts:**
- Root-cause analyses
- Execution traces
- Patch definitions
- Regression tests

**Example prompt:**
> "The payments webhook fails intermittently."
> Response: Activate Debugging mode. Request logs, configuration, recent changes. Trace failure patterns. Propose a minimal fix with test coverage.

---

### Documentation

**Purpose:** Produce reusable docs, explain systems, capture context.

**Behavior:**
- Explain how and why, not just what
- Target an explicit audience (new team member, external consumer, future self)
- Capture context that is currently tacit
- Structure for discoverability and maintenance

**Artifacts:**
- Technical documentation
- Operational guides
- Knowledge base entries
- Context-preservation documents

**Example prompt:**
> "Document the payments flow."
> Response: Activate Documentation mode. Identify audience. Capture current state, decision history, operational procedures. Produce structured docs.

---

### Analysis

**Purpose:** Evaluate existing systems, measure coherence, identify drift.

**Behavior:**
- Measure against defined constraints and flows
- Identify where reality diverges from specification
- Evaluate technical debt and risk exposure
- Propose prioritized improvements, not random refactoring

**Artifacts:**
- Evaluation reports
- Gap analyses
- Drift assessments
- Prioritized recommendations

**Example prompt:**
> "How healthy is our auth system?"
> Response: Activate Analysis mode. Compare current implementation against ADRs and flows. Identify drift. Measure test coverage, dependency freshness, known vulnerabilities.

---

### Migration

**Purpose:** Transform systems while preserving intent and minimizing risk.

**Behavior:**
- Define the target state as precisely as the current state
- Identify invariants that must hold across the transition
- Produce a reversible plan
- Validate at each stage, not only at the end

**Artifacts:**
- Migration plans
- Compatibility matrices
- Rollback procedures
- Validation checkpoints

**Example prompt:**
> "Migrate from REST to gRPC."
> Response: Activate Migration mode. Inventory current API. Define target contract. Identify breaking vs non-breaking changes. Produce a staged migration plan with validation gates.

---

### Optimization

**Purpose:** Refine flows, reduce redundancy, improve clarity.

**Behavior:**
- Measure before changing
- Prefer clarity over cleverness
- Remove structure that no longer serves a purpose
- Preserve intent while improving execution efficiency

**Artifacts:**
- Refined flows
- Simplified specifications
- Performance benchmarks
- Reduction reports (what was removed and why)

**Example prompt:**
> "This flow takes too long to execute."
> Response: Activate Optimization mode. Profile execution. Identify bottlenecks. Propose flow refinements. Validate that outputs remain equivalent.

---

### Mediation

**Purpose:** Contextualize tensions around the enactment of generated or existing artifacts. Produce contextual positions, not verdicts.

**Required reading before activation:** `mediation/FOUNDATIONS.md`.

**Behavior:**
- Operate transversally to the canonical pipeline; never replace it
- Activate only on explicit operator request; never self-trigger
- Identify tensions present in an artifact under a given context
- Interpret those tensions through the active policy
- Propose a contextual position, or surface that human mediation is required
- Produce rationale as primary output; any score is auxiliary

**Constraints:**
- Mediation does not supersede artifact authorship. It contextualizes tensions around enactment.
- Mediation stabilizes contextual positions, not universal truths.
- Stabilization is provisional, contextual, and revisable through new tensions, precedents, or reframing.
- Mediation does not produce approvals or rejections. It produces traceable positions.
- Mediation is proposal-first and human-mediated for stabilization.

**Artifacts:**
- Tension reports
- Contextual positions with rationale
- Mediation requests (when human arbitration is needed)
- Precedents (only after human resolution)

**Example prompt:**
> "Mediate the contextual acceptability of this new module against the startup-mvp policy."
> Response: Activate Mediation mode. Detect tensions. Interpret them through startup-mvp policy. Propose a position or surface ambiguity for human mediation. Do not approve, reject, or modify the artifact.

---

## Mode Transitions

Modes are not isolated. A typical lifecycle might be:

```
Discovery → Architecture → Implementation → Documentation → Analysis → Optimization
```

However, the operator must explicitly authorize each transition. The runtime does not assume that completing Implementation means Documentation should begin. The operator decides which flow to execute next.

---

## Mode Violations

The runtime must refuse to operate on a mode mismatch:

| Request | Active mode | Response |
|---|---|---|
| "Build this now" | Discovery | Stop. Architecture mode required before Implementation. |
| "Just fix it" | Implementation | Stop. Debugging mode required. Request evidence. |
| "Design the system" | Implementation | Stop. Already in build phase. Generate ADR if design changes are needed. |

These stops are not obstacles. They are the framework doing its job: preventing execution from ambiguity.
