# 02 — Health Data Mapping

**Placement stage:** Weeks 2–3 · what data does Ikarians collect, where
does it come from, and how does it move through the system?

## Why this came first

Before any assessment of data quality or AI-readiness was possible, the
data ecosystem needed to be documented from scratch. A lot of this
knowledge existed only informally, distributed across the founders' and
engineers' understanding of the platform rather than written down anywhere.

## What this involved

Reviewing the three main data sources (Garmin sync, onboarding
questionnaire, daily in-app survey), examining how the AI engine consumes
and produces data, and producing a visual ecosystem map, a data flow
diagram, a source catalogue, and a formal data dictionary.

## Contents

| File | What it is |
|---|---|
| [`ecosystem-map.md`](ecosystem-map.md) | A visual map of the data sources, processing layers, and how insight flows out to patients and clinicians |
| [`data-flow-diagram.md`](data-flow-diagram.md) | The technical path: device → sync → server → database → AI engine → interfaces |
| [`data-source-catalogue.md`](data-source-catalogue.md) | Every data source, what it captures, and the specific AI action each metric drives |
| [`data-dictionary.md`](data-dictionary.md) | The schema itself — tables, fields, constraints, and why each one exists |

## Why it mattered

Before this mapping, understanding "what data exists and why" required
asking someone on the team or piecing it together from scattered
documentation. This gives Ikarians a single reference point for the data
ecosystem, and it is the shared vocabulary that the rest of this portfolio
builds on.

## Limitation

The dictionary reflects the schema as understood during the placement. A
few fields were still being finalised at the time (chronotype,
ANA_sessions, the dietary inflammatory score) and are marked as such rather
than presented as settled.

## Where this leads

This mapping is the direct input to
[`03-data-quality-and-value/`](../03-data-quality-and-value/), which
assesses how good this data actually is, and where it falls short.
