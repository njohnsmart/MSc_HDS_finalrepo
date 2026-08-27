# Example Code: Sensor Plausibility Check

This folder contains one small, self-contained script,
[`sensor_plausibility_check.R`](sensor_plausibility_check.R), illustrating
how Tool B from [`../proposed-tools.md`](../proposed-tools.md) — the sensor
value plausibility check — would work in practice.


This is a worked example. It defines plausible ranges for three sensor types (heart rate, sleep score, pulse oximetry), 
runs a small set of made-up readings through the check, and prints which ones would be flagged and why — including the kind of invalid heart-rate readings (negative, zero) identified in the Data Quality Assessment.

## A note on scope: 
This uses synthetic data and was written after the placement to illustrate the tool proposal.

## Running it

Requires only base R, no additional packages:

```
Rscript sensor_plausibility_check.R
```
