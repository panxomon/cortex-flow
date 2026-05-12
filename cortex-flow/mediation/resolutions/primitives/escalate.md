# Primitive: escalate

## Meaning

The situation exceeds the interpretive capacity available at the current mediation layer. It must be raised to a human mediator with broader contextual authority.

Escalation is **not failure**. It is a recognition of interpretive limits, contextual insufficiency, or operational consequences significant enough to warrant broader arbitration.

## What it is

- insufficient contextual stability at the current layer
- tensions that exceed the active policy's reach
- operational consequences that require broader human judgment
- a routing signal, not a verdict

## What it is not

- an error
- a failure of the artifact
- a failure of the system
- exception handling
- a rejection

## Required fields

- originating tension(s)
- specific reason for escalation (one or more of: insufficient context, policy limit reached, operational consequences, ambiguity beyond interpretation)
- what a broader mediator needs to know
- what the proposing layer already assessed

## Drift risk

If `escalate` starts being treated as an error state in the runtime, the vocabulary has drifted. Escalation produces a new mediation event with more context; it does not terminate a pipeline with failure.
