[Back to README](../README.md)

# Engineering Decisions

## Decision Log

| Decision | Why | Trade-Off |
| --- | --- | --- |
| FastAPI backend | Quick iteration, clean API surface, strong fit for Python data workflows | Production hardening would require job queues, auth, and persistence |
| React/TanStack frontend | Provides a structured workspace for multi-step strategy flows | More frontend state management than a simple dashboard |
| Local artifacts before database | Makes prototype data easy to inspect and debug | Not suitable for multi-user production history |
| Optional AI layer | Keeps the product useful even when model providers are unavailable | Requires careful UX to distinguish generated guidance from verified data |
| Source status visibility | Builds trust by showing collection failures and warnings | Adds extra product surface area |
| Conservative TikTok collection | Avoids unsafe or brittle automation patterns | Less comprehensive than aggressive scraping |
| Profile-scoped workflow | Keeps recommendations tied to business context | Requires more setup than generic trend browsing |

## Core Principle

Compass prioritizes explainable recommendations over raw volume. A smaller set of client-fit ideas is more useful than a large list of generic trends.

## Architecture Trade-Off

The prototype architecture favors learning speed. That is appropriate for validating workflow value, but a production version needs:

- persistent database schema;
- background job orchestration;
- observability;
- authentication and tenant boundaries;
- source quota management;
- stronger report versioning.
