> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/review-reputation/hosp-review-reputation)** — one-click deploy, no setup.

# Hospitality/Hotels - Review & Reputation Replies

Hotels live and die by their online rating. A single unanswered 2-star review on TripAdvisor or Google can cost a property dozens of bookings — yet most properties have no system for monitoring reviews across Google, TripAdvisor, Yelp, and OTAs in one place, let alone drafting timely, on-brand replies. This agent monitors every incoming guest review, classifies it by severity, drafts a management-voiced reply specific to that guest's experience, escalates service failures to the duty manager before anything goes public, and delivers a weekly rating trend digest so leadership sees the full picture at a glance.

## Who this is for

General managers, front office managers, and guest relations teams at independent hotels, boutique properties, select-service brands, and resort properties who want every review answered promptly and no service failure to slip by unaddressed.

Relevant subsegments: HOSP

Best fit for properties receiving 10-200 reviews per month across Google, TripAdvisor, Yelp, and/or Booking.com/Expedia, using Opera or Cloudbeds as the PMS.

## What it does

1. **Review monitoring** — pulls new reviews from Google Business Profile, TripAdvisor, Yelp, Booking.com, and Expedia; cross-references reviewer name and stay dates against the PMS to identify room type and stay segment; classifies by star rating and flags service failure signals
2. **Response prioritization** — queues replies by urgency: 1-2 star reviews within 24 hours, mixed reviews within 48, positive reviews within 72
3. **On-brand reply drafts** — writes each reply in the General Manager's voice, specific to the guest's review content; never copy-pastes boilerplate; positive reviews get a personalized thank-you and return invitation, negative reviews get empathy and a private follow-up offer
4. **Service failure escalation** — routes any review mentioning cleanliness, safety, billing errors, or unresolved complaints to the duty manager with the PMS reservation record attached; holds the public reply until the manager confirms
5. **Weekly rating digest** — every Monday, delivers a rating trend summary by platform (7-day and 30-day averages, reply rate, escalation count, any platform drop of 0.2+ stars) to the GM via Slack or email

## Key integrations

- **Google Business Profile / TripAdvisor / Yelp** — review monitoring and reply posting
- **Booking.com / Expedia** — OTA review ingestion
- **Opera / Cloudbeds** — stay data cross-reference for reviewer matching
- **Slack / Email** — escalation alerts and weekly digest delivery

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your property, connected review platforms, PMS, and delivery preferences
3. Give the agent its first task: *"Pull this week's new reviews and draft replies."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`.

## Pattern

Vertical / NON-TECH - Hospitality and hotels

Relevant subsegments: HOSP
