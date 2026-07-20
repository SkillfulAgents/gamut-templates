> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/invoice-ar-chase/cleaning-invoice-ar-chase)** — one-click deploy, no setup.

# Cleaning/Janitorial - Invoice & AR Chase

Commercial cleaning operators on net terms often carry significant unpaid AR with no dedicated staff to chase it. This agent monitors every open invoice, sends polite owner-voiced follow-ups that escalate in firmness as invoices age, automatically flags accounts for escalation when they go too long without payment, and delivers a weekly cash and receivables digest so the owner always knows where they stand.

## Who this is for

Owner-operators running commercial cleaning or janitorial businesses who bill commercial clients on net terms, have no dedicated AR staff, and need a consistent, professional process for following up on slow-paying accounts without damaging client relationships.

Relevant subsegments: CLEN

Best fit for businesses managing 10–150 commercial accounts with recurring invoices and meaningful open AR at any given time.

## What it does

1. **Monitor & detect unpaid invoices** — pulls the open invoice list from Swept, Janitorial Manager, or an exported CSV; flags overdue invoices; and categorizes them into aging buckets (1–14 days, 15–30 days, 31–60 days, 60+ days)
2. **Prioritize & plan outreach** — sorts flagged invoices by dollar amount and days overdue, checks each client's payment history, and determines the correct contact step (first reminder, second reminder, firm notice, or escalation notice)
3. **Draft & send follow-up messages** — writes all outreach in the owner's voice, escalating in tone with AR age; sends by email by default (SMS optional); always BCCs the owner
4. **Log outcome & track responses** — records every contact attempt in the AR tracker, marks invoices resolved when payment is received, and flags disputes for owner review without auto-responding
5. **Weekly cash & AR digest** — every Monday (or configured day) delivers a summary of total open AR by aging bucket, top overdue invoices, payments received in the past 7 days, and accounts due for follow-up this week

## Key integrations

- **Swept** — job management and client billing
- **Janitorial Manager** — operations and invoicing
- **Email** — follow-up outreach to commercial clients
- **Slack** — owner notifications and weekly AR digest (optional)

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will walk through your business details and configure the agent for your AR process
3. Give the agent its first task: *"Show me all invoices over 30 days past due and draft a follow-up for each one."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`. Edit either file to update AR age thresholds, outreach channels, owner name for sign-offs, or the Slack digest target.

## Pattern

Vertical / NON-TECH — Cleaning & janitorial AR ops
