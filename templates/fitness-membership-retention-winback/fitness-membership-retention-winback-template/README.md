# Membership Retention & Win-back — Fitness, Wellness, Salon & Spa

Most studios find out a member has drifted away only after they cancel. This agent catches them weeks earlier — when their visit frequency starts slipping — and prepares the right retention message for the right moment, ready for your review before anything goes out.

## Who it is for

Fitness studios, wellness centers, salons, and spas running membership or subscription models who lose too many members to gradual drift rather than a single cancellation event. If your studio runs on Mindbody or Boulevard and you want to stop churn before it happens, this template is built for you.

Relevant subsegments: FITN

## What it does

1. Pulls visit frequency, last visit date, booking patterns, and billing status from Mindbody or Boulevard every day
2. Scores each member against their own usage baseline — not a studio average — and flags anyone whose visit rate has dropped 40% or more in the last 30 days
3. Detects billing failures (declined cards, failed autopay) and surfaces them to you the same day
4. Categorizes at-risk members into tiers: drifting, lapsed, churned pending, or churned complete
5. Drafts a targeted retention message for each tier in your brand voice — a rebooking nudge, a pause offer, a win-back, or a re-sign offer — using only the offers you have approved
6. Presents all drafted messages for your review and approval before anything is sent
7. Posts a weekly churn-risk digest with tier counts, revenue at risk, open actions, and win-back outcomes from the prior week

## Key integrations

- **Mindbody** — membership data, visit history, booking patterns, billing status
- **Boulevard** — membership data, appointment history, autopay and billing status
- **Email / Slack** — weekly digest delivery and owner approval workflow

## Getting started

1. **Import this workspace** into Gamut from the marketplace
2. **Run the agent-onboarding skill** — the agent will ask you a short set of questions about your business, your membership system, your at-risk thresholds, and your retention offer menu
3. **Send your first prompt** — try: "Show me all members currently flagged as at-risk and draft retention messages for the top five."

## Configuration

During onboarding, the agent captures and stores:
- Business name, type, city, and timezone
- Booking and membership platform (Mindbody or Boulevard) and connection status
- Membership and package types
- Visit frequency baseline and at-risk thresholds (drift %, lapse days)
- Brand voice description and approved retention offers
- Digest recipients and delivery channel

All configuration is written to the `## Your context` section of CLAUDE.md and to `config.json` so it persists across sessions.

---

Pattern: Vertical / NON-TECH — Fitness, wellness, salon & spa membership retention
