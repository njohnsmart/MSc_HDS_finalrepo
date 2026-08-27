# Proposed Tools

*Original: [`../06-supporting-evidence/tools_proposed.docx`](../06-supporting-evidence/tools_proposed.docx)*

Three tool proposals were developed from findings identified during the
data quality, data gap and AI-readiness stages. Each addresses a different
problem within the platform and is intended to be explainable and
practical rather than dependent on a complex model.

---

## A. Fall Risk Identification

**Rationale:** Falls prevention has an established evidence base,
particularly in older adults, making this a potentially useful clinical
application of data already collected by Ikarians. The platform already
holds information that could contribute to an initial assessment,
including age, musculoskeletal conditions and activity patterns.

**Data required:** the `clinical_baselines` musculoskeletal profile (see
the [Data Dictionary](../02-health-data-mapping/data-dictionary.md))
already includes age and documented joint/mobility conditions. The
majority of the work here is designing a sensible rule rather than
collecting new data.
The proposed approach would avoid producing a single unexplained risk
score. Instead, the tool would identify a small number of contributing
factors, for example:

- Older age
- A documented lower-limb or musculoskeletal condition
- A recent decline in activity compared with the individual's baseline

Using change from an individual's own baseline is particularly relevant.
Someone who has always recorded relatively low activity may have a
different risk profile from someone whose activity has recently declined
substantially. A sudden change could indicate emerging pain, reduced
mobility or another issue that has not yet been reported.

The output should therefore be presented as an **explainable flag**, with
the factors contributing to it visible to the clinician rather than as a
single numerical prediction.


**Limitation:** Appropriate thresholds would need to be established and
validated against real patient outcomes. The available placement data was
not sufficient to assess sensitivity, specificity or false-alert rates, so
this remains a proposed tool rather than a clinically validated model.


---

## B. Sensor Value Plausibility Check

**Purpose:** Provide an early validation step for wearable data by checking
measurements against plausible ranges before they are used in downstream
analysis or AI-generated insights.

The [Data Quality Assessment](../03-data-quality-and-value/data-quality-assessment.md)
identified actual problem readings already present in the Sensor
dataset — negative and zero heart-rate values. Left unfiltered, these
would skew averages and trends and could feed directly into incorrect AI
conclusions.

For example:

```
Input:  sensor_type = "HeartRate", value = -4
Check:  value against plausible range for HeartRate
Result: marked invalid, excluded from downstream calculations,
        flagged (not deleted) for later review
```
The value is not discarded outright; it is excluded from calculations but
retained and flagged, so it remains available for later data quality
review.

**Value of the proposed tool** It functions as a simple, upstream
safeguard. If an obviously implausible reading is caught before reaching
the AI, the model does not need to independently judge whether something
"looks realistic," which reduces the risk of poor sensor data quietly
influencing an AI-generated recommendation. This directly implements Stage 2
(Validated) of the
[AI Readiness Framework](../04-ai-readiness/ai-readiness-framework.md)
made concrete.

**Limitation:** An unusual measurement is not automatically an incorrect
measurement. Genuine physiological extremes can occur, so the tool should
identify values for review rather than treating every outlier as a
definitive error.

---

## C. Environment Access Check

**Purpose:** adds environmental context currently missing from the
patient profile (see the
[Data Gap Assessment](../03-data-quality-and-value/data-gap-assessment.md)),
using the postcode already collected at onboarding to retrieve area-level
data on green space access, walkability, and air quality.

Activity suggestions are more
useful when they account for whether a patient has accessible outdoor
space nearby, rather than assuming this is universally the case.

Unlike the other two tools, this one
enriches existing patient data with external, publicly available data
rather than cleaning up what already exists. Given a patient ID, it would
retrieve the stored postcode and query public environmental datasets for
that area, returning structured output rather than a vague verdict:

For example:
```
postcode_area: "AB24"
nearest_public_green_space: ...
green_space_density: ...
walkability_estimate: ...
air_quality_index: ...
```

**Value of the Proposed Tool:** it is a low-burden way to close an
identified gap without requiring an additional patient questionnaire, as
the data can be derived automatically from information the platform
already holds.

**Limitation:** this is read-only, area-level context and
should not be treated as a direct measure of a patient's actual
behaviour. Proximity to green space does not imply its use; the tool
describes the environment rather than the person's behaviour within it.

---

## How the proposals link to the placement 

Each addresses a different kind of gap identified earlier: (A) an
evidence-backed clinical signal that was not being used, (B) a concrete
data quality problem actually observed, and (C) a structural gap
(environmental context) that can be closed without adding patient burden.
Together, they demonstrate the placement's findings translating into
something implementable, rather than remaining at the level of
recommendation documents. They are also explainable rather than
black-box, which is consistent with the platform's  aim of
supporting clinical judgement rather than replacing it.
