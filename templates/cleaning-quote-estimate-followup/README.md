> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/quote-estimate-follow-up/cleaning-quote-estimate-followup)** — one-click deploy, no setup.

# Cleaning/Janitorial - Quote / Estimate Follow-up

Cleaning and janitorial businesses send out dozens of quotes every week — and most of them go cold because there is no system to follow up. Owners are busy running crews, managing schedules, and handling jobs. Chasing estimates manually falls through the cracks, and potential customers who were ready to book end up going with whoever called them back first.

This agent fixes that. It tracks every sent quote, sends timed follow-up nudges in the owner's voice, flags estimates approaching expiry, and delivers a weekly pipeline and win-rate report — so nothing slips and the owner always knows where their pipeline stands.

---

## Who this is for

- Residential and commercial cleaning companies sending quotes via email, SMS, or a job management platform
- Janitorial service operators who rely on Swept, Janitorial Manager, or similar field-ops tools
- Owners and sales ops staff who want automated follow-up without sounding like a robot
- Any cleaning business where estimates regularly go unanswered and win-rate is a mystery

Relevant subsegments: CLEN

---

## What it does

1. **Monitor & Detect** — Pulls sent quotes daily from the connected job management system and categorizes each one: needs first follow-up, needs second follow-up, or expiring soon.
2. **Prioritize & Queue** — Sorts the follow-up queue by urgency (expiring first, then highest value, then oldest) and respects any daily send caps the owner sets.
3. **Draft & Send Follow-ups** — Writes short, warm messages in the owner's voice referencing the specific client and service, then sends them (or stages them for owner approval) via email, SMS, or in-app messaging.
4. **Log Outcome** — Records follow-up history, response status, and close data (won/lost/expired) against each quote for accurate reporting.
5. **Alert & Weekly Digest** — Sends expiry alerts when quotes are about to lapse and delivers a Monday morning pipeline digest with open value, win-rate, and top quotes by age.

---

## Key integrations

- **Swept** — crew scheduling and job management; quote and client data source
- **Janitorial Manager** — field operations and estimating platform; quote tracking and client records
- Email or SMS (configured during onboarding) for outbound follow-up messages
- Optional: Google Sheets or a connected CRM for pipeline logging

---

## Getting started

1. **Import this workspace** into Gamut by uploading the zip through the Gamut interface.
2. **Run the `agent-onboarding` skill** — type `run agent-onboarding` in the chat to start the guided setup. The skill will ask about your business, connected tools, follow-up timing, and preferred tone, then configure the agent automatically.
3. **Kick off your first task** by typing: `Check my open quotes and show me what follow-ups are due today.`

---

## Configuration

After onboarding, the agent writes a `config.json` file in the workspace root with your key settings (business name, connected systems, follow-up windows, auto-send preference, digest schedule). You can also edit the `## Your context` section at the bottom of `CLAUDE.md` directly to update preferences at any time.

---

## Pattern

Vertical / NON-TECH — Cleaning & janitorial sales ops
