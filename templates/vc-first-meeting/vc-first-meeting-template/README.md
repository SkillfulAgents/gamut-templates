# VC First Meeting Agent

A two-mode agent for VC partners. Give it a company name before a meeting and it produces a sharp one-page research brief. Give it raw notes after a meeting and it produces a clean, structured deal record — thesis-scored, CRM-ready, with a follow-up email draft.

---

## What it does

### Mode 1: Pre-meeting prep

Tell the agent you have a meeting coming up. It researches the company across web, Crunchbase, LinkedIn, and news, then produces a one-page brief covering:

- Company snapshot (what they do, stage, funding, HQ, headcount)
- Team assessment (founders, backgrounds, "why them" signal)
- Thesis fit (mapped to your fund's actual criteria)
- Competitive landscape (2–3 comps, differentiation)
- Key questions (5–7 specific questions to ask — not generic VC questions)
- Recent signals (launches, hires, press hits)

The brief is saved to `/workspace/briefs/` and displayed in full.

### Mode 2: Post-meeting structuring

Paste in raw notes or a transcript after a meeting. The agent structures them into a clean deal record:

- Company basics and team assessment
- Problem/solution with differentiation analysis
- Business model and traction metrics
- Funding history and current raise details
- Thesis fit score (Strong Fit / Fit / Weak Fit / No Fit) tied to your criteria
- Concerns and open risks
- Agreed next steps
- Follow-up questions for the next conversation

The record is saved to `/workspace/deals/`, pushed to your CRM if configured, and a follow-up email draft is generated for your review.

---

## How to invoke

Just tell the agent what you need in plain language. Examples:

**Pre-meeting**
- "Prep me for my 2pm with Acme AI"
- "I have a first meeting with Runway tomorrow — what should I know going in?"
- "Research Cohere before my call on Thursday. Here's their intro email: [paste]"

**Post-meeting**
- "I just met with Acme AI. Here are my notes: [paste notes]"
- "Structure my notes from the Runway call: [paste transcript]"
- "Clean up this transcript — [paste raw transcript]"

You do not need to specify a mode. The agent infers from context.

---

## Output examples

### Pre-meeting brief (example structure)

```
## Acme AI — Pre-Meeting Brief
June 15, 2026

### Company Snapshot
Acme AI builds automated data pipeline tooling for mid-market SaaS teams.
Stage: Seed | Raised: $2.1M | Last round: $2M seed, March 2026 (led by Haystack)
Founded: 2024 | HQ: San Francisco | ~12 employees
Website: acme.ai

### Team
Jane Doe (CEO) — ex-Google Brain, ML infra lead. Built similar internal tooling at scale.
Bob Smith (CTO) — ex-Stripe data eng. Knows the customer pain firsthand.
Why them: Both have lived this problem at companies where it was acute. Strong technical depth.

### Thesis Fit
Hits: B2B SaaS infra (sector), Seed stage (stage), SF-based (geo), technical founders (team)
Uncertain: Market size — mid-market SaaS data pipelines is a real pain but TAM math unclear
Initial concern: Fivetran and dbt are both well-capitalized and moving into this space

### Competitive Landscape
- Fivetran: ELT leader, enterprise-focused, $5.6B valuation — moving downmarket
- dbt Labs: transformation layer, $4.2B, increasingly full-stack
- Airbyte: open-source ELT, strong community, $181M raised
Differentiation claim: workflow automation layer on top of pipelines, not the pipelines themselves

### Key Questions
1. Fivetran just launched workflow automation — how do you think about competing with them on this specifically now that they're moving into your layer?
2. Your customers are mid-market SaaS — how are you finding them, and what does your sales motion look like at $2M ARR?
3. You have 12 customers. What does retention look like — any churn, and what's driven it?
4. The technical co-founders are both ex-FAANG. Have you sold to companies that aren't like the ones you came from?
5. What does your product not do yet that your best customers are asking for?

### Recent Signals
- Launched v2.0 with workflow builder (May 2026)
- Hiring: 2 AE roles posted (signal: starting to build sales)
- Featured in The Information, April 2026 — "10 startups to watch in data infra"
```

### Post-meeting deal record (example structure)

```
## Acme AI — Deal Record
First meeting: June 15, 2026 | Partner: [Your name]

### Company Basics
Stage: Seed | Sector: B2B SaaS Infra | HQ: San Francisco | acme.ai

### Team Assessment
Jane Doe (CEO): Clear domain conviction. Answered competitive questions without defensiveness.
Bob Smith (CTO): Strong on product depth, quieter on go-to-market.
Why them: Jane specifically cited building this at Google and knowing "exactly where it breaks at 100 engineers."

### Problem / Solution
Problem: Mid-market SaaS teams spend 40%+ of eng time on pipeline maintenance.
Solution: Automated workflow layer that sits on top of existing ELT tools.
Differentiation: Not replacing Fivetran — designed to work with it. Different layer.

### Business Model
PLG to sales-assist. $2K–$8K/month per customer. Mostly annual contracts.

### Traction
$200K ARR | 12 customers | "Low single-digit churn" [their words, no exact figure given]

### Funding
Raised $2.1M total | Raising $3M seed | Pre-money: not discussed | Lead: TBD

### Thesis Fit
Thesis Fit: Fit
Rationale: Hits stage, sector, geo, and team criteria. TAM math needs work but the pain is real
and the differentiation story is credible. No dealbreakers at this stage.
Criteria check:
  - Stage (Seed): Pass — raising $3M seed
  - Sector (B2B SaaS Infra): Pass — clear fit
  - Technical founder: Pass — both founders are technical
  - Market size ($1B+ TAM): Uncertain — they cited $8B but didn't show the math

### Concerns / Risks
- TAM math unsubstantiated — need to see their model
- Fivetran competitive threat underestimated; they brushed it off
- No sales hire yet despite PLG-to-sales motion claim

### Next Steps
- They're sending the deck by EOW
- We offered intro to portfolio company CTO [confirm internally first]
- Internal: share with partner group; bring to Monday meeting if deck holds up

### Follow-up Questions
1. Walk me through your TAM math — how are you sizing the addressable market?
2. What does a typical expansion look like — how do customers grow from $2K to $8K/month?
3. You said "low single-digit churn" — can you share the exact figure?
4. Have you talked to Fivetran about a partnership? Why or why not?
```

---

## CRM integration

After onboarding, deal records can be automatically pushed to:

- **Notion** — creates a new page in your deals database with all structured fields
- **Airtable** — adds a row to your deal tracking table
- **HubSpot** — creates or updates a Deal record in your configured pipeline
- **Salesforce** — creates or updates an Opportunity record

CRM push happens automatically in post-meeting mode if configured. If the push fails, the record is saved locally and you're notified.

To configure or change your CRM, re-run onboarding: "Re-run onboarding" or "Update my CRM settings."

---

## How it pairs with other agents

**Thesis Screener Agent**: If you're using the Thesis Screener, this agent can import your thesis criteria from its config automatically during onboarding — no need to re-enter them.

**Pipeline Sync Agent**: If you're using the Pipeline Sync Agent, deal records written by this agent are picked up and included in pipeline reviews automatically. No extra steps needed.

Together, the three agents cover the full first-meeting-to-pipeline workflow: screen inbound → prep for first meeting → structure notes → sync to pipeline.

---

## Setup

1. Import this workspace into Gamut
2. The agent-onboarding skill runs automatically on first use
3. It will ask you about your fund thesis, CRM, and preferences — takes about 5 minutes
4. Confirm with a smoke test on a fake company

To re-run onboarding at any time: "Re-run onboarding" or edit `/workspace/config.json` directly.
