> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/invoice-ar-chase/hvac-invoice-ar-chase)** — one-click deploy, no setup.

# HVAC/Plumbing/Electrical - Invoice & AR Chase

Stop chasing payments by hand. This Gamut agent connects to ServiceTitan or FieldEdge, tracks every open invoice against a 30/60/90/120-day aging ladder, drafts follow-up messages in your voice, and delivers a weekly cash and AR digest — so the office can close the books without burning hours on collections.

---

## Who this is for

Trade contractors running service or installation businesses who need a faster, more consistent way to collect on outstanding invoices without hiring a dedicated AR person or spending owner/office time manually following up.

- HVAC contractors (residential service, commercial maintenance, new installs)
- Plumbing contractors (residential and commercial)
- Electrical contractors (residential, commercial, industrial)
- Multi-trade contractors running ServiceTitan or FieldEdge

**Relevant subsegments: HVAC**

---

## What it does

1. Pulls all open invoices from ServiceTitan or FieldEdge each day and classifies them by aging tier: current (0–30), 30–60, 60–90, 90–120, and 120+ days past due.
2. Drafts tiered follow-up messages calibrated to how overdue the invoice is — friendly reminders for current invoices, escalated language for 90+ day accounts — all in the business owner's voice.
3. Presents every draft for your approval before anything is sent. The agent never auto-sends to customers.
4. Logs all outreach attempts, customer responses, and payment promises against each invoice so you always know the full history.
5. Handles commercial accounts (AP contacts, PO/invoice reference format, net terms) separately from residential.
6. Escalates 90+ day invoices to the owner with a recommended next action: collections referral, lien notice, service hold, or write-off.
7. Delivers a weekly cash and AR digest — open balance by aging tier, week-over-week change, invoices collected, and invoices needing immediate attention.

---

## Key integrations

- **ServiceTitan** — primary field service platform; pulls open invoices, customer records, job data, and contact information
- **FieldEdge** — alternative field service platform; same invoice and customer data pull
- Email or SMS (via ServiceTitan/FieldEdge messaging or your preferred channel) for customer outreach
- Optional: accounting system (QuickBooks, etc.) for cross-referencing payment status

---

## Getting started

1. **Import this workspace** into Gamut using the workspace import flow.
2. **Run the `agent-onboarding` skill** — it will walk you through connecting ServiceTitan or FieldEdge, setting your aging thresholds, and calibrating tone for residential vs. commercial accounts.
3. **Give the agent its first task:** "Pull today's open invoices and show me what's overdue by tier." Review the AR snapshot, then ask it to draft follow-ups for a specific tier to see the messages in your voice.

---

## Configuration

**`CLAUDE.md` — `## Your context` section**
After onboarding, the agent fills in your business context here: trade type, platform connection details, commercial account list, tone preferences, escalation contacts, and weekly digest schedule.

Editable fields include:
- ServiceTitan or FieldEdge credentials / API connection
- Residential vs. commercial customer classification
- Tone notes (formal, casual, owner's name to sign messages)
- Escalation contact for 90+ day invoices
- Preferred outreach channel and weekly digest day/time
- Late fee or lien notice policies

---

## Pattern

Vertical skin — HVAC/Plumbing/Electrical flavor of the horizontal **Invoice & AR Chaser** template. Specialized for trade contractors using ServiceTitan or FieldEdge.
