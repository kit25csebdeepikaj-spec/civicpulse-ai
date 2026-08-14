# CivicPulse — Full Feature List

## Phase 1 — In the hackathon demo

| Feature | Description | Where to see it |
|---|---|---|
| Multi-channel intake | Text, WhatsApp, voice-ready form | `prototype/index.html` → Submit Complaint |
| Classification & priority scoring | Keyword-driven category + severity + urgency in the prototype; LLM-driven in production | Agent Pipeline → Step 2 |
| Duplicate detection | Simulated semantic merge against existing tickets | Agent Pipeline → Step 3 |
| Routing & SLA assignment | Maps category → department, assigns SLA by severity | Agent Pipeline → Step 4 |
| Citizen auto-updates | Plain-language status message | Agent Pipeline → Step 5 result card |
| Live dashboard | Stats, category breakdown, ward heatmap, recent tickets table | Official Dashboard tab |

## Phase 2 — Roadmap (pitch these as "next," don't overclaim as built)

| Feature | Why it matters | Judging angle it strengthens |
|---|---|---|
| Voice-first multilingual intake | Reaches elderly / low-literacy / rural citizens | Social Impact |
| Predictive escalation model | Flags tickets likely to breach SLA or go viral, before they do | Innovation |
| Explain-This-Decision UI | One click shows exactly why a ticket was prioritized/routed the way it was | User Experience, Digital Trust |
| Public trust ledger | Anonymized ward-wise resolution-time data, published openly | Social Impact, Digital Trust |
| Call-center transcript ingestion | Brings a legacy channel into the same pipeline | Scalability |
| Gamified civic reporting | Citizens earn points for verified helpful reports | Innovation, community engagement |

## Stretch add-ons worth mentioning if asked in Q&A

- **Multilingual auto-translation** at the Intake Agent so any regional language complaint is normalized to a common internal schema.
- **Officer mobile app** for field crews to close tickets with a photo, auto-notifying the Citizen Communication Agent.
- **Anomaly detection** on the Insights Agent to catch a sudden spike in one category/ward (e.g. water contamination cluster) and alert public health authorities directly.
- **API-first design** so any state's existing e-governance portal can plug into the same agent backend without a UI rewrite.
