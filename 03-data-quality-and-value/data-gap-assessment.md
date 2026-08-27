# Data Gap Assessment

*Original: [`../06-supporting-evidence/Data_Gaps_modified.docx`](../06-supporting-evidence/Data_Gaps_modified.docx)
— the refined version. An earlier draft of this same analysis also appears
inside
[`../06-supporting-evidence/Week4-5__deliverable.docx`](../06-supporting-evidence/Week4-5__deliverable.docx),
kept for reference as it shows how the analysis developed.*

This sets out the important health information that is missing or barely
captured in Ikarians' current data, with specific, evidence based,
low-burden suggestions for closing each gap. Throughout, short validated
instruments were favoured over open-ended data collection, largely to
protect onboarding UX which was a constraint that recurred across the placement and
is discussed further in the reflective report.

## Mental health

**Current state:** a single self-rated 1–10 wellbeing question.

**Gap:** current clinical guidance (a 2024 JAMA review, ASCO and
APA recommendations) supports validated screening tools for common mental
health conditions. A single self-rating can miss depression or anxiety
symptoms outright, and is not reliable for tracking change over time,
which is arguably the more useful measure in this context.

**Recommendation:** brief validated instruments like the **WHO-5
Well-Being Index**, **PHQ-2/PHQ-9** (depression), **GAD-2/GAD-7**
(anxiety). All are short, auto-scorable, and suitable for both onboarding
and periodic follow-up.

## Social and behavioural health

**Current state:** almost no data on living arrangements, social support,
loneliness, dietary habits, hydration, or sedentary time.

**Gap:** AHA reports and large cohort studies consistently link
loneliness and social isolation to higher mortality and dementia risk.
Diet, alcohol intake and prolonged sitting are also well-established
chronic disease risk factors. Without this data, a significant driver of
an individual's health remains invisible to the platform.

**Recommendation:** the **UCLA 3-Item Loneliness Scale** ; short and
validated  plus a small number of questions on alcohol, diet, hydration
and sitting time.

## Nutrition

**Current state:** no structured dietary data collected.

**Gap:** overall eating patterns predict long-term health
outcomes more reliably than tracking individual nutrients. Adherence to a
Mediterranean-style diet in particular is associated with lower
cardiovascular risk.

**Recommendation:** rather than meal by meal logging, which tends to
have poor long-term engagement, a short **Mediterranean Diet Adherence
Score**.

**Protein intake is a partial exception.** It is worth capturing
separately given its link to muscle health, recovery and physical
performance, particularly for users doing resistance training. Gram level
manual logging is unlikely to be sustained as a habit, so a more realistic
approach may be a short habitual frequency questionnaire (how often
protein sources appear in meals, current fitness goals, training
frequency), potentially supplemented later by food-image recognition for
lower effort estimation ( please see
[proteinscreener.nl](https://proteinscreener.nl/) as one example of this
approach in practice).

## Environmental and socioeconomic factors

**Current state:** no data on education, employment, housing, financial
situation, or access to outdoor space.

**Gap:** these are recognised social determinants of health,
and they also affect whether the platform's lifestyle advice is realistic
like recommending an outdoor walk assumes the person has safe green space
nearby, which is not guaranteed.

**Recommendation:** a small number of optional onboarding questions:

1. **Employment status** — full-time / part-time / self-employed /
   unemployed / unable to work / retired / student / prefer not to say
2. **Housing stability** — stable / worried about losing housing /
   currently without stable housing / prefer not to say
3. **Financial strain** — a simple question on how difficult it is to
   cover monthly expenses

## Link to Subsequent Work

This gap assessment forms the evidence base for two later pieces;the
"current readiness" section of the
[AI Readiness Framework](../04-ai-readiness/ai-readiness-framework.md),
and the [Data Prioritisation](../04-ai-readiness/data-prioritisation.md)
ranking, which weighs each gap against the burden it adds relative to its
expected value.
