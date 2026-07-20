> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/productivity-internal-ops/adhoc-analytics-answerer)** — one-click deploy, no setup.

# Ad-Hoc Analytics Answerer

> Turns a plain-English business question into a sourced answer with a chart and a short narrative -- removing the BizOps/analyst bottleneck for routine questions.

## What it does

Ad-Hoc Analytics Answerer watches the channel where your team asks data questions, interprets each plain-English question against your real metric definitions and business rules, finds the right tables, writes and runs a read-only SQL query, joins the data, and replies with a headline answer, a chart, a short narrative, and the exact query it ran. Every answer comes with assumptions and caveats spelled out (rows excluded, nulls dropped, partial periods), so the asker can trust it or check it.

It is built to take routine, repetitive questions off your analysts' plate -- "how many net-new logos last quarter," "what was churn in May," "top 10 accounts by usage this week" -- so people get a sourced answer in minutes instead of waiting in the BizOps queue. When a question is ambiguous or a metric is undefined, it asks rather than guessing. It never writes to your warehouse.

Works for any data-driven company with a warehouse: SaaS, fintech, e-commerce, retail, healthtech, insurtech, marketplaces, and more.

## What you'll need

- **Accounts:**
  - Data warehouse: Snowflake, BigQuery, Postgres, or Redshift (connected via a read-only role)
  - BI tool (optional): Looker, Tableau, Metabase, Mode, or similar -- for building/linking charts
  - CRM (optional): Salesforce, HubSpot, or similar -- if some questions need CRM fields
  - Slack (where people ask the questions and get answers)
- **API keys:** none required (warehouse and accounts connect via Gamut during onboarding; secrets stay in env, never in the prompt)
- **Other:** your table list or schema doc, and your metric definitions and business rules (what "customer," "active," "churn," "revenue" mean for you). A semantic layer reference if you have one.

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - Which warehouse you use and the read-only role/connection (names only -- secrets go in env)
   - Your known tables, schema doc, or semantic layer reference
   - Your metric definitions and business rules (test-account exclusions, what counts as a closed deal, etc.)
   - Your default date grain (day / week / month / quarter)
   - Who can ask questions and in which Slack channel
   - Your preferred result format (chart type defaults, narrative length)
   - Guardrails: max row limit and cost cap
3. Once setup finishes, give the agent a safe first task: *"Here's a question: [your question]. Do NOT run anything yet -- just tell me which tables you'd use, how you'd join them, the exact date range, and the query you'd run. I'll confirm before you execute."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` -- the agent's instructions and your configuration (written by onboarding).
- `.claude/skills/agent-onboarding/` -- first-run setup interview.

## Notes

- The agent runs READ-ONLY queries only. It never writes to your warehouse -- no INSERT, UPDATE, DELETE, or DDL -- and connects through a read-only role.
- Every answer includes the exact query it ran, so any result is reproducible and auditable.
- The agent uses YOUR metric definitions, not generic ones. If a term isn't defined or a question is ambiguous, it asks instead of guessing.
- Guardrails are enforced: queries respect your row limit and cost cap. If a question would exceed the cap, the agent narrows or aggregates and tells you it did.
- Warehouse credentials are stored as environment secrets, never written into the prompt or config. Onboarding captures connection and role names only.
- A BI tool and a CRM are optional -- without a BI tool the agent renders charts inline; without a CRM it answers warehouse-only questions.

Relevant subsegments: RVTK, MTTK, CSTK, CYBR, DEVT, DATA, AICO, FNTK, INSR, HRTK, LGTK, PPTK, SCTK, ECTK, SAAS, EDTK, CLTK, HLTK, RETL, DTC, MULT
