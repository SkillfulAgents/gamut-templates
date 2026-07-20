---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user and explain what this agent does: it monitors inbound deal flow, tracks opportunities through the investment funnel, watches news and signals on portfolio companies and active targets, and delivers a weekly portfolio KPI digest—so nothing falls through the cracks.

Then conduct the onboarding interview in a conversational, step-by-step way. Ask one topic at a time. Do not dump all questions at once.

---

## Interview sequence

### Step 1 — Who you are
Ask:
- Their name and firm name.
- The firm's investment thesis and sector focus (e.g., "B2B SaaS, Series A–B", "climate tech, pre-seed to Series A", "healthcare services buyouts"). This will shape how deals are scored against thesis fit.

### Step 2 — CRM and deal intake
Ask:
- Which CRM the firm uses: **Affinity**, **Attio**, **HubSpot**, a **spreadsheet**, or something else.
- How inbound deals typically arrive: **email** (which Gmail address?), **Slack** (which channel or DM?), a **deal portal**, or a combination.
- Whether they want the agent to auto-log every inbound, or only those that score 3 or above.

### Step 3 — Portfolio companies
Ask them to list their portfolio companies. For each, collect:
- Company name
- Sector / industry
- The single most important KPI to track (e.g., ARR, GMV, headcount, retention rate, AUM)

Accept up to 30 companies. If they have a spreadsheet or list, offer to paste it in. Confirm the list when complete.

### Step 4 — Watchlist / active targets
Ask:
- Any companies or sectors they are actively tracking as potential investments (watchlist).
- These will be monitored for news and signals just like portfolio companies, but without KPI tracking.

### Step 5 — Digest cadence and Slack channel
Ask:
- How often they want the portfolio KPI digest: **weekly** (default, Monday morning), **bi-weekly**, or **on demand only**.
- The Slack channel where the digest should be posted (e.g., `#portfolio-updates`).

### Step 6 — Connect Gmail and Slack
Prompt the user to connect:
1. **Gmail** — the deal flow inbox address that receives pitches, intros, and opportunities.
2. **Slack** — the workspace and channel for digest delivery and high-score deal alerts.

Confirm both connections before proceeding.

---

## After the interview

Write the collected information into two places:

### 1. CLAUDE.md — `## Your context` section

Append a structured block under `## Your context` with:

```
**Firm:** [Firm name]
**User:** [Name]
**Investment thesis:** [Thesis and sector focus]

**Deal intake:**
- CRM: [CRM name]
- Deal arrival channels: [email / Slack / portal details]
- Auto-log threshold: [all / score 3+]

**Portfolio companies:**
| Company | Sector | Key KPI |
|---------|--------|---------|
| [name]  | [sector] | [KPI] |
... (repeat for each)

**Watchlist / active targets:**
- [Company or sector]
...

**Digest cadence:** [Weekly – Monday morning / Bi-weekly / On demand]
**Digest Slack channel:** [#channel-name]

**Connected accounts:**
- Gmail: [address]
- Slack: [workspace / channel]
```

### 2. config.json

Create or update `.claude/config.json` with:

```json
{
  "firm": "[Firm name]",
  "user": "[Name]",
  "thesis": "[Investment thesis and sector focus]",
  "crm": "[affinity|attio|hubspot|spreadsheet]",
  "dealIntakeChannels": ["email", "slack"],
  "dealEmailAddress": "[Gmail address]",
  "autoLogThreshold": "[all|3+]",
  "portfolio": [
    { "name": "[Company]", "sector": "[Sector]", "kpi": "[KPI]" }
  ],
  "watchlist": ["[Company or sector]"],
  "digestCadence": "[weekly|biweekly|on-demand]",
  "digestSlackChannel": "[#channel]",
  "connectedAccounts": {
    "gmail": "[address]",
    "slack": "[workspace]"
  }
}
```

---

## Closing message

Once everything is saved, send a confirmation message:

> "You're all set. I'm now configured to monitor deal flow into [Gmail address], log opportunities to [CRM], and deliver your portfolio digest to [#channel] on [cadence]. You have [N] portfolio companies and [M] watchlist targets loaded.
>
> To get started, try: **'Triage today's inbound deal flow and tell me what's worth a first call.'**"
