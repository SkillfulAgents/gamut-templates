# Skill: agent-onboarding

Run this skill automatically the first time the agent is used, or whenever the user says "run onboarding," "set up," or "configure."

---

## Onboarding flow

Work through the following steps in order. Be conversational — this is a setup interview, not a form. Confirm each answer before moving to the next step.

---

### Step 1 — Welcome

Introduce what this agent does:

> "Welcome to your VC Portfolio Monitor. This agent will automatically sweep your entire portfolio each week — checking news, blogs, social media, and founder activity — and deliver a structured digest straight to your inbox. You'll always know what's happening across every company without having to manually check in on each one.
>
> Let's get you set up. I'll need a few things: your portfolio companies, your signal preferences, and where to send the digest. It should take about 5 minutes."

---

### Step 2 — Portfolio entry

Ask the user to add their portfolio companies. Offer two options:

> "First, let's build your portfolio list. You have two options:
>
> **Option A** — I'll ask you about each company one at a time. For each one I need: company name, website URL, founder names, investment date, stage (pre-seed, seed, Series A, etc.), and sector (SaaS, fintech, healthcare, etc.).
>
> **Option B** — Paste a CSV, spreadsheet table, or list and I'll parse it. The columns should be: name, website, founders, investment_date, stage, sector. Extra columns are fine — I'll ignore them.
>
> Which do you prefer?"

- If Option A: walk through each company interactively. After each entry, confirm: "Got it — [Company Name] ([website]), [stage], [sector], founded by [founders], invested [date]. Does that look right?"
- If Option B: accept the pasted data, parse it, and display a clean summary table for confirmation before writing.

Once confirmed, write all entries to `/workspace/portfolio.json` in the following format:

```json
[
  {
    "name": "Acme Inc",
    "website": "https://acme.com",
    "founders": ["Jane Doe", "John Smith"],
    "investment_date": "2023-08-15",
    "stage": "Seed",
    "sector": "SaaS"
  }
]
```

Confirm how many companies were saved: "Portfolio saved — [N] companies."

---

### Step 3 — Signal preferences

Ask the user which signal categories matter most to them:

> "Next, signal preferences. By default I track all five signal types:
> - 🚀 Milestones (funding, launches, customer wins)
> - 👥 Team changes (hires, departures)
> - 📰 Press coverage
> - ⚠️ Risk signals (layoffs, pivots, negative press, long silence)
> - 💡 Opportunities (co-investor openings, competitive dynamics)
>
> Do you want all of these, or are some more important to you than others? For example, some investors always want Risk and Milestone flagged first; others care most about Team changes."

Accept free-form input and translate it into a prioritized list. Default if they say "all" or skip: `["risk", "milestone", "opportunity", "team", "press"]` (risk and milestone first).

---

### Step 4 — Silence threshold

Ask:

> "How many days of no web or social activity should I treat as a 'Dark' signal — meaning I flag the company as gone quiet and recommend you reach out? The default is 30 days."

Accept their answer (integer, days). Default: 30.

---

### Step 5 — Digest recipients

Ask:

> "Who should receive the weekly digest? Give me one or more email addresses. You can list yourself and any co-investors or associates who should be in the loop."

Accept a comma-separated list of email addresses. Confirm the list back to the user.

---

### Step 6 — Schedule

Ask:

> "When should I send the digest? The default is every Friday at 5 PM — a good end-of-week cadence. Would you like to keep that, or change the day and time?"

Accept their answer. Convert to a cron expression. Common cases:
- Friday 5 PM → `0 17 * * 5`
- Monday 8 AM → `0 8 * * 1`
- Sunday 9 AM → `0 9 * * 0`

Also confirm timezone: "What timezone should I use for the schedule? (e.g. America/New_York, America/Los_Angeles, Europe/London)"

---

### Step 7 — Write config.json

Write `/workspace/config.json` with all collected values:

```json
{
  "portfolio_path": "/workspace/portfolio.json",
  "signal_priorities": ["risk", "milestone", "opportunity", "team", "press"],
  "silence_threshold_days": 30,
  "recipient_emails": ["partner@fund.com"],
  "schedule": "0 17 * * 5",
  "timezone": "America/New_York"
}
```

Confirm: "Configuration saved."

---

### Step 8 — Connect Gmail

> "Now let's connect your Gmail account so I can send the weekly digest. I'll walk you through the authorization — it only takes a moment."

Initiate Gmail OAuth connection. Confirm when connected.

---

### Step 9 — Smoke test

> "Before we wrap up, let's do a quick smoke test. Pick one company from your portfolio and I'll run a full sweep on it right now — I'll show you exactly what signals I find and what your digest will look like for that company."

Ask the user to name a company or pick one at random if they prefer. Run the full sweep (web search for news, site search, founder social) and display:
- All signals found, categorized by type
- Which digest section it would appear in (Needs Attention, Milestones, Quiet, or Dark)
- A preview of that company's entry in the digest

End with: "That's what your weekly digest will look like across all [N] companies. You're all set — I'll send the first full digest this [day] at [time] [timezone]. You can also run a digest anytime by saying 'run portfolio sweep'."
