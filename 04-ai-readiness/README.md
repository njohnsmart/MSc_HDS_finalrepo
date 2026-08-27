# 04 — AI Readiness

**Placement stage:** Weeks 6–7 · how should raw, messy health data be
transformed before an AI model is allowed to reason over it?

## Rationale

Ikarians' AI engine generates patient- and clinician-facing insights
directly from platform data. The Data Quality and Gap work in Section 03
made clear that raw data — invalid sensor readings, free-text clinical
notes, metrics hidden in metadata, unvalidated self-ratings — is not
uniformly safe to hand to that engine. This stage asked what actually has
to be true of a piece of data before an AI system should be trusted with
it.

## Approach

Designing a five-stage readiness framework (Raw → Validated → Aggregated →
Contextualised → AI-Ready) that sets a minimum bar for data reaching an AI
model or a patient/clinician-facing output; designing a standardised
Health Summary structure for presenting a patient's status to an AI
system; and defining prioritisation criteria for which data investments
matter most.

## Contents

| File | What it is |
|---|---|
| [`ai-readiness-framework.md`](ai-readiness-framework.md) | The five-stage model, from raw data through to an AI-ready summary |
| [`health-summary-structure.md`](health-summary-structure.md) | A standardised, pillar-based way of presenting a patient to an AI system |
| [`data-prioritisation.md`](data-prioritisation.md) | What is worth fixing or collecting next, and why |

## Significance

This gives Ikarians a reusable standard rather than a one-off
recommendation for deciding when data is safe to use, and a design for how
an AI system should represent its own confidence rather than defaulting to
silence. It turns "make our data AI-ready" into something closer to an
auditable checklist.

## Limitation

This is a design proposal rather than an implemented pipeline; it was not
tested against live data volumes or evaluated for computational overhead
at each stage. Confidence, as defined here, reflects the reliability of
the input data rather than a guarantee that every AI-generated sentence is
actually supported by it — a limitation the framework names explicitly
rather than resolves.

## Link to Subsequent Work

This framework, particularly its emphasis on validation, directly shaped
the tool proposals in
[`05-product-and-strategy/`](../05-product-and-strategy/), including a
sensor plausibility check that implements Stage 2 (Validated) of this
framework made concrete.
