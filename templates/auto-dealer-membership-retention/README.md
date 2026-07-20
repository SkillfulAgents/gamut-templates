> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/membership-retention-win-back/auto-dealer-membership-retention)** — one-click deploy, no setup.

# Auto Dealer/Service - Membership Retention & Win-back

Auto dealerships and service centers that offer maintenance memberships or service contracts lose customers silently — members simply stop booking, let renewals lapse, or cancel without a word. By the time the service manager notices, the revenue is already gone. This agent watches visit frequency, billing events, and CRM engagement signals across your DMS and CRM platforms, flags at-risk members before they churn, and drafts personalized win-back and rebook outreach so your team can act fast — not after the fact.

---

## Who this is for

- Auto dealerships and service centers running prepaid maintenance plans, oil-change memberships, tire bundles, or multi-visit service contracts
- Service managers who want proactive visibility into membership attrition before it hits the P&L
- BDC or service advisor teams who do retention outreach but lack a systematic trigger to know who to contact and when
- Any dealer group where membership revenue is a growing line item and churn tracking is still manual or spreadsheet-based

Relevant subsegments: AUTO

---

## What it does

1. **Monitor & detect at-risk members** — Pulls active membership records from your DMS (CDK, Reynolds & Reynolds) or CRM (VinSolutions) on a configured schedule and evaluates visit frequency drift, billing signals, and engagement gaps to classify members as at-risk, lapsing, or churned.
2. **Segment & prioritize outreach** — Groups flagged members by risk tier and membership type, prioritizes by contract value and re-engagement likelihood, and selects the right retention play (rebook prompt, renewal nudge, or win-back offer).
3. **Draft outreach** — Writes personalized SMS and/or email drafts for each flagged member referencing their specific contract and last visit, with a clear booking CTA — presented for human review before any message is sent.
4. **Log outcomes** — Records every outreach action and member response back to the CRM, marks recovered members, and escalates non-responders to the advisor call-back queue after the follow-up window.
5. **Alert & digest for service manager** — Delivers a churn health summary (active members, risk-tier breakdown, outreach response rates, recovered bookings) on a configured schedule, with immediate spike alerts when churn signals exceed threshold.

---

## Key integrations

- **CDK Global** — DMS for membership/service-contract data and visit history
- **Reynolds & Reynolds** — DMS alternative for member records and RO history
- **VinSolutions** — CRM for member communication preferences, outreach logging, and response tracking

---

## Getting started

1. **Import this workspace** into Gamut by uploading the zip through the workspace import flow.
2. **Run the `agent-onboarding` skill** — type `run agent-onboarding` as your first message. The skill will walk you through connecting your DMS and CRM, setting your membership tiers, configuring outreach thresholds, and identifying your service manager notification channel.
3. **Kick off your first retention scan** — once onboarding is complete, use the first task prompt provided at the end of onboarding to run your initial at-risk member detection pass.

---

## Configuration

After onboarding, your dealership-specific settings (DMS connection, membership tier definitions, visit-frequency thresholds, outreach preferences, manager contact) are stored in `config.json` at the workspace root. You can edit `config.json` directly to adjust thresholds or update contact info. The agent instructions in `CLAUDE.md` contain the full workflow logic and tone guidelines — edit the `## Your context` section if you need to add dealership-specific notes or override defaults.

---

## Pattern

Vertical / NON-TECH — Auto dealer & service center retention ops
