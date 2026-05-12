# Skill: context-arbitrator

## Purpose

Determine whether the current interpretation has enough contextual stability to propose a position, or whether the situation requires explicit human mediation.

## Required reading

Before invoking this skill, read:

- `mediation/FOUNDATIONS.md`
- outputs of tension-detector and policy-interpreter for the current case

## Responsibility

This skill arbitrates **capacity of proposition**. It does not arbitrate truth or authority.

It must:

- assess whether rationale chains are coherent and context is sufficient
- assess whether ambiguity is bounded and interpretive state is stable
- decide between two arbitration states only
- surface the reasons for its assessment

It must not:

- select or propose resolutions
- approve or reject artifacts
- override human mediation once requested
- produce scores as primary output
- act as a governance gate

## Arbitration states

One of two states, each carrying reasoning:

- `ready_to_propose`: context is stable enough for the runtime to surface candidate positions to the operator. This is not approval of any position.
- `human_mediation_required`: context is ambiguous, tensions exceed policy, or interpretive stability is low. This state means **insufficient contextual stability for autonomous progression**, not **rejected pending approval**.

## Input

- detected tensions
- interpretation output (rationale, candidate positions, flags)
- declared context

## Output

- arbitration state (one of the two above)
- reasoning chain justifying the state
- pointers to the tensions, flags, or ambiguities that informed the arbitration

## Stopping condition

This skill stops once the arbitration state is declared.

## Failure mode

When in doubt, default to `human_mediation_required`. Over-escalation is cheaper than false contextual stability. This default is intentional and should not be tuned toward autonomy over time.
