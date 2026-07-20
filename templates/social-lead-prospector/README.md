> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/sales-pipeline/social-lead-prospector)** — one-click deploy, no setup.

# Social Lead Prospector

Finds targeted leads on LinkedIn and Facebook using your local browser — no ad spend, no scraping APIs, no bot detection issues — and drafts personalized outreach for your review before anything is sent.

## What it does

- Searches LinkedIn and/or Facebook for people matching your target customer profile
- Cross-references your existing customers so you never contact someone twice
- Drafts a short, personalized message per prospect based on their actual profile
- Stages everything for your approval before any message goes out
- Logs sent messages and optionally sends you a daily summary

## Setup

Import this workspace into Gamut, launch the agent, and follow the onboarding conversation. You'll be asked about:

1. Your business and ideal customer profile
2. Which platforms to prospect on (LinkedIn, Facebook, or both)
3. How to identify existing customers (Gmail, CSV, or skip)
4. Outreach tone and goal
5. Prospecting schedule

**Before the first run:** make sure you're logged into LinkedIn and/or Facebook in Google Chrome on your machine. The agent uses your browser session directly.

## Outputs

| File | Contents |
|------|----------|
| `reports/leads.csv` | All prospects found (name, URL, profile notes, date added) |
| `reports/outreach-drafts.md` | Drafted messages staged for your review |
| `reports/sent-log.csv` | Log of approved and sent messages |

## Customization

Edit `CLAUDE.md` → **Your context** at any time to refine the target profile, update the outreach style, or change the schedule. Or re-run the `agent-onboarding` skill from the agent's chat.
