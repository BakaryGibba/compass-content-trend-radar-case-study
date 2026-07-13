[Back to README](../README.md)

# Executive Summary

Compass is a content intelligence workspace for turning client context and market signals into weekly content strategy outputs.

The project combines a FastAPI backend, React/TanStack frontend, Google Trends collection, TikTok source adapters, SEO research, scoring services, optional AI generation, and local report artifacts. Its goal is to help a strategist move from "what is trending?" to "what should we publish this week, and why?"

## Portfolio Narrative

Compass demonstrates product engineering across the full content strategy lifecycle:

| Capability | Portfolio Signal |
| --- | --- |
| Data collection | Integrates multiple external trend sources with graceful failure handling |
| AI workflow | Uses AI as an assistive layer, with fallback logic and review states |
| Product UX | Turns a complex pipeline into a guided workspace |
| Backend design | Separates collectors, scoring, strategy generation, reports, and source status |
| Engineering judgment | Prioritizes transparency and safe collection over brittle automation |

## Outcome

The system provides a working prototype for client-scoped content planning:

- create or select a client profile;
- collect relevant trend and SEO signals;
- normalize and score keyword opportunities;
- generate content pillars, ideas, briefs, and weekly reports;
- review ideas through approval and board workflows.

> [!NOTE]
> This case study focuses on architecture, workflow, trade-offs, and technical contribution. It does not include source dumps, credentials, local data exports, or private client material.
