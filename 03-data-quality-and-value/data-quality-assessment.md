# Data Quality Assessment

*Original: [`../06-supporting-evidence/John_Week4-5__deliverable.docx`](../06-supporting-evidence/John_Week4-5__deliverable.docx)*

Each of the platform's four core datasets was reviewed for completeness,
consistency, and anything likely to cause problems downstream. The review
worked from schema documentation and sample records rather than a live
statistical audit (see the limitation noted in the
[section overview](README.md)), so findings here are structural
observations rather than computed metrics such as null rates.

## User dataset

This dataset is in good shape. Unique identifiers, user details, roles,
registration status and timestamps are all consistently present, with a
clean split between patients and clinicians. There is little to flag here;
it gives a reliable identity layer to build everything else on.

## Patient dataset

Had rich content like demographics, clinical and lifestyle information,
medication history, smoking status, links to a healthcare professional.

However,A few things stood out:

- Most health information is stored in **JSON fields**, which complicates
  analysis unnecessarily
- Clinical conditions are recorded as **free text** rather than standard
  clinical codes
- Medications are also free entry, when a drug-code dropdown would make
  standardisation considerably easier

This is valuable data, but it needs to be standardised before it
could be reliably analysed at scale.

## Device dataset

Links wearable devices to users, supporting both Garmin integration paths.
Its role is largely operational rather than a source of clinical insight in its own right.
The clinical value sits in the linked Sensor dataset.

## Sensor dataset

This is the most valuable dataset on the platforme by some margin. It includes
continuous heart rate, sleep, activity, stress and SpO₂ readings with rich
metadata. Two structural findings are worth flagging specifically:

1. **The `value` field does not mean anything on its own.** What it
   represents depends entirely on `sensor_type` — a HeartRate value is BPM,
   a Sleep value is a score or hours, PulseOx is a blood-oxygen percentage.
   Any real analysis has to join `value` against `sensor_type` to interpret
   it correctly, which is easy to overlook.
2. ** A significant amount of clinically useful content sits in
   `metadata`, not `value`.** 
   For Garmin devices specifically, average/max
   heart rate, stress indicators, activity detail and recovery measures
   are often embedded in metadata rather than the primary field.
   analysis of `value` alone would miss most of the actual clinical
   signal, a finding that would not be obvious without 
   investigating it.

There are also concrete data quality issues to filter like the negative and zero
heart-rate readings that clearly should not exist, and a note that
`created_at`, not `id`, is the correct field for chronological analysis,
since record IDs reflect the ingestion order rather than measurement time.

## Overall

Sensor data has real value, but it requires preprocessing, validation and
standardising ; extracting metadata, filtering invalid readings, using the
correct timestamp field  before it is reliable enough for reporting,
analytics, or anything AI facing.

## Summary

| Dataset | Current state | Priority action |
|---|---|---|
| User | Reliable | None required |
| Patient | Rich but unstructured | Standardise conditions and medications against clinical codes |
| Device | Reliable, operational only | None required |
| Sensor | High value, needs cleaning | Filter invalid readings; extract metadata; use `created_at` for ordering |

## Next

This dataset-level review effectively forms the groundwork for the
[Signal vs Noise Analysis](signal-vs-noise.md), which examines which
specific variables  including the metadata-buried ones flagged here
actually carry the most analytical value.
