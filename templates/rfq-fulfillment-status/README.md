> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/productivity-internal-ops/rfq-fulfillment-status)** — one-click deploy, no setup.

# RFQ / Order & Fulfillment Status — Gamut Agent Template

Track the full quote-to-order-to-fulfillment pipeline, chase suppliers on overdue confirmations, surface backorder and freight exception alerts, and post a daily ops digest — without manual ERP drilling or inbox hunting.

## What this agent does

- **Monitors open RFQs and POs** — queries your ERP or order management system and identifies purchase orders that haven't received supplier acknowledgment past your configured SLA.
- **Chases suppliers automatically** — drafts and sends follow-up emails to suppliers referencing the exact PO number, line items, and days overdue.
- **Flags freight exceptions** — detects stalled shipments and carrier exceptions (delays, holds, failed delivery) and escalates critical issues to your designated contact via Slack.
- **Surfaces backorder risk** — identifies backordered line items that have exceeded your delay threshold and summarizes customer orders at risk.
- **Posts a daily ops digest** — delivers a structured pipeline briefing to your Slack ops channel every morning.

## Key systems

- **ERP / Order management:** NetSuite, SAP Business One, Epicor, Acumatica, or equivalent (CSV export and manual input also supported)
- **Email:** Supplier outreach and follow-up
- **Slack:** Daily digest and exception alerts

## Getting started

1. Import this template into Gamut.
2. Run the `/agent-onboarding` skill — it will walk you through connecting your ERP, email, and Slack, and set your SLA thresholds.
3. Try the first task below.

## First task to try

> **"Show me all open POs that haven't been acknowledged in 2+ days and draft supplier follow-ups."**

## Example tasks

- "Which shipments have had no tracking update in the last 3 days?"
- "What backorders are past their expected delivery date by more than a week?"
- "Send the daily ops digest to #supply-chain now."
- "Pull all open RFQs and show me which ones are oldest."
- "Draft a follow-up to [Supplier Name] for PO-4821."
- "Are there any freight exceptions on orders shipping this week?"

## Configuration (set during onboarding)

| Setting | Default | Description |
|---|---|---|
| PO acknowledgment SLA | 2 days | Flag POs with no supplier response after this many days |
| Shipment stale threshold | 3 days | Flag shipments with no tracking update after this many days |
| Backorder escalation | 7 days | Escalate backorders delayed beyond this many days past expected delivery |
| Digest channel | — | Slack channel for the daily ops briefing |
| Escalation contact | — | Slack handle or email for critical exception alerts |
| Email send mode | Draft for review | Whether the agent sends supplier emails automatically or queues drafts |

## Pattern and subsegments

- **Pattern:** Vertical, NON-TECH
- **Relevant subsegments:** WHSL, MFGR, LGST, AGRI, SCTK

Designed for operations teams in wholesale/distribution, manufacturing, 3PL/logistics, agribusiness, and supply chain-intensive industries.

---

Built with [Gamut](https://datawizz.com) by Datawizz.
