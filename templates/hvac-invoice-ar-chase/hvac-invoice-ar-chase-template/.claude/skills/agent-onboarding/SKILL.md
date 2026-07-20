---
name: agent-onboarding
---

# Agent onboarding

Welcome — I am your Invoice & AR Chase agent for your trade contracting business. Before I start monitoring your open invoices and drafting payment reminders, I need to learn a few things about your business, your field service platform, and how you want to handle collections. This will take about five minutes.

---

## Section 1: Business basics

1. What is your business name, and what trade do you primarily work in — HVAC, plumbing, electrical, or a combination?
2. What city and timezone are you in?
3. Do you serve residential customers, commercial customers, or both?

---

## Section 2: Field service platform

4. Do you use ServiceTitan, FieldEdge, or another platform to manage your jobs and invoicing?
5. Is your platform connected to Gamut yet? If not, can you export an open AR report (CSV or Excel) so I can work from that until the integration is active?

---

## Section 3: AR thresholds and tone

6. At what point past the due date should I send the first payment reminder — after 7 days, 14 days, or 30 days past due?
7. How would you describe the voice you want for reminders — professional and polite, firm and direct, or something in between?
8. Do you want a different tone for residential customers vs. commercial accounts, or the same voice for both?

---

## Section 4: Escalation rules

9. At what aging tier should I stop drafting reminders and escalate directly to you — 60 days past due, 90 days, or another threshold?
10. For accounts that reach your escalation threshold without paying, what action should I recommend: refer to a collection agency, send a lien notice, or simply flag for your review?
11. Are there any customer accounts I should never send automated outreach to — for example, customers on service contracts, active commercial relationships, or anyone you are handling personally?

---

## Section 5: Approval flow

12. Who reviews and approves the draft messages before I send them — you, or your office manager? (Please give me their name.)
13. Where should I deliver the approval queue and the weekly AR digest — email, Slack, or both? (If email, what address? If Slack, what channel?)

---

## After questions are answered

Once the owner or office manager has answered all questions above, do the following:

1. **Write configuration to CLAUDE.md.** Under the `## Your context` section, record all answers in a clean, readable format covering: business name and trade, location and timezone, customer mix, field service platform and integration status, reminder threshold, voice preference (residential and commercial), escalation threshold and escalation action, excluded accounts, approver name, and delivery channel for the approval queue and digest.

2. **Create `config.json`** in the workspace root with the same configuration in structured JSON — keys should be snake_cased and match the categories above (e.g., `business_name`, `trade`, `timezone`, `platform`, `reminder_threshold_days`, `residential_voice`, `commercial_voice`, `escalation_threshold_days`, `escalation_action`, `excluded_accounts`, `approver_name`, `delivery_channel`).

3. **Give the user their first example task prompt** — something like:

   > "Pull today's open invoices from [platform] and show me everything past [threshold] days. Classify by aging tier and draft reminders for any accounts that have crossed my first reminder threshold."

   Tailor the prompt to the platform and threshold they just provided so they can copy and paste it immediately.
