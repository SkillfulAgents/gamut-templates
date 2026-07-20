---
name: agent-onboarding
---

# Agent Onboarding

Welcome to the Membership Retention & Win-back Agent for CPG and DTC subscription brands. This onboarding collects the configuration needed to personalize the agent for your brand, subscription platform, and retention plays. Ask the following questions in a single conversational message. Let the user know their answers will be saved to `config.json` and they can re-run this skill at any time to update the configuration.

---

## Questions to ask

Ask all of the following in one message:

1. **Brand and product category:** What is your brand name, and what is your primary product category? (e.g., supplements, food and beverage, beauty, personal care, or other - describe briefly)

2. **Subscription platform:** Which subscription platform do you use - Recharge, Skio, Bold Subscriptions, or another platform? If another, what is it?

3. **Email and SMS platform:** Which email and SMS platform do you use for subscriber communications - Klaviyo, Attentive, Postscript, or another? If another, what is it?

4. **Ecommerce platform:** Which ecommerce platform are you on - Shopify, Shopify Plus, or another? If another, what is it?

5. **Subscription plan types and AOV:** What subscription plan types do you offer (e.g., monthly replenishment, quarterly box, prepaid bundles, club membership)? What is your average order value (AOV) for subscribers?

6. **Churn signals you already watch:** What does "churn risk" look like for your subscribers today? Are there any specific signals your team already monitors or flags - failed payments, excessive skips, low engagement, support tickets, portal inactivity, or anything else?

7. **Retention plays you currently use:** What retention plays do you currently run when a subscriber is at risk? (e.g., pause offer, skip reminder, product swap, loyalty discount, personal outreach from a founder or customer success rep) Include any plays you'd like the agent to trigger automatically vs. ones that require human approval.

8. **Weekly report recipient:** Who should receive the weekly retention performance report? Provide a name, email address, or Slack handle.

---

## After collecting answers

1. Save all answers to `.claude/config.json` using the following structure:

```json
{
  "brand": "",
  "productCategory": "",
  "subscriptionPlatform": "",
  "emailSmsPlatform": "",
  "ecommercePlatform": "",
  "planTypes": [],
  "aov": null,
  "churnSignals": [],
  "retentionPlays": {
    "automatic": [],
    "requiresApproval": []
  },
  "reportRecipients": []
}
```

2. Update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-text summary of the configuration. Write it as a bulleted list covering: brand name and product category, subscription and ecommerce platforms, email/SMS platform, plan types and AOV, churn signals the team already monitors, retention plays configured (automatic vs. approval-gated), and report recipients.

3. Confirm to the user that setup is complete and suggest this opening prompt to start the agent: "Run the daily churn risk scan and show me any High Risk or Medium Risk subscribers flagged today."
