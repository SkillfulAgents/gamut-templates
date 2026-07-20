---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's set up your DTC/E-commerce Membership Retention & Win-back agent. I'll ask about your subscription program, connected systems, and how you want retention plays handled. About 8 minutes.

---

## Brand and subscription basics

1. What is your brand name, and what type of subscription or membership program do you run — a replenishment subscription, a curated box, a loyalty membership with perks, or another model?
2. How many active subscribers or members do you currently have?
3. What is your typical subscription billing cadence — monthly, every 6 weeks, quarterly?

---

## Connected systems

4. What platform powers your store and subscriptions — Shopify with Recharge, Shopify with a native subscription app, or another combination? Is it connected to Gamut?
5. Do you track customer data and marketing in a CRM or ESP (e.g., Klaviyo, Attentive, HubSpot)? If so, which one?

---

## Risk thresholds

6. How many days of inactivity (no purchase, no login) should trigger an at-risk flag? (Default: 45 days for monthly subscribers.)
7. After a customer cancels, how many days do you consider the "win-back window" still open? (Default: 60 days.)
8. How long ago does a lapsed customer's last purchase need to be before they enter the lapsed win-back flow? (Default: 6 months.)

---

## Retention plays

9. Do you have an existing pause offer you want the agent to present to at-risk subscribers? Describe the terms (e.g., "pause for up to 2 months at no charge").
10. What is your win-back offer strategy — a percentage discount, a free gift with purchase, a reduced price on first renewal, or something else?
11. Is there a maximum number of win-back attempts per customer in a 90-day window? (Default: 3 — one per play type.)

---

## Reporting and alerts

12. Which Slack channel should receive the weekly retention digest?
13. Who should be alerted if there is a spike in payment failures or mass cancellations that may indicate a platform issue?

---

## After Questions Are Answered

1. **Update CLAUDE.md** with: brand name, subscription type, member count, billing cadence, platform and connection status, CRM/ESP, inactivity threshold, win-back window, lapsed definition, pause offer terms, win-back offer, attempt cap, digest channel, and spike alert contact.

2. **Create config.json** at `.claude/skills/agent-onboarding/config.json`:

```json
{
  "brand_name": "",
  "subscription_type": "replenishment | curated_box | membership | other",
  "member_count": 0,
  "billing_cadence": "monthly | 6_week | quarterly | other",
  "platform": "shopify_recharge | shopify_native | other",
  "platform_connected": true,
  "crm_esp": "",
  "inactivity_threshold_days": 45,
  "winback_window_days": 60,
  "lapsed_threshold_months": 6,
  "pause_offer": "",
  "winback_offer": "",
  "max_winback_attempts_per_90_days": 3,
  "digest_channel": "",
  "spike_alert_contact": ""
}
```

3. **Give the user their first task prompt.** Suggest:

   > "Run today's retention check and show me all at-risk members."

   or

   > "Run the win-back sequence for everyone who canceled in the past 30 days."
