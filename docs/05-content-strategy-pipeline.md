[Back to README](../README.md)

# Content Strategy Pipeline

The central workflow turns client context and external signals into a weekly production plan.

```mermaid
flowchart LR
  profile[Client Profile] --> seed[Seed Keywords]
  seed --> seo[SEO Research]
  seed --> trends[Trend Collection]
  seo --> intent[Intent Classification]
  trends --> intent
  intent --> pillars[Evergreen Pillars]
  pillars --> ideas[Weekly Ideas]
  ideas --> approvals[Idea Approvals]
  approvals --> briefs[Production Briefs]
  briefs --> scenes[Content Scenes]
  scenes --> board[Weekly Board]
  board --> report[Weekly Report]
```

## Pipeline Stages

| Stage | Purpose |
| --- | --- |
| Client profile | Captures industry, offer, audience, market, tone, CTA, and risk boundaries |
| Seed keywords | Establishes the search and trend universe |
| SEO research | Expands topics and estimates demand |
| Intent classification | Labels buyer stage and content purpose |
| Pillar generation | Groups topics into durable strategic themes |
| Weekly ideas | Converts research into publishable content candidates |
| Approval workflow | Lets humans review, approve, reject, or move ideas |
| Production briefs | Creates more detailed creator-facing guidance |
| Weekly report | Summarizes strategy for operational or stakeholder review |

## AI Role

AI assists with ideation, summaries, and creative guidance. The workflow is designed so AI is useful but not a hard dependency: rule-based fallbacks and persisted artifacts keep the system operable when providers are unavailable.

```mermaid
stateDiagram-v2
  [*] --> DraftIdea
  DraftIdea --> NeedsReview
  NeedsReview --> Approved
  NeedsReview --> Rejected
  NeedsReview --> NeedsRevision
  NeedsRevision --> NeedsReview
  Approved --> BriefGenerated
  BriefGenerated --> ScheduledOnBoard
  ScheduledOnBoard --> Reported
  Rejected --> [*]
  Reported --> [*]
```
