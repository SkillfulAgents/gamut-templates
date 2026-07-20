> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/membership-retention-win-back/dtc-membership-retention-winback)** — one-click deploy, no setup.

# DTC/E-commerce - Membership Retention & Win-back

For DTC brands with subscriptions or memberships, every churned member is a customer acquisition cost that goes to waste. The signals that predict churn — inactivity, payment failures, declining purchase frequency — are visible in Shopify and the subscription platform weeks before a cancellation happens, but most brands only see them after the member is already gone. This agent watches those signals in real time, executes the right retention play before the cancellation, and runs win-back sequences for recently churned members while the brand is still top of mind.

## Who this is for

DTC founders, retention managers, and e-commerce operators with a subscription or membership program who want to systematically reduce churn and recover lapsed customers without building and maintaining separate retention workflows.

Relevant subsegments: DTC

Best fit for brands with 500+ active subscribers using Shopify with Recharge or a native subscription app, with a defined retention offer set.

## What it does

1. **Signal monitoring** — daily pull of inactivity, payment failure, downgrade, and cancellation signals from Shopify and the subscription platform; expansion signals for high-frequency purchasers not yet on a subscription
2. **Risk scoring and segmentation** — scores each flagged member 0-100 on churn risk based on days since activity, payment health, and complaint history; buckets into Healthy / At-Risk / Churned-Recent / Lapsed
3. **At-risk retention plays** — personalized re-engagement email for inactive subscribers; pause offer for members about to cancel; polite payment-update sequence for failed charges
4. **Win-back sequences** — 3-touch win-back sequence for recently churned members (Day 1, Day 7, Day 14), with escalating offers and a cap per customer per 90-day window
5. **Lapsed reactivation** — re-engagement emails for former customers whose last purchase exceeds the configured lapsed threshold, with a discount or bundle offer triggered only after the first touch goes unanswered
6. **Retention digest** — weekly Slack summary of members actioned, play breakdown, save rate, win-back conversions, and any payment-failure spikes

## Key integrations

- **Shopify** — order history, subscription status, customer records
- **Recharge / subscription app** — subscription billing status, pause/cancel records
- **Klaviyo / Attentive / HubSpot** — email and SMS delivery for retention outreach
- **Slack** — weekly digest and spike alerts
- **Google Sheets / CRM** — logging of all plays and outcomes

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your subscription program, risk thresholds, retention offers, and reporting preferences
3. Give the agent its first task: *"Run today's retention check and show me all at-risk members."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`.

## Pattern

Vertical / NON-TECH - DTC/E-commerce brands with subscription or membership programs

Relevant subsegments: DTC
