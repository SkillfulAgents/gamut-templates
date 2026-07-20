> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/quote-estimate-follow-up/landscaping-quote-estimate-followup)** — one-click deploy, no setup.

# Landscaping/Lawn - Quote / Estimate Follow-up

Landscaping and lawn care operators send dozens of quotes that never get a response — not because the prospect said no, but because nobody followed up. This agent monitors every sent estimate in Jobber or Aspire, sends owner-voiced follow-up messages that escalate gently over time, alerts the owner before quotes expire, and reports win-rate by service type so the business knows where proposals are being won and lost.

## Who this is for

Owner-operators and sales leads running landscaping, lawn care, or lawn maintenance businesses who send quotes through Jobber or Aspire, have no dedicated sales staff to follow up on open proposals, and want a consistent process for nudging prospects without burning relationships.

Relevant subsegments: LAND

Best fit for businesses managing 15–200 active quotes per season across services like maintenance contracts, one-time cleanups, hardscape installs, or design/build projects.

## What it does

1. **Pull & categorize open quotes** — pulls all sent or awaiting-approval quotes from Jobber or Aspire, categorizes them by days since sent, and flags any approaching their expiration date
2. **Prioritize follow-up outreach** — sorts open quotes by dollar value and age, checks for any prospect activity, and determines the correct contact step (first follow-up, second follow-up, final nudge, or expiration warning)
3. **Draft & send follow-up messages** — writes all outreach in the owner's voice with job-specific details pulled from Jobber or Aspire; escalates tone gently over time; sends by email by default with SMS optional
4. **Log outcomes & update quote status** — records every contact attempt, marks quotes won or lost when decisions come in, and flags prospect replies that require owner input (scope changes, negotiations)
5. **Expiration & scheduling alerts** — sends a daily alert for quotes expiring within 3 days and can surface crew-calendar pressure when install slots are filling up
6. **Win-rate report & pipeline summary** — delivers a weekly pipeline summary showing total open quotes, win/loss counts, overall win rate, and win rate broken down by service type

## Key integrations

- **Jobber** — field service management, quote tracking, and client records for landscaping and lawn care operations
- **Aspire** — landscape business management platform for quotes, job costing, and crew scheduling
- **Email** — follow-up outreach to prospects
- **Slack** — owner notifications, expiration alerts, and weekly pipeline report (optional)

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your business, your quoting system, and your follow-up preferences, then configure the agent for your operation
3. Give the agent its first task: *"Show me all quotes that have been open for more than 7 days with no response and draft a follow-up for each one."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`. Edit either file to update follow-up timing windows, expiration warning lead time, dollar thresholds for owner-review escalation, service types tracked for win-rate, or the report delivery destination.

## Pattern

Vertical / NON-TECH — Landscaping & lawn care sales ops
