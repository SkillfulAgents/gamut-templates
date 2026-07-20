> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/review-reputation/hvac-review-reputation)** — one-click deploy, no setup.

# HVAC/Plumbing/Electrical - Review & Reputation Replies

Trade contractors win or lose jobs on Google stars and Angi ratings, but most owner-operators have no system for monitoring reviews or responding consistently. A week-old unanswered 1-star review about a no-show technician costs more in lost leads than the job itself was worth. This agent monitors reviews across Google Business Profile, Yelp, and Angi, drafts on-brand owner-voiced replies, escalates service failure reviews to the manager with the full job record attached, and delivers a weekly rating trend digest.

## Who this is for

Owner-operators and service managers running HVAC, plumbing, or electrical businesses who use ServiceTitan or FieldEdge for dispatch and job management, receive steady review volume across multiple platforms, and need a consistent process for responding to reviews without hiring a marketing coordinator.

Relevant subsegments: HVAC

Best fit for businesses with 3–25 technicians, 50+ jobs per month, and active Google Business Profile listings where reputation directly drives inbound lead volume.

## What it does

1. **Monitor & ingest incoming reviews** — pulls new reviews from Google Business Profile, Yelp, and Angi; cross-references reviewer name or address against job records in ServiceTitan or FieldEdge; classifies each review by star rating and flags technician mentions, safety concerns, or unresolved callback requests
2. **Prioritize responses** — queues replies by urgency: 1–2 star reviews within 24 hours, 3-star within 48 hours, positive reviews within 72 hours or on a batched schedule
3. **Draft on-brand replies** — writes all replies in the owner's voice, specific to the service and reviewer; positive reviews get a personal thank-you and referral nudge; negative reviews acknowledge the experience and invite a direct conversation without arguing publicly
4. **Route service failures to manager** — escalates any 1–2 star review mentioning a no-show, property damage, safety hazard, billing dispute, or unreturned call; attaches the associated ServiceTitan or FieldEdge job record so the manager has full context before responding
5. **Weekly rating trend digest** — every Monday delivers a summary of new reviews by platform, 7- and 30-day average star ratings, trend direction, technician mentions, and any reviews that went unanswered past the response window

## Key integrations

- **ServiceTitan** — job management and dispatch; used to cross-reference reviewer identity and pull job records for escalations
- **FieldEdge** — field service management alternative; same job-record lookup for escalation context
- **Google Business Profile** — primary review platform for inbound leads
- **Yelp** — secondary review platform, especially relevant for residential plumbing and electrical
- **Angi** — lead generation platform where ratings directly affect lead distribution
- **Email / Slack** — owner and manager alerts, escalation routing, and weekly digest delivery

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will walk through your business details, review platforms, and ServiceTitan or FieldEdge connection to configure the agent for your operation
3. Give the agent its first task: *"Pull all reviews from the past 14 days, flag any that need escalation, and draft replies for everything that's ready to go."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`. Edit either file to update the owner sign-off name, response window thresholds, escalation routing (email vs. Slack), auto-post behavior, or the day and destination for the weekly digest.

## Pattern

Vertical / NON-TECH — HVAC, plumbing, and electrical reputation management
