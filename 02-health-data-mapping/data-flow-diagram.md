# Data Flow Diagram

*Original: [`../06-supporting-evidence/data_flow_diagram.pdf`](../06-supporting-evidence/data_flow_diagram.pdf)*

![Ikarians Data Flow Diagram](assets/data-flow-diagram-1.png)

## The technical path

This traces the more literal, pipeline level route a data point takes,
complementing the conceptual ecosystem map:

1. **Garmin wrist sensor** → synced via the Garmin app → **Garmin Cloud and
   Ikarians server**
2. **Patient** enters lifestyle info directly → **Ikarians Mobile App** →
   synced to the same server layer
3. Both streams converge at **Ingestion** → **Processing Layer** → stored
   in a **Relational Database** (users, baselines, biometrics, lifestyle
   logs)
4. The **AI Engine** reads from the database, applies clinical guidelines,
   and produces two output streams:
   - **Patient insights** → mobile interface → lifestyle alerts,
     notifications, meal ideas
   - **Clinician insights** → dashboard → health markers, screenings,
     fatigue warnings

## How this was used
auditable pipeline. It was used later to identify where specific data
quality issues originated; for instance, whether an invalid heart-rate
reading is a raw sensor fault or something introduced during processing
and again when placing the AI-readiness stages against the platform's
actual architecture rather than an abstract one.
