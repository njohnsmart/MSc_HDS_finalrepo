# Data Dictionary

*Original: [`../06-supporting-evidence/data_dictionary_John.xlsx`](../06-supporting-evidence/data_dictionary_John.xlsx)*

The formal schema across four tables — fields, constraints, and why each
one is there. A few fields were still being finalised during the placement
(marked with `?` in the original spreadsheet); I have flagged those below.

## `User`

| Variable | Constraints | Why it is there |
|---|---|---|
| `user_id` | Primary key, not null | Unique identifier |
| `full_name` | Not null | Identifier for reporting |
| `email` | Unique, not null | Communication and authentication |
| `user_role` | patient / clinician / admin | Restricts data views and dashboard access |
| `time_created` | Not null | Logging |

## `clinical_baselines`

| Variable | Constraints | Why it is there |
|---|---|---|
| `baseline_id` | PK, not null | Unique identifier for the patient's clinical file |
| `user_id` | FK, not null | Links baseline to a user |
| `date_of_birth` | Not null | Age-specific activity/nutrition targets |
| `sex` | male / female | Age- and sex-specific targets |
| `musculoskeletal_disorders` | none, OA, tendinitis *(still being finalised)* | Better-tailored exercise suggestions |
| `gad7` | 0–21 | Anxiety screening |
| `phq9` | 0–29 | Depression screening |
| `chronotype` *(still being finalised)* | early_bird / intermediate / night_owl | Predicting health vulnerabilities |

## `daily_wearable_summary`

| Variable | Constraints | Why it is there |
|---|---|---|
| `summary_id` | PK, not null | Unique key per entry |
| `user_id` | FK | Links summary to patient |
| `entry_date` | Not null | Date of entry |
| `total_steps` | ≥0 | Low-intensity movement measure |
| `sleep_duration` | ≥0 | Time slept vs. the 7-hour guideline |
| `sleep_efficiency` | ≤100 | Sleep quality and recovery |
| `resting_heart_rate` | bpm | Cardiovascular health signal |
| `average_stress_score` | 0–100 | Physiological strain |
| `morning_body_battery` | 0–100 | Overnight recovery estimate |
| `ANA_sessions` *(still being finalised)* | ≥0 | Count of sessions at 70–85% max HR for ≥22 min |

## `daily_lifestyle_tracking`

| Variable | Constraints | Why it is there |
|---|---|---|
| `log_id` | PK, not null | Identifier per survey entry |
| `user_id` | FK, not null | Links input to the right user |
| `log_date` | Not null | Date of entry |
| `protein_intake_g` | ≥0 | Protein intake vs. goal (1.6–2 g/kg body weight) |
| `dietary_inflammatory_score` *(still being finalised)* | 1–11 | Meal-pattern evaluation |
| `social_score` | 1–10 | Social connection patterns |

## Why this matters

This is effectively the schema-level counterpart to the source catalogue:
the catalogue explains why something is collected and what it triggers,
while this defines how it is stored. Together they were the primary
reference for the Weeks 4–5 quality assessment; several issues flagged
there ; free-text clinical fields, metrics embedded in JSON metadata,
unresolved fields were first visible at this schema level.
