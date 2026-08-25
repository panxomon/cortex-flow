# AGENTS.md - CortexFlow Agent Guidelines

## Overview

This repository implements **CortexFlow**, a context engineering framework and cognitive orchestration system. It transforms ambiguity into executable intent through structured flows rather than improvisational prompts.

**Runtime:** CortexFlow Runtime  
**Paradigm:** Flow-Spec Driven Development  
**Tagline:** *Transforma ambigüedad en flows ejecutables*

## Core Philosophy

> **Nunca ejecutes desde la ambigüedad.**

The framework treats ambiguity reduction as a first-class concern, not a retrospective afterthought. All execution begins with structured context. All outputs trace back to defined intent.

### Key Principles

1. **Context first** - No operation begins without structured ground truth
2. **Never execute from ambiguity** - Ambiguity signals stop-and-define, not proceed-with-assumptions
3. **All execution derives from a flow** - Flows are the sole source of operational truth
4. **All consequential decisions are captured** - Reasoning lives in ADRs, not memory
5. **All flows produce reusable evidence** - Outputs are artifacts, not disposable answers

---

## Workflow: Flow-Spec Driven Development

The canonical pipeline is strict and non-negotiable:

```
Context → Stories → Flows → ADRs → Outputs
```

No step is skipped. No step is simulated.

### Pipeline Components

| Stage | Purpose |
|-------|---------|
| **Context** | Ground truth, structured input that defines operational reality |
| **Stories** | Crystallized intent in narrative form; bridge between ambiguity and structure |
| **Flows** | Declarative execution paths; reusable orchestration units |
| **ADRs** | Captured reasoning for consequential decisions |
| **Outputs** | Executable artifacts derived from structured intent, not improvised generation |

---

## Runtime Modes

CortexFlow operates in distinct cognitive modes. The mode must be explicitly selected, never inferred.

| Mode | Behavior | Artifacts |
|------|----------|-----------|
| **Discovery** | Explore ambiguity, structure unknowns, generate problem definitions | Problem definitions, context maps |
| **Architecture** | Design systems, evaluate tradeoffs, produce decisions | ADRs, system diagrams, contracts |
| **Implementation** | Build from structured specifications | Code, configs, tests |
| **Debugging** | Isolate failure causes, trace state, propose minimal fixes | Root cause analysis, patch definitions |
| **Documentation** | Produce reusable docs, explain systems, capture context | Docs, guides, knowledge bases |
| **Analysis** | Evaluate existing systems, measure coherence, identify drift | Reports, gap analyses, recommendations |
| **Migration** | Transform systems preserving intent and minimizing risk | Migration plans, compatibility matrices |
| **Optimization** | Refine flows, reduce redundancy, improve clarity | Refined flows, performance gains |

---

## Operational Rules

- ✅ Never execute from ambiguity
- ✅ Activate discovery mode when context is missing
- ✅ Ask at most 3 questions per iteration in discovery mode
- ✅ Always produce reusable outputs
- ✅ Register consequential decisions as ADRs
- ✅ Explicitly select runtime mode
- ✅ Activate story-formatter before implementation
- ✅ Activate adr-writer for consequential decisions
- ✅ Activate flow-mapper for functional behavior definition
- ✅ Activate oas-diff-analyzer in migrations or contract work

---

## Discovery Mode Protocol

When context is insufficient:

1. **Stop execution immediately**
2. **Ask at most 3 structural questions**
3. **Generate problem-definition.md** using the template
4. **Wait for user response before continuing**

### Problem Definition Template

Use this structure when activating discovery mode:

```markdown
# Problem Definition

## Problem to solve

Describe clearly the main problem.

---

## Input

What does the system receive?

Examples: repositories, documentation, prompts, events, requests

---

## Output

What should the system produce?

Examples: stories, definitions, documentation, flows, contracts, code

---

## Constraints

What limitations exist?

Examples: language, architecture, performance, compliance, time

---

## Success Criteria

How do we know the result is correct?

Examples: validated equivalence, aligned contracts, documented flows, successful tests
```

---

## Flow Structure

A Flow is the fundamental operational unit of CortexFlow. Every flow follows this structure:

```yaml
flow:
  name: identifier
  goal: declarative statement of intent
  context: reference to ground truth
  inputs:
    - required item 1
    - required item 2
  constraints:
    - non-negotiable limit 1
    - non-negotiable limit 2
  assumptions:
    - given fact 1
    - given fact 2
  steps:
    - operational step 1
    - operational step 2
  expected_outputs:
    - output artifact name
  validations:
    - verification criterion
  artifacts:
    - /path/to/artifact
```

### Flow Characteristics

- Reduces ambiguity by making intent explicit
- Guides reasoning by restricting operational paths
- Preserves consistency by defining expected behavior
- Enables evolution by being versionable and inspectable

---

## Output Locations

| Location | Purpose |
|----------|---------|
| `/definitions` | Formal specifications and contracts |
| `/docs` | Documentation and guides |
| `/examples` | Reusable flow templates |
| `stories/` | Executable intent narratives |
| `adr/` | Architecture decision records |
| `analysis/` | Evaluation and assessment reports |
| `contracts/` | Interface and compatibility specs |
| `flows/` | Declarative orchestration units |

---

## Templates Reference

### Problem Definition Template

Location: `.ai/templates/problem-definition.md`

Use for discovery mode outputs.

### Story Template

Location: `.ai/templates/story-template.md`

Use before implementation phase. Structure: Name, Context, Action, Expected Output, Validation Criteria.

### ADR Template

Location: `.ai/templates/adr-template.md`

Use for consequential decisions. Structure: Context, Decision, Consequences (simplifications, technical debt, risks, benefits, tradeoffs).

---

## Skills Available

Located in `.ai/skills/`:

| Skill | Purpose |
|-------|---------|
| `context-discovery.md` | Discover and structure ambiguous context |
| `definitions-bootstrap.md` | Bootstrap definition structures |
| `story-formatter.md` | Format stories before implementation |
| `adr-writer.md` | Write ADRs for consequential decisions |
| `flow-mapper.md` | Map functional behavior definitions |
| `oas-diff-analyzer.md` | Analyze OpenAPI diff changes |

### Workflows

Located in `.ai/workflows/`:

- `repo-analysis.md` - Repository analysis workflow

### Orchestrator

The orchestrator coordinates discovery, structuring, and generation of reusable outputs. It enforces the pipeline and mode selection rules.

---

## Code Style Guidelines

### Formatting

- Use 2-space indentation
- Prefer compact YAML over verbose formatting
- Use descriptive field names in flows (name, goal, context, inputs, constraints, assumptions, steps, expected_outputs, validations, artifacts)
- Keep flow definitions under 100 lines when possible
- Use horizontal rules (`---`) to separate major sections

### Import/Include Conventions

This repository uses Markdown-based composition. Include related flows/documents using:

```markdown
<!-- See: /definitions/flow-definition.md for formal structure -->
<!-- Related: adr-002-cortexflow-rebrand.md for recent architectural decisions -->
```

No external package managers or module systems are used. All dependencies are document-based.

### Naming Conventions

| Element | Convention | Examples |
|---------|------------|----------|
| Flows | kebab-case with domain prefix | `api-contract-migration`, `context-discovery` |
| ADRs | `adr-XXX-title.md` format | `adr-002-cortexflow-rebrand.md` |
| Stories | descriptive lowercase | `user-authentication-story.md` |
| Templates | lowercase with hyphens | `problem-definition.md` |
| Artifacts | kebab-case in paths | `openapi-3.1.yaml`, `compatibility-report.md` |

### Error Handling

This framework operates on **explicit failure modes**:

1. **Ambiguity detected** → Activate discovery mode, generate problem definition
2. **Context missing** → Request specific inputs before proceeding
3. **Validation failed** → Trace to constraint violation, propose minimal fix
4. **Contract mismatch** → Generate compatibility report with rollback plan

Never proceed with assumptions about missing context or ambiguous requirements.

### Type System

Types are expressed through:

- YAML field schemas in flow definitions
- Markdown section headers for document structure
- Explicit examples in constraints and validations sections

No type annotations or schema files exist outside of flow specifications.

---

## ADR Guidelines

Write an ADR when:

1. Making a consequential architectural decision
2. Evaluating tradeoffs between alternatives
3. Documenting non-obvious design choices
4. Recording assumptions that constrain future options

### ADR Structure

```markdown
# ADR-XXX: Title

## Context

Describe the situation encountered.

---

## Decision

What decision was made?

---

## Consequences

What impact does it have?

May include: simplifications, technical debt, risks, benefits, tradeoffs
```

### ADR Numbering

Use sequential numbering starting from 001. Format: `adr-XXX-title.md`

Example: `adr-002-cortexflow-rebrand.md`

---

## Story Guidelines

Stories crystallize intent into executable narratives. Use the story template before implementation.

### Story Structure

```markdown
# Story Name

## Context

Describe the problem or need.

---

## Action

What should be done?

---

## Expected Output

What artifacts or results should be produced?

Examples: markdown, OAS, analysis, documentation, code, flows

---

## Validation Criteria

How do we validate it's complete?

Examples: aligned contracts, equivalent flows, documented endpoints, recorded divergences
```

---

## First Action Protocol

When encountering a new request or ambiguous context:

1. **Read** `README.md`
2. **Read** `BOOTSTRAP.md`
3. **Read** `SYSTEM_PROMPT.md`
4. **Read** `.ai/orchestrator.md`
5. **Review** available skills in `.ai/skills/`

If context is insufficient:

1. Activate context-discovery workflow
2. Use problem-definition template
3. Wait for definition before continuing

---

## Valid Outputs

Do not produce outputs outside these locations or formats:

- `/definitions` - Formal specifications and contracts
- `/docs` - Documentation and guides
- `stories/` - Executable intent narratives
- `adr/` - Architecture decision records
- `analysis/` - Evaluation and assessment reports
- `flows/` - Declarative orchestration units
- `contracts/` - Interface and compatibility specs

All outputs must be reusable artifacts, not disposable responses.

---

## Quick Reference Commands

This repository uses Markdown-based composition with no build system:

### Analysis

```bash
# List all flows
find . -name "*.md" -path "*/examples/*" | xargs grep "^flow:" 

# List all ADRs
ls -la definitions/adr/

# Read a flow definition
cat examples/api-contract-migration.md
```

### Template Usage

```bash
# Copy problem definition template
cp .ai/templates/problem-definition.md new-problem.md

# Copy story template
cp .ai/templates/story-template.md new-story.md

# Copy ADR template
cp .ai/templates/adr-template.md adr-XXX-title.md
```

---

## Identity

| Attribute | Value |
|-----------|-------|
| **System** | CortexFlow |
| **Abbreviation** | CF |
| **Runtime** | CortexFlow Runtime |
| **Paradigm** | Flow-Spec Driven Development |
| **Tagline** | Transforma ambigüedad en flows ejecutables |
| **Core Question** | ¿Qué flow quieres hoy? |
