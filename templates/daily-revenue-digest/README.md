> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/finance-accounting/daily-revenue-digest)** — one-click deploy, no setup.

# Daily Revenue Digest

Connects to your payment processor (Stripe, Square, etc.) and POS/EPOS till system to deliver a consolidated income summary every morning — total taken, per-location breakdown, and comparison to recent averages. No manual report pulling required.

## What it delivers each morning

- **Total revenue** across all connected sources
- **Per-location / per-terminal breakdown** (if you have multiple sites)
- **Transaction count and average transaction value**
- **Comparison** to prior day, same day last week, and 30-day average
- **Anomaly flags** — anything more than 15% above or below the norm
- **Monday:** weekly digest with 7-day total and week-over-week comparison

## Setup

Import this workspace into Gamut, launch the agent, and follow the onboarding conversation. You'll be asked about:

1. Your payment processor(s) — Stripe, Square, SumUp, or other (API key needed)
2. Your POS/EPOS system — Epos Now, Lightspeed, Clover, or other
3. Your locations or terminals (if multiple)
4. Where to deliver the report — email, Slack, or both
5. What time to deliver (default: 7:00 AM)

A smoke test at the end of onboarding shows you exactly what the daily report looks like before the first scheduled run.

## Outputs

| Destination | Contents |
|-------------|----------|
| Email / Slack | Daily income summary (delivered each morning) |
| `reports/YYYY-MM-DD.md` | Saved copy of each day's report for historical reference |

## Customization

Edit `CLAUDE.md` → **Your context** to add new payment sources, change locations, or adjust the anomaly threshold. Or re-run the `agent-onboarding` skill from the agent's chat.
