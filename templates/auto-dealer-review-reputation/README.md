> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/review-reputation/auto-dealer-review-reputation)** — one-click deploy, no setup.

# Auto Dealer/Service - Review & Reputation Replies

Most dealerships and service centers get reviews every day across Google, DealerRater, and Yelp — but without a dedicated marketing person, those reviews go unanswered for days or get generic copy-paste replies that signal no one is actually paying attention. This agent closes that gap: it monitors your review platforms around the clock, drafts on-brand responses tuned to your dealership's voice, flags 1-2 star reviews for immediate manager follow-up, and delivers a weekly rating trend digest so leadership can spot problems before they compound.

## Who this is for

This template is built for automotive dealerships and service centers that:

- Receive reviews across multiple platforms (Google, DealerRater, Yelp) and struggle to reply consistently
- Do not have a dedicated marketing or reputation management staff member
- Want 1-2 star reviews escalated immediately to the service manager — not discovered at end of week
- Need visibility into whether ratings are trending up or down, and why

Relevant subsegments: AUTO

## What it does

1. **Monitor and detect** — Checks Google Business Profile, DealerRater, and Yelp on a scheduled cadence for net-new reviews, parsing rating, reviewer name, text, platform, and any mentioned staff or department.
2. **Classify and triage** — Buckets reviews by star rating (positive / neutral / negative), identifies the department referenced (sales, service, parts, F&I), and tags recurring themes for trend tracking.
3. **Draft on-brand replies** — Writes a personalized, voice-consistent reply for every review, queued for service advisor or manager approval before anything is posted.
4. **Log outcomes** — Records every approved-and-posted reply with turnaround time, approver, and platform for accountability and coaching.
5. **Alert and weekly digest** — Sends real-time notifications for 1-2 star reviews and a Monday morning digest covering platform ratings, review volume, reply rate, and top positive/negative themes.

## Key integrations

- **CDK Global** — DMS integration for tying reviews to repair orders and customer records
- **Reynolds & Reynolds** — DMS/CRM integration for service history context and customer lookup
- **VinSolutions** — CRM integration for customer contact data and follow-up task creation

> Note: Review platform connections (Google Business Profile API, DealerRater partner API, Yelp Fusion API) are configured separately during onboarding. CDK, Reynolds, and VinSolutions connections are optional enhancements that enable deeper context in replies and automated follow-up task creation.

## Getting started

1. **Import this workspace** into your Gamut environment using the workspace import flow.
2. **Run the `agent-onboarding` skill** — type `/agent-onboarding` in the chat to start the guided setup. The skill will ask you about your dealership, platforms, voice preferences, and escalation contacts, then write your configuration automatically.
3. **Send your first task prompt** — once onboarding is complete, try: "Check for any new reviews posted in the last 24 hours, draft replies, and flag anything under 3 stars for manager review."

## Configuration

After onboarding, your settings are stored in `.claude/config.json` and the `## Your context` section of `CLAUDE.md`. You can edit either file directly to update escalation contacts, adjust the monitoring cadence, change tone guidelines, or add platform credentials. Re-run `/agent-onboarding` at any time to update your configuration interactively.

## Pattern

Vertical / NON-TECH — Auto dealer reputation management
