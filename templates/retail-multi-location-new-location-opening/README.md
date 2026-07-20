> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/new-location-opening/retail-multi-location-new-location-opening)** — one-click deploy, no setup.

# Retail (Multi-Location) - New-Location Opening

Turns a greenlit retail store location into a tracked opening project - permits, vendor orders, fixtures, staffing, POS configuration, and grand-opening marketing - with deadline alerts and a daily progress brief until doors open.

## What it does

1. Builds a phased opening checklist (permits, vendors, staffing, systems, marketing, walk-through) with due dates anchored to the target opening day, and tracks every item through to sign-off.
2. Monitors deadlines daily and sends targeted email alerts to the opening lead for overdue items and to the district manager for escalations that put the opening date at risk.
3. Guides Lightspeed Retail provisioning for the new location - catalog import, tax configuration, staff accounts, and end-to-end register testing.
4. Walks through Shopify POS setup - hardware pairing, location configuration, staff PINs, payment processing, and end-of-day close testing.
5. Tracks vendor and fixture orders against confirmed delivery dates, flagging late deliveries and triggering receiving workflows in Lightspeed when inventory arrives.
6. Manages the staffing pipeline from job posting through payroll enrollment and POS training completion for all opening-day staff.
7. Drafts, schedules, and logs grand opening email and SMS campaigns to the local customer base, timed at T-3 and T-1.
8. Delivers a concise daily progress brief to the opening lead and DM from T-30 through T+3, showing checklist status, overdue items, and a plain on-track/at-risk/critical assessment.

## Key integrations

- **Lightspeed Retail** - Multi-location inventory, product catalog, tax configuration, staff accounts, and POS register setup for the new store.
- **Shopify POS** - Hardware provisioning, location activation, payment processing, staff access, and end-of-day reporting.
- **Email** - Deadline alerts and escalations to the opening lead and district manager, plus customer-facing grand opening announcement campaigns.
- **SMS** - Grand opening text message to opted-in local customers, coordinated with the email announcement schedule.

## Getting started

1. **Import this workspace** into Gamut by uploading the zip through the Gamut workspace import screen.
2. **Run agent-onboarding** - type `/agent-onboarding` (or trigger the skill from the sidebar). The agent will ask 8 questions about your brand, Lightspeed and Shopify setup, email/SMS platforms, team contacts, and operating geography. Answers are saved to `config.json` and written into the agent's context.
3. **Start your first project** - tell the agent: "Start a new opening for [Store Name] at [Address], opening [Target Date]." The agent will create the full checklist, assign due dates, and begin daily monitoring.

## Customization notes

- The default checklist phases and due-date offsets are based on a standard 90-day ramp. If your typical opening window is shorter or longer, tell the agent and it will compress or extend the timeline accordingly.
- Permit requirements vary by municipality. The agent flags the most common categories; you should add jurisdiction-specific items (e.g., liquor license, food handler permit) during or after onboarding.
- If your organization uses a different POS system or inventory platform alongside Lightspeed and Shopify, tell the agent during onboarding so it can adjust the systems checklist.

Relevant subsegments: RETL
