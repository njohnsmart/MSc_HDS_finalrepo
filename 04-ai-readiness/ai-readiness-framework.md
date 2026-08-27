# AI Readiness Framework

*Original: [`../06-supporting-evidence/ai_readiness_framework.docx`](../06-supporting-evidence/ai_readiness_framework.docx)*

## Purpose

A consistent way of deciding whether a given piece of health data is fit
for an AI system to use, rather than leaving that as an ad-hoc,
developer-by-developer judgement call, which is roughly the situation
found at the start of this stage.

**The core rule:** data should not reach an AI model until it has reached
**Stage 4**. Only Stage 5 data should be used to generate anything
patient- or clinician-facing.

## The five stages

### Stage 1 — Raw

Data exactly as it arrives: wearable output, free-text survey responses,
and so on. No checks applied yet; may contain duplicates, impossible
values (a 2 bpm heart rate, for instance), or inconsistent formatting.
Reference only — this should never reach a dashboard or an AI model.

### Stage 2 — Validated

Impossible values are removed using rules specific to the measurement type
— heart rate, sleep score and SpO₂ each require different plausible
ranges, so a single generic check is not sufficient. Duplicates removed,
free text standardised. At this point the data is technically reliable,
but still represents individual observations rather than anything
clinically meaningful.

### Stage 3 — Aggregated

Validated readings summarised over meaningful time windows. Simple
averages were considered and rejected here, as they can obscure genuine
change. Instead, values are expressed relative to the person's own
baseline: not "71 bpm average" but "71 bpm this week, up 4 bpm from the
4-week baseline of 67." This surfaces a trend rather than an isolated
number.

### Stage 4 — Contextualised

Aggregated data is annotated with three pieces of metadata before
reaching an AI system: when it was recorded, where it came from, and how
reliable that source is. Without this, a model cannot distinguish a
six-hour-old wearable reading from a six-month-old one, or a validated
device reading from something manually entered. "71 bpm, measured six
hours ago via Garmin, high confidence" is considerably more useful than
"71 bpm" alone.

### Stage 5 — AI-Ready

Contextualised data is converted into short, plain-language summaries,
organised by health domain. One design decision considered important
here is that **domains with no data must say so explicitly**, rather than
being left blank. An empty section is too easily misread, by a model or a
clinician, as "no concerns" when it in fact means "no information at
all." This is treated as the minimum bar for data to safely inform
AI-assisted decisions.

## Current readiness of Ikarians' data

- **Medical history and medications** are not yet there — largely free
  text. Standardising against **ICD-10, SNOMED CT** (conditions) and
  **RxNorm** (medications) would meaningfully improve reliability here.
- **Mental wellbeing, nutrition, and social/environmental health** are
  either absent or barely captured (see the
  [Data Gap Assessment](../03-data-quality-and-value/data-gap-assessment.md)),
  and should be collected using the validated instruments already
  identified there — WHO-5, PHQ-2/9, GAD-2/7, UCLA-3, a short dietary
  measure.

## Making absence and uncertainty visible

- **No data for a domain** → an explicit flag, so the AI registers that
  nothing is known rather than assuming "no concerns."
- **Incomplete or unreliable data** → a low-confidence flag with a short
  explanation, applied to free text, incomplete wearable streams, or
  unstandardised fields.
- **Human-review flag** — for anything requiring clinician sign-off before
  AI-generated advice reaches a patient, for example a PHQ-9 score of 14.
  This could reasonably be extended to cover any AI output touching
  possible diagnoses or medication advice.

**Where this framework falls short:** confidence, as defined here,
describes how reliable the input data is, not whether every sentence an
AI system produces is actually supported by it. This is a genuine
limitation of the framework

## Units and Measurement type

Every measurement needs an explicit unit and measurement type attached
before it reaches the AI. As covered in the
[Data Quality Assessment](../03-data-quality-and-value/data-quality-assessment.md),
the same numeric field can represent heart rate, a sleep score, or SpO₂
depending on sensor type; without an attached unit, there is no reliable
way for the AI to interpret what a number represents.
