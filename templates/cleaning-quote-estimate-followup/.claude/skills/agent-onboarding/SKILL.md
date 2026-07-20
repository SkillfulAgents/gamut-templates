---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user warmly and explain that you are going to ask a few quick questions to set up their Quote / Estimate Follow-up agent. Let them know the whole process takes about 2 minutes and they can update any setting later by editing `config.json` or the `## Your context` section in `CLAUDE.md`.

Then walk through the following questions **one at a time** (do not ask them all at once). Wait for the user's answer before moving to the next question.

---

## Onboarding Questions

**Question 1 — Business basics**
Ask: "What's the name of your cleaning or janitorial business, and do you primarily serve residential clients, commercial clients, or a mix of both?"

Use the answer to set `business_name` and `client_mix` (residential / commercial / mixed) in config.

---

**Question 2 — Connected job management system**
Ask: "Which system do you use to send and track your quotes or estimates? For example, Swept, Janitorial Manager, another platform, or just email/spreadsheet?"

If they name Swept or Janitorial Manager, note the integration. If it's another tool, record it under `job_management_system` and note that they may need to connect it manually. If it's just email/spreadsheet, set `job_management_system: "manual"` and note that the agent will work from a shared sheet or inbox.

---

**Question 3 — Follow-up timing**
Ask: "How many business days after sending a quote should I send the first follow-up? And if there's still no response, how many more days before a second nudge? (Common defaults are 2 days for the first, then 5 more days for the second — feel free to use those or pick your own.)"

Record `first_followup_days` and `second_followup_days` in config.

---

**Question 4 — Sending preference and channel**
Ask: "When it's time to send a follow-up, would you like me to send it automatically, or would you prefer to review and approve each message first? And what channel should I use — email, SMS, or through your job management platform?"

Record `auto_send: true/false` and `followup_channel` (email / sms / in-platform) in config.

---

**Question 5 — Tone and voice**
Ask: "How would you describe the tone you use with your customers? For example: casual and friendly, professional and polished, or different depending on whether it's a homeowner vs. a business? Feel free to share a sentence or two in your own words — I'll match your style."

Record `tone_description` and `tone_by_client_type: true/false` in config.

---

**Question 6 — Weekly digest and alerts**
Ask: "Where should I send your weekly pipeline digest and expiry alerts? Options: email (give me the address), SMS (give me the number), or skip the digest for now."

Record `digest_channel` and `digest_recipient` in config. Set `digest_day: "Monday"` as default unless they specify otherwise.

---

## After Completing All Questions

Once you have answers to all six questions, do the following:

### 1. Write `config.json`

Create or overwrite `/workspace/config.json` with the collected settings. Use this structure:

```json
{
  "business_name": "",
  "client_mix": "mixed",
  "job_management_system": "",
  "first_followup_days": 2,
  "second_followup_days": 5,
  "max_followup_attempts": 2,
  "auto_send": false,
  "followup_channel": "email",
  "tone_description": "",
  "tone_by_client_type": false,
  "expiry_warning_days": 3,
  "daily_send_cap": 10,
  "digest_channel": "email",
  "digest_recipient": "",
  "digest_day": "Monday"
}
```

Fill in all fields from the user's answers. Leave defaults where the user did not specify.

### 2. Write `## Your context` in CLAUDE.md

Append a filled-in `## Your context` section to the bottom of `/workspace/CLAUDE.md`, replacing the `<!-- Filled in during onboarding -->` placeholder. Write it as a short, plain-English summary of the business and configuration — 4–8 bullet points covering: business name and client mix, connected system, follow-up timing, send preference and channel, tone guidance, and digest settings.

### 3. Confirm and give the first task prompt

Tell the user that setup is complete and their agent is ready to use. Then give them this first task prompt to try:

> "Check my open quotes and show me what follow-ups are due today."

Let them know they can also ask things like:
- "Show me all quotes expiring this week."
- "Draft follow-ups for any quotes I haven't touched in 3 days."
- "Give me my pipeline summary for the last 30 days."
