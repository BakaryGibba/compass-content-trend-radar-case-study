[Back to README](../README.md)

# Diagrams

This folder contains editable Mermaid source files. GitHub renders Mermaid inside Markdown automatically, and these `.mmd` files can also be exported to PNG/SVG using Mermaid CLI.

| File | Purpose |
| --- | --- |
| `architecture.mmd` | System architecture across frontend, backend, sources, AI, and storage |
| `collection-workflow.mmd` | Data collection flow from client profile to normalized trend signals |
| `strategy-pipeline.mmd` | End-to-end strategy generation workflow |
| `source-fallback.mmd` | Source reliability and fallback behavior |
| `data-model.mmd` | Conceptual ERD for production data modeling |
| `frontend-navigation.mmd` | Main frontend journey and route structure |

Suggested export command:

```bash
mmdc -i diagrams/architecture.mmd -o diagrams/architecture.png
```
