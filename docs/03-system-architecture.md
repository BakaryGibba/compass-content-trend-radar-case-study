[Back to README](../README.md)

# System Architecture

Compass uses a modular prototype architecture: a FastAPI backend owns orchestration and persistence, while the React workspace presents a guided strategy experience.

```mermaid
flowchart TB
  subgraph Experience
    UI[React + TanStack Workspace]
    Views[Dashboard / Keywords / Ideas / Briefs / Board / Reports / Profile]
    UI --> Views
  end

  subgraph API
    FastAPI[FastAPI Application]
    ProfileSvc[Client Profile Services]
    StrategySvc[Strategy Pipeline Services]
    CollectorSvc[Collector Services]
    ScoreSvc[Scoring + Intent Services]
    ReportSvc[Report Services]
    StatusSvc[Source Status Services]
  end

  subgraph Sources
    GT[Google Trends]
    TikTok[TikTok Source Family]
    SEO[SEO / Search Volume Sources]
    AI[Optional AI Provider]
  end

  subgraph Storage
    Raw[(Raw Artifacts)]
    Processed[(Processed JSON / CSV)]
    Reports[(Markdown / JSON Reports)]
  end

  UI --> FastAPI
  FastAPI --> ProfileSvc
  FastAPI --> StrategySvc
  StrategySvc --> CollectorSvc
  StrategySvc --> ScoreSvc
  StrategySvc --> ReportSvc
  CollectorSvc --> GT
  CollectorSvc --> TikTok
  CollectorSvc --> SEO
  StrategySvc -. optional .-> AI
  CollectorSvc --> Raw
  ScoreSvc --> Processed
  ReportSvc --> Reports
  FastAPI --> StatusSvc
```

## Component Responsibilities

| Component | Responsibility |
| --- | --- |
| React workspace | Guides the strategist through profile, research, approvals, board, and reports |
| FastAPI backend | Exposes API endpoints and coordinates strategy runs |
| Collector services | Retrieve Google Trends, TikTok, and SEO signals |
| Normalization services | Convert mixed source data into comparable strategy inputs |
| Scoring services | Rank opportunities by relevance, buyer intent, content potential, demand, and brand fit |
| AI services | Assist with suggestions and generation where enabled |
| Local storage | Keeps prototype artifacts inspectable and easy to debug |

## Architectural Boundary

Compass is intentionally not a production SaaS platform yet. The current design excludes authentication, billing, scheduled jobs, and database infrastructure so the prototype can focus on the strategy workflow and data-quality loop.
