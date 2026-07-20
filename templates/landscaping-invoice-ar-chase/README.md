> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/invoice-ar-chase/landscaping-invoice-ar-chase)** — one-click deploy, no setup.

# Landscaping/Lawn - Invoice & AR Chase

Landscaping and lawn care operators often carry significant unpaid AR — especially with commercial clients like HOAs, property managers, and municipalities — with no dedicated staff to follow up. This agent monitors every open invoice in Jobber or Aspire, sends polite owner-voiced follow-ups that escalate in firmness as invoices age, and delivers a weekly cash and receivables digest so the owner always knows where they stand.

## Who this is for

Owner-operators running landscaping, lawn maintenance, or grounds care businesses who bill residential or commercial clients on net terms, have no dedicated AR staff, and need a consistent, professional process for following up on slow-paying accounts without damaging client relationships.

Relevant subsegments: LAND

Best fit for businesses managing 15–200 active accounts — from residential lawn routes to commercial property maintenance contracts — with recurring invoices and meaningful open AR at any given time.

## What it does

1. **Monitor & detect unpaid invoices** — pulls the open invoice list from Jobber (Past Due filter) or Aspire (Receivables Aging report); flags overdue invoices; and categorizes them into aging buckets (1–14 days, 15–30 days, 31–60 days, 60+ days)
2. **Prioritize & plan outreach** — sorts flagged invoices by dollar amount and days overdue, checks each client's payment history, distinguishes between residential homeowners and commercial AP contacts, and determines the correct contact step (first reminder, second reminder, firm notice, or escalation notice)
3. **Draft & send follow-up messages** — writes all outreach in the owner's voice referencing the specific job (lawn maintenance, mulch installation, irrigation startup), escalating in tone with AR age; sends by email by default (SMS optional); always BCCs the owner
4. **Log outcome & track responses** — records every contact attempt in the AR tracker, marks invoices resolved when payment is received, and flags disputes or commercial PO delays for owner review without auto-responding
5. **Weekly cash & AR digest** — every Monday (or configured day) delivers a summary of total open AR by aging bucket, top overdue invoices, payments received in the past 7 days, and accounts due for follow-up this week

## Key integrations

- **Jobber** — job management, client billing, and client hub payment portal
- **Aspire** — operations, contract management, and receivables aging reporting
- **Email** — follow-up outreach to residential and commercial clients
- **Slack** — owner notifications and weekly AR digest (optional)

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will walk through your business details and configure the agent for your AR process
3. Give the agent its first task: *"Show me all invoices over 30 days past due and draft a follow-up for each one."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`. Edit either file to update AR age thresholds, outreach channels, owner name for sign-offs, how to handle commercial vs. residential clients differently, or the Slack digest target.

## Pattern

Vertical / NON-TECH — Landscaping & lawn care AR ops
