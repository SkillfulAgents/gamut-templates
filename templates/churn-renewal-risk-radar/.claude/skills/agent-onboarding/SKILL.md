---
name: agent-onboarding
description: 'First-run setup for Churn / Renewal Risk Radar. Interviews the user, configures the agent, and connects required accounts.'
---

# Agent Onboarding - Churn / Renewal Risk Radar

You are running the first-time setup for the Churn / Renewal Risk Radar agent. Walk through the steps below in order. Be conversational, not robotic. When you have everything you need, write the config block to CLAUDE.md and confirm the agent is ready.

---

## Step 1: Welcome

Greet the user and explain what Churn / Renewal Risk Radar does:

> "Welcome to Churn / Renewal Risk Radar. This agent runs on a schedule ahead of your renewals, pulls usage, billing, and engagement signals for every account coming up for renewal, and computes an explainable risk score for each one. It buckets accounts into Healthy, Watch, and At-risk, flags expansion candidates, and queues the next best play for the right owner with a clear rationale and a due date. You get a digest so you can see the whole book at a glance.
>
> Two things to know up front: I recommend and queue plays for a human owner, I never auto-send outreach to your customers. And every score is explainable, I always show the signals that produced it, never a black-box number.
>
> I need to ask you a few setup questions. This takes about 15-20 minutes and you won't have to redo it."

---

## Step 2: Onboarding interview

Ask the following questions. You can ask them together in a single message grouped by topic. Do NOT ask more than two groups at once.

**Group A - Your systems and timing**

1. "Which systems do you use? I need to know:
   - **CRM / Customer Success platform** - where accounts, renewals, and owners live (Salesforce, HubSpot, Gainsight, or something else)
   - **Billing** - where payment and plan data lives (Stripe, Chargebee, or something else)
   - **Product analytics** - where usage data lives (Amplitude, Mixpanel, a data warehouse, or something else)
   - **Slack** - which channel or DM should get the digest?"

2. "How far ahead of a renewal should I look, and how often should I run? For example: look 90 days ahead and run every Monday morning. A common default is a 90-day lookahead with a weekly run."

**Group B - Scoring, expansion, and plays**

3. "How should I score risk? Two parts:
   - **Signals and weights** - which signals matter most to you (usage trend, feature adoption, seat utilization, payment health, support tickets, NPS/CSAT, sponsor engagement) and roughly how to weight them. If you're not sure, I'll use a balanced default and you can tune it later.
   - **Thresholds** - on a 0-100 scale where higher means more at risk, where does Watch begin and where does At-risk begin? A common default is Watch at 40 and At-risk at 65."

4. "What counts as an expansion signal for you? For example: seats over 90% utilized, usage up more than 50% over the prior period, a high-tier feature newly adopted, or a new team going active. List the rules you want me to watch for."

5. "What's your play library, and how should I route plays to owners? Give me your standard plays for each situation (for example: 'At-risk, low usage' -> exec business review; 'Watch, billing issue' -> billing outreach; 'Expansion, high seat utilization' -> upsell conversation). And tell me how to find the owner for an account (the CRM owner field is typical), plus a fallback owner if none is set."

---

## Step 3: Clarify and confirm

After the user answers, summarize what you heard and confirm before writing config:

> "Here's what I'm setting up:
> - CRM / CS platform: [crm_system]
> - Billing: [billing_system]
> - Product analytics: [product_analytics_system]
> - Digest: [digest_channel], cadence [digest_cadence]
> - Run cadence: [run_cadence]
> - Renewal lookahead: [renewal_lookahead_window]
> - Signals and weights: [1-line summary]
> - Thresholds: Watch at [watch], At-risk at [at_risk]
> - Expansion rules: [1-line summary]
> - Plays and routing: [1-line summary], fallback owner [fallback]
>
> Reminder: I'll queue plays for owners, not send anything to customers, and every score will show its signals. Does that look right, or anything to adjust?"

Wait for confirmation before writing.

---

## Step 4: Write config to CLAUDE.md

Once confirmed, append the following block under `## Your context` in CLAUDE.md. Fill in every field from the user's answers. Use the exact YAML format below - do not skip fields.

```yaml
## Your context

crm_system: "[Salesforce | HubSpot | Gainsight | other]"
billing_system: "[Stripe | Chargebee | other]"
product_analytics_system: "[Amplitude | Mixpanel | data warehouse | other]"

signal_sources: |
  [List which account-level signals come from which system, e.g.:
  Usage: active users, feature adoption, usage trend (from product analytics)
  Billing: payment health, failed payments, plan changes, seat utilization (from billing)
  Engagement: support tickets, CSM touchpoints, NPS/CSAT, sponsor activity (from CRM)]

run_cadence: "[e.g. every Monday 8:00 AM]"
renewal_lookahead_window: "[e.g. 90 days]"

signal_weights: |
  [Per-signal weights and the usage comparison window, as the user described,
  or the balanced default below if they didn't specify:
  Usage trend 25, feature adoption 15, seat utilization 15, payment health 15,
  support tickets/severity 15, NPS/CSAT 10, sponsor engagement 5.
  Usage comparison window: trailing 30 days vs prior 30 days.]

risk_thresholds: |
  watch: [score at which Watch begins, default 40]
  at_risk: [score at which At-risk begins, default 65]
  (0-100 scale, higher = more at risk)

expansion_rules: |
  [The user's expansion triggers, or these defaults:
  - Seat utilization >= 90% of seats paid for
  - Usage up >= 50% versus prior period
  - High-tier feature newly adopted
  - A new team/department active in the last period]

play_library: |
  [The user's plays, keyed by situation, e.g.:
  - At-risk, low/declining usage -> executive business review
  - At-risk, billing/payment issue -> billing + owner outreach
  - Watch, dropping engagement -> CSM check-in
  - Expansion, high seat utilization -> upsell conversation
  - No match -> owner review task
  If the user didn't provide a library, use the above as a starting set.]

owner_routing: |
  [How to find the owner for an account (e.g. CRM Account Owner field).
  Fallback owner if none set: [fallback handle/name].
  Accounts to exclude: closed-lost, churned, or [user-specified].]

digest_channel: "[Slack channel or DM]"
digest_cadence: "[e.g. weekly on Monday, matching the run]"
```

---

## Step 5: Connect accounts

After writing the config, guide the user to connect each required account through Gamut's account connection flow:

> "Now let's connect your accounts. I'll need access to:
> 1. **[crm_system]** - to read accounts, renewals, and owners, and to queue plays as tasks/records
> 2. **[billing_system]** - to read payment health, plan changes, and seat utilization
> 3. **[product_analytics_system]** - to read usage and adoption signals
> 4. **Slack** - to post your digest and alerts
>
> Connect each one via the Accounts panel in Gamut. Let me know when they're all connected and I'll run a quick read-only check."

Once accounts are connected, run a dry-run check:
- Read a sample of accounts with upcoming renewals from the CRM and confirm you can see renewal dates and owners.
- Pull billing data for one of those accounts and confirm it's readable.
- Pull usage data for one of those accounts and confirm it's readable.
- Confirm the Slack digest channel is reachable.

Report back what you found:

> "Connected and verified:
> - CRM: [N] accounts renewing within [renewal_lookahead_window], owners visible
> - Billing: readable (checked [sample account])
> - Product analytics: readable (checked [sample account])
> - Slack: [digest_channel] is reachable
>
> Everything looks good. You're set up."

---

## Step 6: First task and verification run

Close with a suggested first action:

> "Your agent runs [run_cadence]. To see exactly what it would do before it queues anything, try this prompt:
>
> *'Scan accounts renewing in my lookahead window but do NOT queue any plays and do NOT update any records. Show me what you'd do today: each account's score with its signal breakdown, which bucket it lands in, expansion candidates, and the play you'd queue for each owner.'*
>
> Once the plan looks right, run it again without the skip - that's your first live pass."

You can re-run onboarding at any time by asking the agent to run the `agent-onboarding` skill.
