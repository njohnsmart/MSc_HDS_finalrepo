# Health Summary Structure

*Original: [`../06-supporting-evidence/Health_Summary_Structure.docx`](../06-supporting-evidence/Health_Summary_Structure.docx)*

## Rationale

Ikarians' patient data arrives from several sources — wearables,
onboarding, the lifestyle survey — in different formats, with markedly
different levels of completeness and reliability. Without a standard
structure, an AI system has to independently reconcile fragmented,
sometimes conflicting data each time it reasons about a patient. This
represents a real risk of inconsistency, particularly when data is missing
rather than simply messy.

A standardised Health Summary gives the AI one consistent representation
of a patient rather than several raw datasets to reconcile itself, and
makes it considerably clearer where a conclusion is well-supported versus
uncertain. It also benefits clinicians directly, as consistent
presentation makes trends and under-assessed areas easier to spot, while
preserving a link back to the original data.

## Design choices

1. **Organised by wellbeing pillar, not by data source.** The five
   pillars already used on the platform — physical, mental, social,
   nutritional, environmental — give a patient-centred view that reflects
   how wellbeing is assessed clinically, rather than a structure convenient
   for engineering.

2. **Each pillar reports status, trend, and confidence.** Confidence
   matters here because some conclusions rest on months of continuous
   wearable data while others rest on a single questionnaire answer;
   collapsing that distinction risks making a weak conclusion appear as
   solid as a strong one.

3. **Incompleteness is stated explicitly, not simply omitted.** If data is
   missing or stale, this should be visible, so clinicians and the AI both
   know where further information is needed before a recommendation is
   made.

4. **Every field retains a link back to its original source.** This
   preserves auditability and supports future review of anything the AI
   generates, while keeping the overall structure consistent across users.

## Fields per pillar

- **Current status**
- **30-day trend** — change since the prior period
- **Key measurements** behind the assessment
- **Confidence** — reflecting the quality and quantity of supporting
  evidence rather than the health status itself, since continuous
  wearable monitoring is inherently more reliable than a single
  self-report, and that distinction needs to be visible
- **A short note** where confidence is limited, so thin evidence is not
  mistaken for a definitive finding
- **Last updated** and **source(s)**, for traceability

## Applications to  Ikarians' actual data

- **Physical wellbeing** is the strongest pillar today — wearable-derived
  sleep, activity and heart-rate data combine into a reasonably confident
  picture.
- **Mental, social, nutritional and environmental** pillars expose the
  gaps identified in the
  [Data Gap Assessment](../03-data-quality-and-value/data-gap-assessment.md):
  mental health limited to a basic stress rating, social and environmental
  data largely absent, nutrition present but inconsistent due to manual
  logging.

These gaps are represented within the summary itself rather than only in
a separate report, deliberately, so that incomplete evidence remains
visible at the point a clinician or AI system is actually making a
decision, supported by an overall completeness indicator showing how many
of the five pillars currently have sufficient information for reliable
interpretation.
