# Landscaping/Lawn - Local / Seasonal Signal Watch

Landscaping and lawn care operators live and die by timing — a storm cleanup call made two days after the event lands a job; one made two weeks later does not. This agent watches the signals that create urgency — weather events, permit filings, new-mover lists, and seasonal windows — and turns them into a daily prioritized prospect list with outreach context ready to act on.

Relevant subsegments: LAND

## Who this is for

Owner-operators and sales leads at residential or commercial landscaping and lawn care businesses who want to stay ahead of outreach timing rather than relying on word-of-mouth or reactive marketing. Best fit for operations in 1–5 service territories that use Jobber or Aspire for job and client management and want a consistent system for converting local signals into booked work.

## What it does

1. **Monitor inbound signals** — scans weather and storm events, county permit filings, new-mover lists, and calendar-based seasonal triggers across the configured service territory on a daily schedule
2. **Score and prioritize prospects** — applies a priority ranking based on signal overlap, recency, and opportunity type; separates existing/former Jobber or Aspire customers from net-new prospects
3. **Enrich prospect records** — cross-references Jobber and Aspire for service history and notes; flags records missing contact details so nothing slips through without a lookup
4. **Build the prioritized outreach list** — compiles all enriched prospects into a sorted list with signal context, recommended outreach channel, timing window, and a 1–2 sentence talking point opener per prospect
5. **Push to Jobber or Aspire** — creates lead or contact records, attaches signal notes, and assigns follow-up tasks with outreach dates for approved prospects
6. **Weekly signal digest** — every Monday delivers a summary of signals detected, prospects added, top priority targets, upcoming seasonal windows, and any prior-week prospects that converted to booked jobs

## Key integrations

- **Jobber** — primary field service and CRM platform; used for client lookup, lead creation, and follow-up task assignment
- **Aspire** — landscaping-specific business management; used for client records, job history, and sales pipeline when Aspire is the system of record
- **County permit portals / data feed** — source for new construction and landscaping permit filings in the service territory
- **New-mover data provider** — MLS feeds or list services (e.g., ListSource, DataTree) for recently closed home sales and new residents
- **Email / Slack** — delivery channel for the daily prioritized prospect list and weekly signal digest

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your service territory, connected systems, signal preferences, and Jobber/Aspire setup so the agent is configured for your market
3. Give the agent its first task: *"Pull all signals from the past 7 days, score the prospects, and show me the top 10 with talking points."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`. Edit either file to update service territory zip codes, signal source URLs or credentials, seasonal trigger dates, the Jobber or Aspire connection, auto-push permissions, and the digest delivery channel.

## Pattern

Vertical / NON-TECH — Landscaping & lawn care local market intelligence
