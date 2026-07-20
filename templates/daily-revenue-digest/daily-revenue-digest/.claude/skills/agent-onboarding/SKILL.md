---
name: agent-onboarding
description: 'First-run setup for the Daily Revenue Digest. Connects the payment processor (Stripe or other) and POS/EPOS system, confirms locations and terminals, sets the report format and delivery destination, and schedules the daily job. Runs automatically when the agent is imported from a template.'
---

# Onboard the Daily Revenue Digest

You are helping a new user set up the **Daily Revenue Digest**. Be friendly and efficient. Ask a few questions at a time, offer sensible defaults, and explain *why* you need each thing in one line. **Confirm before any outward action** (connecting accounts, scheduling jobs, sending test messages).

Guiding principle: get one data source connected and generate yesterday's report. A working report with one source beats a perfectly configured one with none.

## 1. Welcome + business basics

In two sentences: this agent pulls yesterday's revenue from your payment systems each morning and delivers a clean summary — total taken, per-location breakdown, and comparison to recent averages. Then ask:
- Business name (for the report header).
- How many locations or sites? (Single location is fine — just needs to know.)
- What currency?

Write these into **Your context** in `CLAUDE.md`.

## 2. Connect the payment processor

Ask which payment processor(s) they use (Stripe, Square, SumUp, PayPal, or other). For each:
- **Stripe:** request the secret key (`sk_live_...`) or a restricted key with read-only access to charges/balance. Add to `.env` as `STRIPE_API_KEY`. If they have multiple Stripe accounts (e.g. one per location), ask for each and record as `STRIPE_API_KEY_1`, `STRIPE_API_KEY_2`, etc.
- **Other processors:** ask for the API key or export method. If it has no API, ask how they currently pull reports (CSV export, email report) and set up a workflow to ingest that.

Verify by fetching yesterday's transaction count. Show the number to confirm it looks right.

## 3. Connect the POS / EPOS system

Ask which till or EPOS system they use (Square POS, Lightspeed, Clover, Epos Now, iZettle, or other). For each:
- Walk them through finding the API key or access token in the system's developer/integration settings.
- Add the key to `.env` (e.g. `EPOS_API_KEY`).
- If the system doesn't have an API, ask whether it can email daily reports — if so, set up a Gmail connection to parse those.

Verify by pulling yesterday's sales total and showing it.

## 4. Locations and terminals

If the business has multiple sites:
- Ask for each location name (e.g. "City Centre", "East Side").
- Map each to the corresponding API credential or terminal ID.
- Record the mapping in `CLAUDE.md` → Your context.

## 5. Report delivery

Ask where the daily report should be delivered:
- Email (which address?)
- Slack (which channel?)
- Both?

Connect the relevant account (`request_connected_account`) and confirm before proceeding.

Ask for the preferred delivery time — default: **7:00 AM local**, covering the prior day (midnight–midnight).

## 6. Anomaly threshold

Confirm the threshold for flagging unusual days — default: **±15% vs. 30-day average**. Ask if they'd like a different threshold.

Write into `CLAUDE.md` → Your context.

## 7. Schedule and test

With their confirmation, create the recurring daily scheduled task.

Then offer a smoke test: generate and deliver yesterday's report right now so they can see exactly what they'll receive each morning.

## 8. Write everything back

All answers → **Your context** in `CLAUDE.md`. Credentials → `.env`. Do not overwrite general instructions.

## 9. Finish

Tell the user:
- Reports are also saved under `reports/` as dated markdown files for historical reference.
- They can re-run `agent-onboarding` anytime to add a new payment source, change the delivery destination, or adjust the schedule.
- On Mondays the report will automatically include a 7-day week-in-review.
