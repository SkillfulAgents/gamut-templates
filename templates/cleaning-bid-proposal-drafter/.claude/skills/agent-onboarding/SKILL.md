---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user to the Cleaning/Janitorial - Bid / Proposal Drafter. Explain that you are going to ask a few quick questions to configure the agent for their specific business, and that it will only take a couple of minutes. After onboarding, the agent will be ready to draft proposals from their past work and pricing data.

## Configure the agent for this business

## Steps

Ask the owner the following questions (you may ask them all at once in a single message):

1. **Business name** — What is your cleaning company's name?
2. **Service types offered** — What services do you provide? (e.g., commercial janitorial, floor care, carpet cleaning, window washing, post-construction, medical/healthcare cleaning)
3. **Past proposal storage** — Where are your past proposals stored? (Google Drive folder path or URL, Dropbox folder, or local directory)
4. **Pricing model** — How do you price your work? (hourly rate, per-square-foot rate, flat project fee, or a combination)
5. **Bid pipeline alerts** — What Slack channel or email address should receive bid pipeline alerts and the weekly win-rate digest?
6. **Follow-up reminder timing** — How many days after submitting a proposal should the agent remind you to follow up? (e.g., 5 days)

## After collecting answers

1. Write a `config.json` file at `.claude/skills/agent-onboarding/config.json` with the following structure:

```json
{
  "businessName": "<answer>",
  "serviceTypes": ["<answer>", "..."],
  "proposalStorageLocation": "<answer>",
  "pricingModel": "<answer>",
  "alertChannel": "<answer>",
  "followUpReminderDays": <number>
}
```

2. Update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-English summary of the configuration, for example:

```
## Your context

**Business:** [Business Name]
**Services:** [list]
**Proposal library:** [location]
**Pricing model:** [model]
**Alerts:** [channel/email]
**Follow-up reminder:** [N] days after submission
```

3. Confirm setup is complete, then give the owner their first task prompt:

> "Draft a proposal for a 20,000 sq ft office cleaning contract, 3x per week, with a bid due in 5 days."
