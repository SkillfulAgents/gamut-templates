> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/customer-success-support/churn-renewal-risk-radar)** — one-click deploy, no setup.

# Churn / Renewal Risk Radar

> Pulls usage, billing, and engagement signals to score renewal risk per account, surfaces expansion signals, and queues a recommended play for the account owner.

## What it does

Churn / Renewal Risk Radar runs on a schedule ahead of your renewals, pulls usage, billing, and engagement signals for every account coming up for renewal, and computes an explainable risk score for each one. It buckets accounts into Healthy, Watch, and At-risk, flags expansion candidates on the way up, and queues the next best play for the right owner with a clear rationale and a due date that gives them lead time. You get a digest so you can see the whole book of business at a glance.

It recommends and queues plays for a human owner. It does not auto-send any outreach to customers, and every score shows the signals that produced it, so nothing is a black box.

Works for any SaaS or subscription business managing renewals: customer success, account management, and revenue teams. A consumer skin works for reorder and retention motions on a subscription base.

## What you'll need

- **Accounts:**
  - CRM / Customer Success platform: Salesforce, HubSpot, Gainsight, or similar
  - Billing: Stripe, Chargebee, or similar
  - Product analytics: Amplitude, Mixpanel, or a data warehouse
  - Slack (for the digest and alerts)
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** your renewal lookahead window, how you weight signals, your risk thresholds, and your library of plays (the standard outreach/actions your team runs for each situation)

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - Which CRM/CS platform, billing system, and product analytics source to read, and which Slack channel gets the digest
   - How far ahead of renewals to look, and how often to run
   - Which signals to use and how to weight them
   - Your risk thresholds (where Watch and At-risk begin)
   - Your expansion signal rules
   - Your library of recommended plays and how to route them to owners
3. Once setup finishes, give the agent its first task: *"Scan accounts renewing in my lookahead window but do NOT queue any plays and do NOT update any records. Show me what you'd do today: each account's score with its signal breakdown, which bucket it lands in, expansion candidates, and the play you'd queue for each owner."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` - the agent's instructions and your configuration (written by onboarding).
- `.claude/skills/agent-onboarding/` - first-run setup interview.

## Notes

- The agent recommends and queues plays for a human owner. It never auto-sends outreach to customers and never executes a play on its own.
- Every risk score is explainable. The agent always shows the contributing signals, their values, the direction each pushed the score, and its weight, so you never see a bare number.
- Missing signals are reported as missing, not treated as zero. The agent lowers its confidence and notes which source was unreachable rather than inventing a value.
- Slack is recommended but optional; if not connected, the digest will surface in your CRM/CS platform instead.
- An account can be both at-risk and an expansion candidate at the same time; the agent surfaces both rather than letting one hide the other.
- Play due dates are back-calculated from the renewal date so owners get lead time instead of a same-day scramble.

Relevant subsegments: RVTK, MTTK, CSTK, CYBR, DEVT, DATA, AICO, FNTK, INSR, HRTK, LGTK, PPTK, SCTK, ECTK, SAAS, EDTK, CLTK, HLTK, ASSN, FITN, MULT, DTC
