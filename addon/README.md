# CivicPulse — Add-On Package

This package supplements `TeamCatalyst_CivicPulse.pptx` with a working prototype and supporting documentation for the Innovik Hackathon submission.

## What's inside

```
CivicPulse_AddOns/
├── README.md                  ← you are here
├── deck/
│   └── TeamCatalyst_CivicPulse.pptx
├── prototype/
│   └── index.html              ← working offline demo (open directly in any browser)
└── docs/
    ├── FEATURES.md              ← full feature list, incl. Phase 2 roadmap detail
    └── ARCHITECTURE.md          ← agent-by-agent technical breakdown
```

## Running the prototype

No installation, no server, no API keys needed.

1. Open `prototype/index.html` in any modern browser (Chrome, Edge, Firefox, Safari).
2. Go to **Submit Complaint** → click "Use sample complaint" → **Submit to Agent Pipeline**.
3. Watch the 5-agent pipeline run live on the **Agent Pipeline** tab.
4. Check **Official Dashboard** to see the ticket land in the stats, ward heatmap, and category breakdown.

The classification, routing, and duplicate-detection logic is a lightweight rule-based simulation (keyword matching + mock scoring) standing in for the real LLM-agent pipeline described in the deck — it's built to demonstrate the *workflow and UX*, not to be the production model.

### Taking screenshots for your slides
Recommended shots for Slide 7 (Demo / Use Case):
- Submit Complaint screen with the sample complaint filled in
- Agent Pipeline mid-run (2–3 steps lit up)
- Agent Pipeline fully complete, showing the result card
- Official Dashboard (heatmap + stats)

Resize your browser window to roughly 1600×1000 before capturing for the cleanest crop.

## Why this package helps your score

| Judging criterion | What this adds |
|---|---|
| Technical Excellence | A real, running artifact — not just slides describing one |
| Feasibility | Shows the workflow works end-to-end, even before the real LLM/backend is wired in |
| User Experience | Judges can click through it themselves during Q&A |
| Innovation | Dashboard + heatmap + explainable routing are visible, not just described |

## Next steps to make it "real"
See `docs/ARCHITECTURE.md` for how each mock function in `index.html` maps to the actual agent it would call in production (Claude API + tool use, PostGIS, vector DB, etc.).
