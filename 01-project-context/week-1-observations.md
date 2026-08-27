# Week 1: Initial Observations, Questions and Opportunities

**Original deliverable:** Summary of observations, questions and opportunities* — retained at [`../06-supporting-evidence/Summary_week1.docx`](../06-supporting-evidence/Week1_summary.docx)

## Project Orientation

Before working with the data itself, I focused on understanding the product, the thinking behind it and the potential challenges that could affect later stages of the placement. Week 1 was primarily spent reviewing pitch materials and product demonstrations, exploring the app from a user perspective, and evaluating Ikarians' internal clinical reference material.

## Tension Between User Experience and Clinical Rigour

The app's onboarding uses quick 1–10 self-rating scales, which are fast, low-friction and easy to complete on a phone. However, Ikarians' internal clinical reference material also recommends validated instruments, such as the HOPE questions, for some of the domains that these simpler scales are intended to capture.

This highlighted an important operational trade-off: low-friction measures may support engagement and repeated data collection, but they provide less standardisation and clinical interpretability than validated instruments. This could become important if the platform were eventually expected to evaluate meaningful health outcomes or support value-based healthcare applications. I therefore flagged the data collection approach early, as decisions made at ingestion directly affect the validation, comparability and downstream utility of the resulting data.

## Addressing Data Gaps in Social Health

Wearable data cannot directly capture subjective experiences such as loneliness, and a daily mood rating alone is unlikely to provide a sufficiently structured representation of social wellbeing. The initial onboarding surveys did not appear to capture social connectivity in a way that would readily support a measurable longitudinal outcome.

I therefore identified the **UCLA 3-Item Loneliness Scale** as a potential lightweight addition. Its brevity made it potentially compatible with the platform's low-friction approach while providing a more standardised measure of an important aspect of social health.

## Initial Questions for the Team

Several questions emerged from this initial review:

* How is onboarding friction being balanced against the need for a meaningful clinical baseline?
* How frequently does wearable data reach the dashboard, and what processes are in place to assess the reliability and clinical safety of AI-generated advice?
* What happens when a sensor produces an implausible reading, such as when a wearable is removed or records an anomalous heart-rate spike?
* How is the platform's composite "IK factor" score weighted across the different health pillars?

Some of these questions were clarified through early discussions with the team. Others, particularly the weighting of the IK factor, remained open questions throughout the placement.

## Relevance

This week established the direction for much of the subsequent work. The emerging issue was not simply that Ikarians needed more data, but that the data already being collected needed to be standardised, contextualised and validated before it could be relied upon for downstream analysis and AI applications.

This principle became a recurring theme in the subsequent data quality, gap assessment and AI-readiness work.

## Limitations

This was a first-week exploratory review rather than a technical audit of the underlying database. Some observations were based on limited hands-on use of the application and the materials available to me at that stage, rather than systematic analysis of the underlying data.

I therefore treated these observations as hypotheses and starting questions rather than confirmed findings. This distinction was important as the placement progressed, since several initial assumptions were subsequently refined through closer examination of the data and discussions with the team.

## Proposed Approach and Subsequent Direction

I proposed a hybrid approach that would retain the fast 1–10 daily check-ins to minimise friction while introducing validated instruments at onboarding and at defined intervals, such as Day 30 and Day 90. Examples considered included the PHQ-9, GAD-7 and EQ-5D, depending on the specific construct being measured and the intended use of the resulting data.

The aim was not simply to increase the volume of information collected, but to combine low-friction signals with more standardised measures that could provide a stronger baseline and support meaningful change over time. This balance between user experience, clinical rigour and downstream data utility became a recurring consideration throughout the placement and is explored further in [`03-data-quality-and-value/`](../03-data-quality-and-value/) and [`04-ai-readiness/`](../04-ai-readiness/).
