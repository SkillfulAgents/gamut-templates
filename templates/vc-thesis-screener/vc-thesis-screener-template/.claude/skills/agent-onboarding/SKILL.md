---
name: agent-onboarding
description: First-run setup for the VC Thesis Screener. Interviews the analyst or partner, writes fund thesis criteria and delivery settings to CLAUDE.md and config.json, connects Gmail, and schedules the nightly screening run.
---

# Agent Onboarding — VC Thesis Screener

Welcome! This agent screens inbound companies against your fund's investment thesis each evening and emails you a sorted fit/no-fit report. Setup takes about 5 minutes. I'll ask you a few questions, then configure everything automatically.

---

## Interview

Work through each group in order. Ask all questions in a group together, then confirm the answers before moving on.

---

### Group 1 — Fund basics

Ask:
1. What is your fund's name? (e.g., "Horizon Ventures", "Elm Street Capital")
2. What is your name and role? (e.g., "Sarah Chen, Partner" — this is used in the report header)

---

### Group 2 — Investment thesis

Ask:
1. What sectors or spaces do you invest in? List them specifically. Examples: "AI infrastructure, developer tools, vertical SaaS", "climate tech, energy storage", "fintech, insurtech, B2B payments". You can list as many as you like.
2. What stage range do you invest in? (e.g., Pre-Seed only; Pre-Seed to Series A; Seed to Series B). Name the stages explicitly.
3. What is your geography focus? (e.g., US only; North America; US + EU; global)
4. What is your typical check size range? Give a min and max (e.g., $500K–$2M; $1M–$5M).

---

### Group 3 — Must-haves

Ask:
List 1–3 things that **must** be true for a company to pass screening. These are positive requirements — if any one of them can't be confirmed, the company gets a NO-FIT. Examples:
- "AI must be core to the product, not a bolt-on feature"
- "Founder must be technical (CTO/engineer background)"
- "B2B only — must have a business customer, not consumers"
- "Must have at least one paying customer or a signed LOI"

(If they have fewer than 3 must-haves, that's fine. Accept whatever they provide.)

---

### Group 4 — Dealbreakers

Ask:
List 1–3 hard no's — things that immediately disqualify a company regardless of everything else. Examples:
- "No crypto / web3 / blockchain"
- "No consumer apps (B2C)"
- "No companies outside the US"
- "No biotech or life sciences"
- "No hardware"

(Same as must-haves — fewer than 3 is fine.)

---

### Group 5 — Inbox setup

Ask:
Where do inbound companies come from? The default is simple: you paste company names and descriptions directly into `/workspace/inbox.txt`, one per line. Each line looks like:

```
Company Name — one-sentence description
```

Do you want to use a different path for the inbox file, or is `/workspace/inbox.txt` fine?

(Note: email-based inbound parsing — e.g., forwarding a deal email to a monitored inbox — is an advanced enhancement not included in this base template. If they ask about it, note it's a future extension.)

---

### Group 6 — Delivery

Ask:
Which email address should the nightly report be sent to? This is where the HTML fit/no-fit digest will land each evening.

---

### Group 7 — Schedule

Ask:
What time each evening should the screening run? The default is **6:00 PM on weekdays (Monday–Friday)**. What timezone are you in?

Confirm the cron expression with them: `0 18 * * 1-5` is weekdays at 6 PM. Adjust the hour for their timezone (e.g., 6 PM Pacific = `0 18 * * 1-5` with timezone set to `America/Los_Angeles`).

If they want weekends included, use `0 18 * * *`.

---

## Write-back

After collecting all answers, do the following:

### 1. Write config.json

Create or overwrite `/workspace/config.json` with:

```json
{
  "fund_name": "<fund name>",
  "analyst_name": "<name and role>",
  "sectors": ["<sector 1>", "<sector 2>"],
  "stage_range": ["<stage min>", "<stage max>"],
  "geography": "<geography>",
  "check_size_min": "<e.g. $500K>",
  "check_size_max": "<e.g. $3M>",
  "must_haves": ["<must-have 1>", "<must-have 2>"],
  "dealbreakers": ["<dealbreaker 1>", "<dealbreaker 2>"],
  "inbox_path": "/workspace/inbox.txt",
  "verdicts_path": "/workspace/verdicts.json",
  "report_email": "<email address>",
  "schedule": "0 18 * * 1-5",
  "timezone": "<e.g. America/New_York>"
}
```

Use the exact values collected in the interview. For stage_range, record it as a two-element array [min_stage, max_stage]. If they gave a single stage, use it for both min and max.

### 2. Update CLAUDE.md

Append a populated summary block under `## Your context` in `/workspace/template-builds/vc-thesis-screener-template/CLAUDE.md` (or the project's CLAUDE.md if the path differs). The block should look like:

```
## Your context

**Fund:** [fund name]
**Analyst:** [name and role]
**Sectors:** [comma-separated list]
**Stage range:** [min] to [max]
**Geography:** [geography]
**Check size:** [min] – [max]
**Must-haves:** [bulleted list]
**Dealbreakers:** [bulleted list]
**Inbox path:** [path]
**Verdicts path:** [path]
**Report email:** [email]
**Schedule:** [cron] ([human-readable], [timezone])
```

Replace any existing content under `## Your context` rather than appending duplicate blocks.

### 3. Create the inbox file

If `/workspace/inbox.txt` (or the configured inbox path) does not exist, create it with the default header:

```
# VC Thesis Screener — inbox
# Add one company per line: "Company Name — one-sentence description"
# Lines starting with # are ignored. Inbox is cleared after each nightly run.
```

---

## Connect accounts

Walk through connecting Gmail for sending the nightly report:

> To send the nightly report, I need access to a Gmail account. I'll connect it now using the available account integration. This will only be used to send the thesis screen digest to [report_email].

Use `mcp__user-input__request_connected_account` with service `gmail` to connect the account. If the connection succeeds, confirm it and move on. If it fails or the user wants to skip, note that the email step will be skipped at runtime until a Gmail account is connected, but verdicts will still be saved to `verdicts.json`.

---

## Smoke test

Once config is written and accounts are connected, run a quick smoke test:

> Let's verify everything works. I'll add one test company to your inbox and run a single screening pass so you can see the verdict format and the email that would be sent.

Add this line to the inbox file:
```
Acme AI — builds AI-powered contract review software for legal teams at mid-market companies
```

Run one full screening pass (Steps 1–6 from the agent instructions, but do NOT clear the inbox after — leave the test entry so the user can see it). Show the user:
1. The verdict for Acme AI (FIT or NO-FIT, with reason)
2. A preview of the HTML report structure (or the actual rendered HTML)
3. Confirmation that the email would be sent to [report_email] (if Gmail is connected, send it; if not, show the subject line and a summary of the body)

After the smoke test, remove the Acme AI line from the inbox so it starts clean.

---

## Done

Summarize the configuration and how to use the agent going forward:

> Setup complete! Here's what's configured:
>
> - **Fund:** [fund name]
> - **Thesis:** [sectors], [stage range], [geography], [check size range]
> - **Must-haves:** [list]
> - **Dealbreakers:** [list]
> - **Nightly run:** [human-readable schedule and timezone]
> - **Report delivered to:** [report_email]
>
> **How to add companies:**
> Open `/workspace/inbox.txt` and add one company per line:
> ```
> Company Name — one-sentence description
> ```
> Each evening at [time], the agent will screen everything in the inbox, email you the report, and clear the file.
>
> To update your thesis criteria or delivery settings, re-run `/agent-onboarding` at any time.
