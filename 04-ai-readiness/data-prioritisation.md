# Recommendations for Data Prioritisation

*Original: [`../06-supporting-evidence/Recommendations_for_Data_Priortisation.docx`](../06-supporting-evidence/Recommendations_for_Data_Priortisation.docx)*

## Approach

Not every variable on the platform deserves equal investment. Priority was
assessed against four criteria:

1. **Strength of clinical evidence** — variables with solid, consistent
   research backing outrank weaker or less-established measures.
2. **Data quality** — per the
   [Data Quality Assessment](../03-data-quality-and-value/data-quality-assessment.md),
   some variables are already reliable; others need cleaning first.
3. **Gap severity** — how well each wellbeing pillar is currently
   represented (from the
   [Data Gap Assessment](../03-data-quality-and-value/data-gap-assessment.md)).
4. **Patient burden** — passive wearable data is inherently easier to
   obtain than repeated questionnaires or manual logging, and burden tends
   to correlate with how complete a data source ends up being in practice.

## Existing data, ranked

| Priority | Data | Rationale |
|---|---|---|
| **1 — Highest** | Wearable data (sleep, activity, heart rate) | Strong evidence base, collected automatically, generally complete once invalid values are filtered out |
| **2** | Self-reported stress scores, journal entries | Useful, but currently unstandardised — stress is a simple rating rather than a validated tool, and journals are unstructured free text |
| **3** | Nutritional information | Clinically relevant but held back by inconsistent manual logging — improving how it is collected likely matters more than extracting more from what already exists |
| **4 — Lowest** | Free-text medical conditions/medications | Potentially high value, but not safely usable until converted to ICD-10/SNOMED CT — genuine risk of AI misinterpretation otherwise |

## Missing data, ranked

| Priority | Gap | Rationale |
|---|---|---|
| **1** | Mental health | Currently a single stress score; validated tools (PHQ-9, GAD-7) would improve data quality for minimal added patient burden |
| **2** | Social connectedness | Strong evidence linking loneliness/isolation to health outcomes, yet almost nothing is currently captured — addressable with a short validated tool |
| **3** | Nutrition | Some data exists (protein intake) but relies on manual logging — engagement is the more difficult problem here, not the choice of instrument |
| **4** | Environmental factors | Smaller direct health effect than the others, but very low burden, since it is derivable from a postcode already on file |

## Conclusion

**Improving the quality of existing data should take priority over
collecting more of it.** Missing data is at least recognisable as missing;
poor-quality data can quietly produce misleading conclusions without
anyone noticing. Once existing quality is strengthened, **validated mental
health assessment** represents the greatest single opportunity, as it
addresses the largest current gap for comparatively little additional
effort from users.

## Where this leads

This prioritisation, particularly the principle of fixing quality before
expanding collection, is the direct rationale behind the
sensor-value plausibility check proposed in
[`05-product-and-strategy/`](../05-product-and-strategy/).
