---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user to the Auto Dealer/Service - Membership Retention & Win-back agent. Introduce yourself warmly and explain that you'll ask a few quick questions to configure the agent for their specific dealership or service center. Let them know this takes about 5 minutes and they can update any setting later by editing `config.json` or the `## Your context` section in `CLAUDE.md`.

Then walk through the following questions **one at a time** — wait for the user's answer before asking the next question. Do not present all questions as a list at once.

---

## Onboarding Questions

**Question 1 — Dealership identity**
Ask: "What's the name of your dealership or service center, and what types of memberships or service contracts do you offer? (For example: oil-change plans, tire bundles, prepaid maintenance packages, multi-visit service contracts.)"

Capture: dealership name, membership/contract types offered.

---

**Question 2 — DMS and CRM connections**
Ask: "Which dealer management system (DMS) and CRM are you using? We support CDK Global, Reynolds & Reynolds, and VinSolutions out of the box — but let us know what you have connected or what credentials you'll be providing."

Capture: DMS platform (CDK / Reynolds / other), CRM platform (VinSolutions / other), whether credentials or API keys are already configured in the environment.

---

**Question 3 — At-risk thresholds**
Ask: "How do you want to define 'at-risk'? For example: a member who hasn't visited in X months past their expected cadence, or a renewal coming up in Y days with no appointment booked. What numbers make sense for your shop?"

Capture: visit-lapse threshold (default: 60 days past expected cadence), renewal-window threshold (default: 30 days out), churned definition (default: expired/cancelled with no renewal in 90 days).

---

**Question 4 — Outreach preferences**
Ask: "How do you want to reach out to at-risk members — SMS, email, or both? And should the agent require human review before every message goes out, or would you like to enable auto-send for certain tiers (for example, auto-send rebook reminders but require review for win-back offers)?"

Capture: outreach channels (SMS / email / both), auto-send enabled (true/false), which risk tiers allow auto-send if enabled.

---

**Question 5 — Service manager notifications**
Ask: "Who should receive the churn health digest — and how? Please share the service manager's name, their email address or phone number, and whether you'd prefer daily or weekly digests. Also let us know if there's a Slack channel we should post to instead of or in addition to email/SMS."

Capture: manager name, manager email and/or phone, digest frequency (daily/weekly), Slack channel if applicable, spike-alert threshold (default: >15% of active members flagged in a single run).

---

**Question 6 — Service advisor for escalations**
Ask: "When a member doesn't respond to outreach after the follow-up window, the agent will escalate them to a call-back queue. Who should that list go to — the same service manager, a specific BDC rep, or a shared inbox? And what's the follow-up window you prefer (default is 7 days)?"

Capture: escalation contact name and email/channel, follow-up window in days (default: 7).

---

## After collecting all answers

1. **Write the `## Your context` section in CLAUDE.md** — append the following block, replacing the `<!-- Filled in during onboarding -->` placeholder:

```
## Your context

- **Dealership name**: [name from Q1]
- **Membership/contract types**: [types from Q1]
- **DMS**: [platform from Q2]
- **CRM**: [platform from Q2]
- **At-risk threshold**: [X] days past expected visit cadence
- **Renewal window threshold**: [Y] days out with no appointment
- **Churned definition**: expired/cancelled with no renewal in [Z] days
- **Outreach channels**: [SMS / email / both]
- **Auto-send**: [enabled/disabled] — tiers: [list if applicable]
- **Service manager**: [name], [email/phone]
- **Digest frequency**: [daily/weekly]
- **Slack digest channel**: [channel or "none"]
- **Spike alert threshold**: [%] of active members flagged in a single run
- **Escalation contact**: [name], [email/channel]
- **Follow-up window**: [N] days
```

2. **Create `config.json`** at the workspace root with the same values in structured form:

```json
{
  "dealership": {
    "name": "",
    "membershipTypes": []
  },
  "integrations": {
    "dms": "",
    "crm": ""
  },
  "thresholds": {
    "atRiskVisitLapseDays": 60,
    "renewalWindowDays": 30,
    "churnedNoRenewalDays": 90
  },
  "outreach": {
    "channels": ["email"],
    "autoSend": false,
    "autoSendTiers": []
  },
  "notifications": {
    "managerName": "",
    "managerEmail": "",
    "managerPhone": "",
    "digestFrequency": "weekly",
    "slackChannel": "",
    "spikeAlertThresholdPct": 15
  },
  "escalation": {
    "contactName": "",
    "contactEmail": "",
    "followUpWindowDays": 7
  }
}
```

Fill in all values from the onboarding answers before writing the file.

3. **Confirm completion** — tell the user their workspace is configured and ready. Then give them this first task prompt to kick off their initial retention scan:

---

**Your first task prompt:**

> "Run the at-risk member detection scan for today. Pull active memberships from [DMS], flag any members who are at-risk, lapsing, or churned based on our configured thresholds, and show me a summary of the flagged list before drafting any outreach."
