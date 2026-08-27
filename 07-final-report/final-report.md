# Final Report: MSc Health Data Science Placement — Ikarians


**Full portfolio:** see the [repository README](../README.md) for section-by-section detail; this report is a single-document summary of that work.

---

## Executive Summary

Ikarians is an early-stage digital health platform combining 
wearable data, a one-off onboarding questionnaire and a daily in-app
lifestyle survey to power an AI engine that generates patient - and
clinician-facing health insights. The purpose of this placement was not
to build production systems, but to help Ikarians turn this multi-source
data into something structured, reliable and genuinely usable for
AI-driven insight.

Across the placement, the data ecosystem was mapped from scratch, assessed
for quality and analytical value, evaluated for AI-readiness, and
translated into three concrete, explainable tool proposals.The platform
already collects data with real clinical value ;particularly from
wearable sensors, but a meaningful share of that value is either
buried in the metadata, recorded as unvalidated free text, or
captured inadequately in domains like mental health, social connection and
environment.

The core recommendation carried through every stage is that **improving
the reliability of existing data should take priority over collecting
more of it.** Missing data is at least visible as a gap; poor quality data
can silently produce misleading AI-generated insights. Where new data
collection is justified, brief validated instruments (WHO-5, PHQ-9/GAD-7,
UCLA-3) were consistently favoured over open-ended logging, to protect the
platform's low-friction user experience.

## Background and Approach

Ikarians' underlying philosophy draws on Value-Based Healthcare and
longevity research, including the Blue Zones literature, with an emphasis
on extending healthy life expectancy rather than simply treating disease.
Working alongside the founding and technical team, the placement's role
was to develop an independent, evidence-based understanding of the
platform's health data ; critically engaging with existing assumptions
rather than only documenting the platform as it stood.

Recommendations throughout were grounded in a structured literature base
covering physical activity, sleep, mental health, nutrition, social
relationships and longevity, alongside Ikarians' own internal clinical
reference material (see
[`01-project-context/evidence-landscape.md`](../01-project-context/evidence-landscape.md)
for the full evidence base; the internal material itself is proprietary
and is not reproduced in this portfolio).

## Summary of Work by Stage

### 1. Familiarisation (Week 1)

Initial review of the product, its clinical reasoning and the app itself
surfaced a recurring tension that shaped the rest of the placement: the
onboarding's quick 1–10 self-rating scales support fast, low-friction data
collection, but offer far less standardisation and clinical
interpretability than validated instruments. This, alongside an early gap
identified in social-health data, motivated a hybrid approach;retaining
fast daily check-ins while introducing short validated instruments at
onboarding and at defined follow-up intervals.

→ [`01-project-context/week-1-observations.md`](../01-project-context/week-1-observations.md)

### 2. Health Data Mapping (Weeks 2–3)

Working alongside the team to map out the platform's existing data infrastructure provided an opportunity to aggregate technical knowledge into a single reference point which included
An ecosystem map, a technical data-flow diagram, a source catalog linking each metric to the specific AI feature it feeds, and a formal data dictionary.
Connecting each data point directly to the AI action it drives turned out to be particularly useful, as it made it much easier to see where the strongest clinical signal was coming from later on.

→ [`02-health-data-mapping/`](../02-health-data-mapping/)

### 3. Data Quality and Value (Weeks 4–5)

Reviewing the sample dataset confirmed that User and Device data were solid, but highlighted a few practical ways to get more out of the Sensor table.
For instance, the main value field needs to be read alongside sensor_type to make sense, and a lot of valuable clinical detail ;like heart-rate peaks, stress markers, 
and recovery scores—lives inside nested metadata fields where standard queries might miss it.
A few basic data cleaning points were also noted, such as filtering out occasional impossible sensor values (like negative heart rates) and relying on timestamps rather than IDs for strict chronological order.

The signal vs noise analysis confirmed that physical-health metrics
dominate the platform's current high-value signal, while mental
wellbeing, social health and lifestyle factors are comparatively thin —
motivating the gap assessment, which set out specific, evidence-based,
low-burden instruments (WHO-5, PHQ-2/9, GAD-2/7, UCLA-3, a short
Mediterranean Diet Adherence Score) to close the largest gaps for the
smallest added onboarding burden.
→ [`03-data-quality-and-value/`](../03-data-quality-and-value/)

### 4. AI Readiness (Weeks 6–7)

To help establish a clear baseline for when data is ready for AI features, I outlined a five-stage readiness model (Raw → Validated → Aggregated → Contextualised → AI-Ready).
The basic idea is to ensure data is properly validated and contextualized (Stage 4) before feeding an AI model, and that only fully processed Stage 5 data is used for anything
shown directly to users or clinicians.

This fed into a standardised, pillar-based Health Summary Structure
(physical, mental, social, nutritional, environmental), where each pillar
reports status, trend and confidence; and where the absence of data is
stated explicitly rather than left blank, since an empty section is too
easily misread as "no concerns" rather than "no information at all." A
prioritisation ranking concluded that fixing existing data
quality (particularly standardising medical conditions and medications
against ICD-10/SNOMED CT/RxNorm) should come before expanding collection,
with validated mental health assessment as the single highest-value new
addition.
→ [`04-ai-readiness/`](../04-ai-readiness/)

### 5. Product and Strategy (Week 9)

Three tool proposals translated the above findings into something
implementable: a **fall-risk identification flag** (an explainable,
factor-based flag using age, musculoskeletal profile and activity decline
from baseline, rather than a black-box score); a **sensor-value
plausibility check** (a concrete implementation of Stage 2 of the
AI-readiness framework, flagging implausible readings like negative heart
rates for review rather than deleting them,worked example at
[`sensor_plausibility_check.R`](../05-product-and-strategy/sensor_plausibility_check.R));
and an **environment-access check** (enriching the existing patient
postcode with public green-space, walkability and air-quality data,
closing the environmental gap without any new patient burden).

Each proposal is a specification rather than tested, implemented code,
consistent with the placement's brief. The sensor plausibility check was
identified as the recommended starting point, since it is the most
directly justified by already-established findings and requires no new
data collection.
→ [`05-product-and-strategy/proposed-tools.md`](../05-product-and-strategy/proposed-tools.md)

## Consolidated Recommendations

1. **Fix data quality before expanding collection.** Filter invalid sensor
   readings, extract clinically useful values currently buried in
   `metadata`, and use `created_at` rather than `id` for chronological
   analysis.
2. **Standardise clinical free text.** Convert conditions and medications
   to ICD-10/SNOMED CT and RxNorm respectively — currently the biggest
   blocker to safely using the Patient dataset at scale.
3. **Close the mental-health and social gaps first**, using short
   validated instruments (WHO-5, PHQ-2/9, GAD-2/7, UCLA-3) rather than
   open-ended questions, to protect onboarding UX while materially
   improving data reliability.
4. **Adopt the five-stage AI-readiness framework** as a standing rule:
   nothing reaches an AI model before Stage 4 (Contextualised), and only
   Stage 5 (AI-Ready) data generates patient- or clinician-facing output.
5. **Build the sensor plausibility check first** among the three proposed
   tools — it needs no new data collection and directly implements a
   validation gap already confirmed to exist in production data.


## Limitations of This Work

This placement was a documentation- and design-based review rather than a
statistical audit of live production data.
Specifically:

- Data quality findings are structural, documentation-based observations
  (e.g. "the value field requires joining against sensor_type") rather
  than computed metrics such as null rates or duplication counts.
- The AI-readiness framework's notion of "confidence" describes the
  reliability of input data, not a guarantee that every AI-generated
  sentence is actually supported by it.
- None of the three proposed tools were implemented or tested against
  real patient outcomes; thresholds for the fall-risk flag in particular
  would need clinical validation before use.
- Because I didn't have direct access to raw, production-level patient data, I wasn't able to run extensive quantitative analyses 
  like measuring duplication counts, or running statistical distributions.

## Conclusion


This placement provided a valuable opportunity to deeply analyze an active digital health ecosystem and apply core health data science principles to real-world clinical data.
Working alongside the Ikarians team allowed for a constructive, hands-on exploration of how multi source wearable sensors, onboarding profiles,
and daily check-ins can be further structured, validated, and evaluated for AI applications.
Through this collaborative process, the project moved beyond initial data collection to address the nuances of health data quality:
surfacing high-value clinical signals, identifying gaps in mental and social health domains, and addressing the need for standardized clinical coding. 
The resulting five-stage AI-readiness framework, structured health summary concepts, and three targeted tool specifications offer practical,
evidence-based options that Ikarians can draw upon as the platform continues to mature.
Ultimately, this work served as a rich learning experience in digital health governance, demonstrating that the value of health data depends not simply on its volume,
but on the rigor of its structure, validation, and clinical context. The recommendations developed throughout this report provide a flexible roadmap to support Ikarians 
in building reliable, transparent, and patient-centered health insights.
