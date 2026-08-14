# CivicPulse — Architecture: Prototype vs. Production

The `prototype/index.html` demo simulates the agent pipeline with simple JavaScript so it runs offline with zero setup. This doc maps each mock piece to what it would be in a real deployment — useful if judges ask "how would this actually work in production?"

| Pipeline stage | Prototype (index.html) | Production equivalent |
|---|---|---|
| Intake Agent | Static HTML form | Claude API (tool use) + WhatsApp Business API + IVR for voice; normalizes any input into a structured ticket schema |
| Classification & Priority Agent | `classify()` — keyword matching | Claude API call with a structured-output prompt, returning category/severity/urgency as JSON; fine-tuned on historical grievance data over time |
| Duplicate Detection Agent | Random 25% chance mock | Vector DB (e.g. pgvector) storing embeddings of open tickets; new ticket compared via cosine similarity within the same geo-radius |
| Routing Agent | Static category → department map | Rules engine + department directory service; auto-escalates via cron/queue job if SLA timer expires |
| Citizen Communication Agent | Template string | Claude API generating a plain-language, empathetic status update in the citizen's preferred language; sent via WhatsApp/SMS |
| Insights Agent / Dashboard | In-memory JS array, recalculated on render | PostgreSQL + PostGIS for geo-queries; scheduled aggregation jobs feeding a BI dashboard (e.g. Metabase) |
| Orchestrator | Sequential `setTimeout` calls | LangGraph-style state machine coordinating agent calls, retries, and shared context/memory |

## Data flow (production)

```
Citizen (WhatsApp / Web / Voice)
        │
        ▼
  Intake Agent  ──────────────► Shared Knowledge Base (Postgres + PostGIS)
        │                                 ▲
        ▼                                 │
  Classification & Priority Agent         │
        │                                 │
        ▼                                 │
  Duplicate Detection Agent (Vector DB)    │
        │                                 │
        ▼                                 │
  Routing Agent ──► Department Queue      │
        │                                 │
        ▼                                 │
  Citizen Communication Agent             │
        │                                 │
        ▼                                 │
  Insights Agent ─────────────────────────┘
        │
        ▼
  Official Dashboard (Metabase / custom React admin)
```

## Why this is feasible to build for real

- No custom hardware or IoT sensors required — pure software on top of an LLM API.
- Every component (Postgres, vector DB, LLM API, WhatsApp Business API) is an existing, documented service — no research-grade R&D needed to reach an MVP.
- The prototype's mock logic already defines the exact input/output contract each real agent needs to satisfy, so swapping mock → real is additive, not a rewrite.
