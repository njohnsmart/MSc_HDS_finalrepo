# Signal vs Noise Analysis

*Original: [`../06-supporting-evidence/John_Week4-5__deliverable.docx`](../06-supporting-evidence/John_Week4-5__deliverable.docx)*

This analysis identifies which platform variables provide meaningful
health insight, as opposed to those that add volume without much
analytical value, assessed against relevance to health outcomes,
behavioural patterns, and potential for future analytics or AI use.

## High signal

The strongest signal comes from wearable sensor data and core patient
health information:

- **Sleep** — duration, REM, deep sleep, sleep quality: solid indicators
  of recovery and long-term wellbeing
- **Heart rate** — resting, average, maximum: strong cardiovascular
  indicators, particularly valuable when tracked over time rather than as
  single readings
- **Physical activity** — step count, activity duration, distance,
  intensity: a direct measure of healthy behaviour, useful for
  behaviour-change work
- **Patient profile** — age, conditions, medication use, smoking status:
  essential clinical context, particularly when combined with wearable
  data

## Medium signal

Useful context, but limited value on its own: profession, language,
country of origin, religion, device type, device connection history.
These do not measure health directly, but they help interpret and
personalise the wearable data.

## Low signal

Mostly operational fields like record IDs, auth tokens, notification tokens,
file references. These were necessary for the system to run, but not worth including
in an analytical dataset.

## What stood out

Most of the current high-value signal comes from **physical health**
metrics. **Mental wellbeing, social health, and broader lifestyle
factors are comparatively thin** in the current data, which is what
motivated the [Data Gap Assessment](data-gap-assessment.md).

## The main takeaways

The most valuable variables are those that show change over time rather
than single readings eg:"71 bpm" says little on its own; "71 bpm, up from
a 4-week baseline of 67" says considerably more.

## Conclusion

The platform already holds valuable data such as wearable sensor data
and patient profiles.Standardising it, extracting
the metadata currently hidden, and reducing reliance on low-value
operational fields would substantially improve its usability.
