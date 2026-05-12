# Skill: policy-interpreter

## Purpose

Given detected tensions and an active policy, produce contextual rationale and candidate positions. This skill performs situated reading.

## Required reading

Before invoking this skill, read:

- `mediation/FOUNDATIONS.md`
- the active policy file in `mediation/interpretation/policies/`
- relevant tension files in `mediation/interpretation/tensions/`

## Responsibility

This skill interprets. It does not decide.

It must:

- read the active policy as a contextual position, not a law
- for each detected tension, produce rationale situated in the current context
- identify candidate contextual positions consistent with the policy
- expose tradeoffs implied by each candidate position
- flag when the policy is silent on a detected tension
- flag when the policy's limits are reached by the context

It must not:

- select a final resolution
- suppress tensions the policy does not explicitly address
- produce universal judgments
- produce numeric scores as primary output
- enact operational authority

## Authority boundary

Policy interpretation **informs mediation; it does not enact operational authority**. The rationale and candidate positions produced by this skill are advisory, contextual, precedent-aware, and revisable.

## Input

- detected tensions (from tension-detector)
- active policy
- declared context

## Output

- per-tension rationale chain
- candidate contextual positions with explicit tradeoffs
- explicit flags when the policy is silent on a tension
- explicit flags when a policy limit is reached

## Stopping condition

This skill stops when rationale and candidate positions are produced. Selection is not this skill's responsibility.

## Failure mode

If the policy is silent or the context does not support situated reading, surface that explicitly. Do not fabricate policy intent.
