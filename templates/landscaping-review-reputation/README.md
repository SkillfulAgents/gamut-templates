> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/review-reputation/landscaping-review-reputation)** — one-click deploy, no setup.

# Landscaping/Lawn - Review & Reputation Replies

Landscaping and lawn care businesses live and die by their online reputation, but most owner-operators have no process for monitoring reviews or responding consistently — negative reviews sit unanswered for days while competitors look more responsive. This agent monitors reviews across Google, Yelp, Facebook, and other platforms, drafts on-brand owner-voiced replies matched to the job details from Jobber or Aspire, and routes service failures to the manager before a bad review compounds into a pattern.

Relevant subsegments: LAND

## Who this is for

Owner-operators and operations managers running landscaping, lawn care, or lawn maintenance businesses — residential, commercial, or HOA-focused — who want every review answered promptly, service failures escalated before they escalate publicly, and a weekly view of their rating trends without manually checking every platform.

Best fit for businesses with 50+ active customers generating 5–30 new reviews per month across two or more platforms.

## What it does

1. **Monitor & ingest new reviews** — pulls new reviews from Google Business Profile, Yelp, Facebook, and other connected platforms; cross-references reviewer names against recent Jobber or Aspire job records to surface job details for context
2. **Triage by urgency** — categorizes reviews by sentiment tier (positive, mild concern, mixed, service failure) and flags any 1–2 star review or mention of a crew or safety issue for manager review before a reply is posted
3. **Draft on-brand replies** — writes all replies in the owner's voice, personalized to the reviewer's name and specific service mentioned, with escalating specificity from appreciative (5-star) to accountable and action-oriented (1–2 star)
4. **Route service failures to manager** — sends an immediate alert (email, Slack, or SMS) with the full review, matched job details from Jobber or Aspire, and a draft reply awaiting approval; follows up if approval isn't received within the SLA window
5. **Post approved replies** — posts replies to review platforms once approved; logs every reply with timestamp and platform; outputs copy-paste text with direct review links for platforms without API access
6. **Weekly rating trend digest** — delivers a Monday summary of new reviews by platform, average rating vs. prior 4-week average, service failures flagged, and any review where response time exceeded 48 hours

## Key integrations

- **Google Business Profile** — primary review platform for local landscaping search
- **Yelp** — review monitoring and reply posting
- **Facebook** — review monitoring for businesses with active Facebook presence
- **Jobber** — job and customer data for residential and light commercial landscaping accounts; used to match reviews to recent jobs
- **Aspire** — job management and customer account data for commercial landscaping and HOA contract accounts
- **Email / Slack / SMS** — manager alerts for service failure reviews and weekly digest delivery

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your platforms, job management system, brand voice preferences, and escalation routing
3. Give the agent its first task: *"Pull all reviews from the past 30 days, triage them by urgency, and draft replies for any that haven't been answered yet."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`. Edit either file to update review platforms, the owner name used in reply sign-offs, the manager escalation contact, the service failure SLA window, or the digest schedule and delivery channel.

## Pattern

Vertical / NON-TECH — Landscaping & lawn care reputation management
