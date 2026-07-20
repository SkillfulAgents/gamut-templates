# VC Market Scout

A weekly agent that sweeps funding news, sector moves, and competitor fund activity, then delivers a clean digest to your inbox every Monday morning.

## What it does

Every Monday at 7 AM, the agent:

1. Pulls your configured sectors, thesis keywords, and competitor funds from `config.json`
2. Searches for funding activity across your sectors from the past 7 days
3. Checks what your competitor funds have been investing in
4. Surfaces macro signals: exits, IPOs, regulatory news, key talent moves
5. Curates the 10–15 most relevant items and drops the noise
6. Writes a structured digest and emails it to your configured recipients
7. Archives the digest to `/workspace/market-scout/[date]-digest.md`

## Who it's for

VC analysts and partners who want Monday-morning awareness of what moved in their space — without spending an hour reading TechCrunch, Crunchbase, and fund newsletters. Useful for competitive tracking, thesis validation, and staying ahead of portfolio-adjacent moves.

## Digest structure

Each weekly email follows this format:

- **Header** — "Market Scout — Week of [date]" with a 3-sentence summary of the top signal
- **Section 1: Funding Activity** — companies that raised in your sectors: amount, stage, lead investor, one-sentence description
- **Section 2: Competitor Fund Moves** — what competing funds invested in, with any pattern noted
- **Section 3: Sector Signals** — macro news, regulatory developments, notable exits, key talent moves
- **Section 4: Thesis Implications** — 1–3 analytical bullets connecting the week's signals to your fund's thesis
- **Footer** — full source list with URLs

## Setup

Import this workspace and the `agent-onboarding` skill runs automatically. It will ask you:

- What sectors your fund invests in
- Your thesis keywords
- Which competitor funds to monitor
- Companies to always include in the sweep
- Who receives the digest
- Your timezone (default schedule: Monday 7 AM)
- Any topics to always exclude

Once configured, the agent runs on its own schedule.

## Adjusting sectors and competitor funds after setup

Edit `/workspace/market-scout/config.json` directly. The relevant fields:

**Add a sector:**
```json
"sectors": ["B2B SaaS", "climate tech", "your new sector"]
```

**Remove a competitor fund:**
```json
"competitor_funds": ["a16z", "Sequoia"]
```

**Add a company to always track:**
```json
"tracked_companies": ["Stripe", "Anduril", "your company"]
```

**Change the schedule:**
```json
"schedule": {
  "cron": "0 7 * * 1",
  "timezone": "America/New_York",
  "description": "Every Monday at 7 AM ET"
}
```

Changes take effect on the next scheduled run. No need to re-run onboarding.

## Adding recipients

Update `recipient_emails` in `config.json`:

```json
"recipient_emails": ["analyst@fund.com", "partner@fund.com"]
```

## Digest archive

All digests are saved to `/workspace/market-scout/` as markdown files named by date (e.g. `2026-06-15-digest.md`). You can search past digests to track how sectors or competitor activity has shifted over time.
