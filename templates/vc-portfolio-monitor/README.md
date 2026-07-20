> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/vc-investing/vc-portfolio-monitor)** — one-click deploy, no setup.

# VC Portfolio Monitor

A weekly agent that sweeps your entire portfolio for news, product launches, key hires, funding milestones, press mentions, and risk signals — then delivers a structured digest so you always know what's happening across every company without manually checking each one.

---

## What it does

Each week (default: Friday at 5 PM), the agent:

1. Reads your portfolio from `portfolio.json`
2. Sweeps each company across at least 3 sources: news search, company website/blog, and founder social media
3. Categorizes every finding into one of five signal types
4. Builds a four-section digest — Needs Attention, Milestones, Quiet, Dark
5. Emails the digest to your configured recipients
6. Saves the digest to disk and updates an activity log

You can also trigger a sweep manually at any time by saying "run portfolio sweep."

---

## Who it's for

- VC partners and associates who manage portfolios of 5–100+ companies
- Angel investors who want to stay informed without spending hours on manual research
- Fund analysts responsible for portfolio monitoring and LP reporting

---

## Signal categories

| Signal | Emoji | What it means |
|--------|-------|---------------|
| Milestone | 🚀 | Funding round closed, product launch, major customer win, strategic partnership, industry award |
| Team | 👥 | Key hire (VP-level or above), executive departure, leadership reorg |
| Press | 📰 | Media coverage — flagged as positive, neutral, or negative |
| Risk | ⚠️ | Layoffs, pivot, negative press, shutdown signals, long silence, large competitor raise |
| Opportunity | 💡 | Portfolio company is raising and may benefit from co-investor intros; competitor raise signals market heating up |

---

## How to read the digest

The digest has four sections:

**Needs Attention** — Companies requiring your active involvement this week. Each entry includes the signal type, a brief description of what was found, and a recommended action (e.g., "Schedule a call with founder"). Sorted by urgency: Risk signals appear before Opportunity signals.

**Milestones & Momentum** — Companies with positive signals this week. Good news to be aware of; may warrant a congratulatory note to the founder.

**Quiet** — Companies with no notable activity. Listed by name only. No action needed unless they've been quiet for a while (in which case they'll be in Dark instead).

**Dark** — Companies with no detectable web presence, news, or social activity at all this week. These are high-priority for personal outreach. The digest shows the last known activity date and recommends emailing the founder directly. A portfolio company that has gone completely quiet is one of the most important early risk signals.

---

## How to add companies after setup

Edit `/workspace/portfolio.json` directly. Each entry follows this format:

```json
{
  "name": "Acme Inc",
  "website": "https://acme.com",
  "founders": ["Jane Doe", "John Smith"],
  "investment_date": "2023-08-15",
  "stage": "Seed",
  "sector": "SaaS"
}
```

The agent picks up changes automatically on the next sweep. You can also tell the agent "add [Company Name] to my portfolio" and it will walk you through the entry interactively.

---

## Configuration

All settings live in `/workspace/config.json`:

| Field | Description | Default |
|-------|-------------|---------|
| `portfolio_path` | Path to portfolio.json | `/workspace/portfolio.json` |
| `signal_priorities` | Ordered list of signal types to prioritize | `["risk", "milestone", "opportunity", "team", "press"]` |
| `silence_threshold_days` | Days of no activity before flagging as Dark | `30` |
| `recipient_emails` | Email addresses to receive the digest | Set during onboarding |
| `schedule` | Cron expression for the weekly run | `0 17 * * 5` (Friday 5 PM) |
| `timezone` | Timezone for the schedule | Set during onboarding |

---

## Digest archive

Every digest is saved to `/workspace/portfolio-monitor/[YYYY-MM-DD]-digest.md`. The activity log at `/workspace/portfolio-monitor/activity-log.json` tracks the last known signal date for each company across runs — this is how the agent detects when a company has gone Dark.

---

## First-time setup

Say "run onboarding" to configure the agent. Onboarding takes about 5 minutes and covers:
- Adding your portfolio companies (one by one or via CSV paste)
- Setting signal preferences
- Configuring the silence threshold
- Setting digest recipients and delivery schedule
- Running a live smoke test on one company
