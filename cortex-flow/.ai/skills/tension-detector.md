# Skill: tension-detector

## Purpose

Identify which canonical tensions are present in a given artifact under a given context. Describe them. Do nothing else.

## Required reading

Before invoking this skill, read:

- `mediation/FOUNDATIONS.md`
- `mediation/interpretation/tensions/canonical/`

## Responsibility

This skill is strictly observational.

It must:

- detect signals in the artifact under the declared context
- identify possible tensions present
- map observed conflicts to canonical tensions when appropriate
- surface candidate emergent tensions when no canonical match fits

It must not:

- interpret the tensions
- assign intent to the author of the artifact
- infer human causality
- resolve meaning
- propose resolutions
- invoke a policy
- produce scores

## Input

- artifact under consideration
- declared context (system, domain, stage, constraints)

## Output

- list of detected tensions
- for each tension:
  - canonical reference or candidate emergent descriptor
  - observable evidence in the artifact that signaled its presence
  - concerns in conflict

## Epistemic status of output

Detected tensions are **interpretive candidates, not authoritative findings**. They mark where mediation may be useful, not where failure has occurred.

## Stopping condition

This skill stops when tensions have been described. It does not continue into interpretation.

## Failure mode

If the context is insufficient to detect tensions reliably, surface that explicitly instead of inferring. Under-detection is preferable to hallucinated tensions.
