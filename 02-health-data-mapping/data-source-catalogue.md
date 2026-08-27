# Data Source Catalogue

*Original: [`../06-supporting-evidence/data_source_catalogue_John.docx`](../06-supporting-evidence/data_source_catalogue_John.docx)*

For each source, I have listed what it is, what it captures, and the actual
AI behaviour each metric currently drives. Capturing that alongside the
metric itself, rather than just listing fields, makes it clear which
pieces of data already inform the platform's behaviour, as opposed to
those collected without a defined use yet.

## Source A: Garmin / Smartwatch

Passive, collected automatically via sync. Gives a continuous picture of
activity, sleep, stress, recovery and cardiovascular patterns without the
user having to do anything.

| Metric | Why it matters clinically | What the AI does with it |
|---|---|---|
| Step count (`steps`) | Tracks overall activity, flags prolonged inactivity | Steps below 50% of target for 3 days straight → suggests a 10-minute outdoor walk |
| Sleep duration (`durationInSeconds`) | Adequacy of rest/recovery | Under 6 hours → reduces recommended cognitive workload, advises against heavy evening meals |
| REM sleep (`remSleepInSeconds`) | Memory processing, emotional regulation | Consistently below the user's usual pattern → suggests an evening "Mental Download" exercise |
| Stress level (`averageStressLevel`, `maxStressLevel`) | HRV-estimated autonomic activity | Elevated while inactive → suggests a brief paced-breathing exercise |
| Body Battery (`bodyBatteryChargedValue`) | Combines sleep/stress/activity into a recovery estimate | Morning score below 20 → reduced activity target for the day |
| Max heart rate (`maxHeartRateInBeatsPerMinute`) | Workout intensity | ~70% max HR sustained for ≥22 minutes → logged as a mood-supporting exercise event |
| Pulse oximetry (`PulseOx`) | SpO₂, overnight respiratory/recovery health | Notably below the user's normal range → flagged for clinician review |

## Source B: User Onboarding Questionnaire

One-off, collected at registration. Sets a baseline so later
recommendations are not generic.

| Metric | Why it matters clinically | What the AI does with it |
|---|---|---|
| Basic profile (name, email, language, role) | Account setup | Personalises the app experience |
| Musculoskeletal profile | Flags conditions (e.g. knee/hip OA) affecting exercise safety | High-impact activities swapped for joint-friendly strengthening work |
| Baseline chronotype | Natural preference for earlier/later sleep-wake | Evening reminders scheduled ~90 minutes before usual bedtime |
| GAD-7 and PHQ-9 scores | Standardised anxiety/depression screening | Higher scores → closer monitoring via the clinician dashboard |

## Source C: In-App Lifestyle Survey

Daily, user-entered. Captures information wearables cannot
measure like nutrition and social connection.

| Metric | Why it matters clinically | What the AI does with it |
|---|---|---|
| Daily protein intake (`daily_protein_g`) | Muscle health, weight management, healthy ageing | Below personal target → recommends higher-protein meal options |
| Dietary Inflammatory Index (DII) | Overall diet quality | Few anti-inflammatory foods logged → suggests a nutrient-rich meal |
| Social Connectedness Index | Perceived social connection, possible isolation | Low scores → prompts engagement suggestions, may notify clinicians |

The AI action column matters proved more useful than expected 
as it surfaced which fields already have defined behaviour
attached versus which do not yet have one. This fed directly into the
signal-vs-noise work and the data prioritisation later on ;variables with
a clear, evidence-backed AI action already attached were treated as
stronger candidates for continued investment than those collected without
a clear reasoning.
