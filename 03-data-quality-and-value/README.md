# 03 — Data Quality and Value

**Placement stage:** Weeks 4–5 · Is the data reliable, which parts carry
genuine analytical value, and what is missing?

## Rationale

Having mapped what data exists (Section 02), the next question was whether
any of it could be trusted as is. Volume does not equal usefulness ;this
stage assessed reliability, distinguished meaningful signal from noise,
and identified what the platform was not capturing at all.

## Approach

Reviewing the User, Patient, Device and Sensor datasets for completeness
and consistency, classifying variables by analytical value, and producing
a gap assessment across five wellbeing pillars, each grounded in specific
clinical evidence and paired with a concrete, validated instrument as a
remedy.

## Contents

| File | What it is |
|---|---|
| [`data-quality-assessment.md`](data-quality-assessment.md) | A dataset-by-dataset review of completeness, consistency and known issues |
| [`signal-vs-noise.md`](signal-vs-noise.md) | Which variables carry genuine analytical value |
| [`data-gap-assessment.md`](data-gap-assessment.md) | What is missing across five wellbeing pillars, why it matters, and what to add |

## Significance

This is the point at which the platform's data stopped being treated as
uniformly usable. It produced a concrete list of what needs cleaning
before use (filtering invalid heart-rate readings, extracting metadata),
what to deprioritise, and which validated clinical instruments (WHO-5,
PHQ-9/GAD-7, UCLA-3) would close the largest gaps for the smallest added
burden on users.

## Limitation

This assessment is based on reviewing the datasets and documentation
rather than a statistical audit of live production data. Findings on
completeness and consistency are structural and documentation-based
observations rather than computed metrics such as duplication counts.

## Link to Subsequent Work

These findings, particularly on which data is reliable enough to use, set
the requirements for [`04-ai-readiness/`](../04-ai-readiness/): a
framework for deciding when data of a given quality is safe to hand to an
AI model.
