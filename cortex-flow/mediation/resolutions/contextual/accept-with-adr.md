# Contextual resolution: accept-with-adr

> A contextual composition built on the `accept` primitive, where acceptance is conditioned on recording the reasoning as an Architecture Decision Record.

## Meaning

The artifact is contextually acceptable, but the tensions involved carry enough structural weight that the rationale must be stabilized into an ADR for future reference.

The ADR becomes durable context. It does not become authority.

## Composition

- primitive: `accept`
- conditioned on: creation of a corresponding ADR in `definitions/adr/`

## When it is appropriate

- the tension touches architectural boundaries
- the rationale is likely to inform future mediations
- the acceptance assumes specific architectural conditions that must remain true
- the context would be lost if not captured as durable reasoning

## When it is not appropriate

- the tension is local and transient
- the rationale does not carry architectural weight
- capturing the decision would overstate its significance

## Required fields

- all fields required by `accept`
- reference to the ADR (`definitions/adr/adr-XXX-...md`)
- statement of the architectural conditions the acceptance depends on
- statement of what would invalidate the acceptance

## Relationship to authority

The ADR provides durable reasoning, not final authority. If the architectural conditions change, the acceptance is automatically open for reframing. An ADR linked here is a precondition of the resolution, not a guarantor of permanence.

## Drift risk

If ADRs linked here begin to be treated as closing arguments rather than durable context, the semantic balance is lost. The ADR is context. The resolution is the contextual position. They are not the same.
