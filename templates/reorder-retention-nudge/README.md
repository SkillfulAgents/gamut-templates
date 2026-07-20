> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/customer-success-support/reorder-retention-nudge)** — one-click deploy, no setup.

# Reorder / Retention Nudge

> Stop churn before it happens — monitor purchase recency and frequency, surface at-risk and VIP segments, and auto-draft winback, reorder, and rebooking messages for your customers.

## What it does

Watch customer purchase recency and frequency, automatically draft winback, reorder, and rebooking messages, and surface VIP and at-risk segments before they churn.

The agent runs on a configurable cadence, pulling transaction and booking data from your connected platform, scoring customers by recency, frequency, and value, and classifying them into actionable segments (VIP, at-risk, lapsed, new). For at-risk and lapsed customers, it generates personalized outreach messages — ready to review and send through your email or SMS tool. A daily or weekly Slack digest keeps your team informed about segment shifts and customers that need attention, without any manual list-pulling.

## What you'll need

- **Accounts:** E-commerce, POS, or booking platform (Shopify, Square, or Mindbody); email/SMS tool (Klaviyo, Mailchimp, or Twilio); Slack workspace
- **API keys:** Listed in `.env.example` (fill in during setup)
- **Other:** Access to the relevant tools with read/write permissions

## Getting started

1. Import this template into Gamut (drag the zip into the agent import dialog).
2. On import, a setup session starts automatically. The **agent-onboarding** skill will ask:
   - Your name, role, and company name
   - Which systems/accounts to connect
   - Your preferences (notification channel, cadence, thresholds)
3. Once setup finishes, give the agent its first task.

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's instructions and role definition.
- `.claude/skills/agent-onboarding/` — first-run setup interview.
- `.env.example` — required environment variables (filled in during onboarding).

## Notes

This template is generic — it works for any organization in the relevant segments. All company-specific context is added during onboarding, not baked in.

Relevant subsegments: DTC, CPG, FITN, FOOD, RETL, AUTO, ECTK
