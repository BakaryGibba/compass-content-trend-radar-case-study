[Back to README](../README.md)

# Data and Storage

Compass uses local artifact storage for prototype speed, transparency, and debugging.

## Storage Model

```mermaid
erDiagram
  CLIENT_PROFILE ||--o{ STRATEGY_RUN : owns
  STRATEGY_RUN ||--o{ SOURCE_RESULT : collects
  STRATEGY_RUN ||--o{ KEYWORD_INTENT : produces
  STRATEGY_RUN ||--o{ CONTENT_PILLAR : groups
  CONTENT_PILLAR ||--o{ CONTENT_IDEA : inspires
  CONTENT_IDEA ||--o{ PRODUCTION_BRIEF : becomes
  CONTENT_IDEA ||--o{ BOARD_ITEM : tracks
  STRATEGY_RUN ||--o{ REPORT : summarizes

  CLIENT_PROFILE {
    string profile_id
    string client_name
    string industry
    string target_market
    string brand_tone
  }
  STRATEGY_RUN {
    string run_id
    datetime generated_at
    string status
  }
  SOURCE_RESULT {
    string source
    string status
    string warning
  }
  KEYWORD_INTENT {
    string keyword
    string intent
    string buyer_stage
    number score
  }
  CONTENT_IDEA {
    string idea_id
    string title
    string platform
    string approval_status
  }
```

## Artifact Types

| Artifact | Purpose |
| --- | --- |
| Raw source files | Debug collector behavior and source failures |
| Processed JSON/CSV | Store latest trends, intents, ideas, briefs, and source status |
| Markdown reports | Make weekly outputs readable outside the app |
| Frontend state | Remembers active profile and workflow context in the browser |

## Production Upgrade Path

A production Compass would move from local files to a relational database plus object storage:

- profiles, runs, ideas, briefs, approvals, and audit history in PostgreSQL;
- source artifacts and brand assets in object storage;
- asynchronous strategy jobs in a queue;
- versioned reports for client delivery.

> [!IMPORTANT]
> This case study does not include raw trend exports, local client outputs, logs, or generated report artifacts from the working project.
