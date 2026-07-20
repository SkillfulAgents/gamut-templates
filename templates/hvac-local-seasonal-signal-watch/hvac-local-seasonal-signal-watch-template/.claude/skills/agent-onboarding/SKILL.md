---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's get your Local / Seasonal Signal Watch configured for your business. I'll ask you a few quick questions so the agent knows your service area, which signals to watch, where your data lives, and how to deliver your weekly outreach list. This takes about 5 minutes.

---

## Business basics

1. What is your business name, and which trade(s) do you work in — HVAC, plumbing, electrical, or a combination?
2. What ZIP codes or counties make up your primary service area?
3. What is your primary outreach channel — phone calls, email, postcards, SMS, or a combination?

---

## Signal preferences

4. Which signal types do you want to watch — weather events, permit filings, new-mover data, or all three?
5. For weather signals: what temperature thresholds matter for your market? (For example: AC outreach after 3+ consecutive days over 90°F, furnace outreach after the first night below 32°F — or give me your local numbers.)
6. For permit signals: which permit types are most relevant to your trade — new construction, major renovations, or homeowner-filed trade permits (or all of these)?

---

## Data sources

7. Are you currently using a new-mover data provider (e.g., ListSource, USPS NCOALink, a data broker), or is that something to explore?
8. Do you have access to your county's permit search portal? (Many are public and searchable via browser — just share the URL if you have it.)
9. Are your maintenance-agreement customers tracked in ServiceTitan, FieldEdge, or a spreadsheet?

---

## Outreach list delivery

10. Who should receive the weekly outreach list — you, a CSR, or both? (Include names/emails as relevant.)
11. What day should it arrive? (Default: Monday morning.)
12. How should it be delivered — email, Slack, or in-chat?
13. Do you want pre-drafted outreach templates for each signal segment, or just the prioritized list?

---

## After questions are answered

Once the user has answered all questions above:

1. **Write configuration to CLAUDE.md** — append the answers as structured content under the `## Your context` section at the bottom of `CLAUDE.md`. Include: business name, trade(s), service area ZIP codes/counties, outreach channel, active signal types, temperature thresholds, relevant permit types, new-mover source status, permit portal URL (if provided), field service platform, weekly delivery recipient(s), delivery day, delivery channel, and template preference.

2. **Create config.json** in the workspace root with the same configuration in machine-readable form. Use keys: `businessName`, `trade`, `serviceArea` (array of ZIP codes or county names), `outreachChannels` (array), `signals` (object with keys `weather`, `permits`, `newMover` each true/false), `weatherThresholds` (object with `heatTriggerDaysAbove`, `heatTempF`, `freezeTempF`), `permitTypes` (array), `newMoverSource`, `permitPortalUrl`, `fieldServicePlatform`, `weeklyDelivery` (object with `recipients`, `dayOfWeek`, `channel`), `draftTemplates` (boolean).

3. **Give the user their first example task prompt:**

> "Run this week's signal check for [their service area]. Pull any active weather alerts, check for new permit filings in [their county], and compile Monday's outreach list with draft messages for each segment."
