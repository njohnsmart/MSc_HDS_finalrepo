# 05 — Product and Strategy

**Placement stage:** Week 9 (delivered in a different form than the
original brief set out) · what concrete features follow from everything
above?

## Why this stage exists

The Data Quality, Gap, and AI-Readiness work (Sections 03–04) surfaced
specific weaknesses: invalid sensor readings reaching analysis unfiltered,
no environmental or socioeconomic data layer, and a gap between "the data
exists" and "the data is safe to act on." This stage translated those
findings into three concrete tool proposals rather than staying at the
level of recommendation documents.

## What this involved

Three tool designs, each grounded in a specific finding from earlier
stages rather than proposed independently of it: a fall-risk
identification flag, a sensor-value plausibility check, and an
environment-access enrichment tool.

## Contents

| File | What it is |
|---|---|
| [`proposed-tools.md`](proposed-tools.md) | The full specification for each tool, its clinical reasoning, and its limitations. |
| [`sensor_plausibility_check.R`](sensor_plausibility_check.R) | A worked out example of how the tool would work. |

## Why it mattered

These are the first outputs from the placement that Ikarians could
plausibly hand to an engineer: each uses data the platform already
collects, each is explainable rather than black-box, and each closes a
specific gap already identified — invalid sensor data, missing
environmental context, an evidence-based but currently unused clinical
signal for fall risk.

## Limitations

None of the three tools were implemented or tested during the placement;
these are specifications rather than working code, consistent with the
brief's emphasis on structuring data rather than building a production
system. Each tool's own write-up names its specific limitations.

## Recommended next step

Build the sensor-value plausibility check first. It is the most directly
justified by findings already established (see the
[Data Quality Assessment](../03-data-quality-and-value/data-quality-assessment.md))
and requires no new data collection.

## Where the portfolio ends

This is the final stage of work produced during the placement. See the
root [README's scope note](../README.md#scope) for why Insight Discovery
and the Final Roadmap are not represented here.
