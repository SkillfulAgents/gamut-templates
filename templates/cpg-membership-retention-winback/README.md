> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/membership-retention-win-back/cpg-membership-retention-winback)** — one-click deploy, no setup.

# CPG/Consumer Brand - Membership Retention & Win-back

Monitors subscription and membership activity signals to catch customers heading toward churn, then triggers personalized retention plays - pause offers, win-back sequences, or re-engagement campaigns - before the cancel happens.

---

## What it does

1. Pulls daily activity signals from Recharge Subscriptions and Shopify - skips, payment failures, inactivity, downgrades, and support ticket intent - and builds a churn risk profile for each flagged subscriber.
2. Scores customers into three risk tiers (high/medium/low) based on signal severity and account history, then segments further by LTV, tenure, and subscription type to match the right intervention to the right customer.
3. Triggers targeted Klaviyo flows for each retention play: pause offers for frequency-fatigued customers, retention discounts for price-sensitive accounts, product swap recommendations for dissatisfied ones, and win-back sequences for recently lapsed subscribers.
4. Works failed payments through a structured dunning process - first-failure email within 2 hours, SMS escalation on second failure for opted-in customers, and human escalation before Recharge auto-cancels on third failure.
5. Runs a standing win-back process against lapsed subscribers from the past 90 days, segmenting by time-since-cancel to personalize messaging and offer depth.
6. Enforces guardrails automatically: suppresses repeat offers within a configurable window, gates discount application behind an approval step if required, and escalates high-LTV accounts to a human regardless of automated play status.
7. Tracks retention outcomes by play type and win-back conversion by timing window, and surfaces a weekly report on revenue saved, discount cost, and escalation status.

---

## Key integrations

- **Shopify** - Order history, product catalog, and inventory availability for personalizing retention and product swap recommendations.
- **Recharge Subscriptions** - Subscription state, skip and pause history, payment failure events, and renewal dates. Supports both Recharge v1 (legacy) and v2 (Checkout on Shopify).
- **Klaviyo** - All customer-facing email and SMS flows: pause offers, retention discounts, product fit, win-back sequences, and payment update messages. Profile properties and opt-in status are read before any message is triggered.
- **Email/SMS (via Klaviyo)** - Outbound retention and win-back messages sent through Klaviyo flows, with SMS gated to customers with a valid opt-in status.

---

## Getting started

1. **Import this workspace** into Gamut by uploading the zip file through the workspace import flow.
2. **Run the agent-onboarding skill** - type `/agent-onboarding` in your first message. The agent will ask 8 configuration questions covering your Shopify and Recharge credentials, Klaviyo flow IDs, churn thresholds, discount rules, and escalation preferences. Your answers are saved to `.claude/config.json` and written into the agent's context.
3. **Start your first session** with the prompt: "Run the daily churn risk scan and report any Tier 1 or Tier 2 customers flagged today."

---

Relevant subsegments: CPG
