> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/review-reputation/restaurant-qsr-review-reputation)** — one-click deploy, no setup.

# Restaurant/QSR - Review & Reputation Replies

Every restaurant lives and dies by its online reputation, yet most owners and operators spend hours each week manually checking Google, Yelp, and TripAdvisor, writing one-off replies, and hoping nothing slipped through. This agent automates the monitoring and drafting work so you stay on top of every review, respond in your own voice, catch food safety or complaint escalations before they become crises, and get a clear weekly picture of how your ratings are trending across platforms.

## Who this is for

This template is built for independent restaurants, multi-location QSR operators, and hospitality groups that manage online reviews across Google Business Profile, Yelp, and TripAdvisor. It works best for operations where the owner or general manager wants to maintain a personal, authentic reply voice without reviewing every platform manually every day. It is equally suited to a single-location neighborhood restaurant and a franchise group managing dozens of profiles.

## What it does

1. **Monitors reviews across platforms** - Polls Google Business Profile, Yelp, and TripAdvisor on a configurable schedule and surfaces new reviews prioritized by star rating, with 1- and 2-star reviews appearing first for fastest response.

2. **Drafts on-brand, owner-voiced replies** - Writes custom replies for each review using your brand voice guidelines, addressing specifics the guest mentioned rather than recycling generic templates. Drafts queue for your approval before publishing.

3. **Escalates safety and serious service complaints** - Automatically flags reviews containing food safety concerns, allergy incidents, or threatening language and routes them directly to the designated manager with the full review text and a hold message, preventing any premature public reply.

4. **Cross-references Toast POS data** - For time-stamped complaints, pulls Toast transaction and labor data to give management operational context (cover volume, staffing) in internal escalation reports without exposing that detail publicly.

5. **Delivers a weekly rating digest** - Every Monday, sends a digest covering total reviews, average ratings, week-over-week deltas, recurring positive and negative themes, escalation count, and reply rate - so ownership has a clear signal on reputation health without digging through three platforms.

## Key integrations

- **Google Business Profile** - Primary source for Google reviews; the agent reads new reviews and publishes approved replies via the API.
- **Yelp** - Reads new reviews from your Yelp Business listing; reply publishing requires Yelp Business Owner API access.
- **TripAdvisor** - Monitors your TripAdvisor listing for new reviews; reply publishing uses the Management API.
- **Toast POS** - Provides transaction volume and labor data to contextualize complaint timing in internal escalation reports.

## Getting started

1. **Import the workspace** - In Gamut, import this workspace zip. The agent will be available immediately with placeholder configuration.

2. **Run agent-onboarding** - Type `run agent-onboarding` in the chat. The onboarding skill will ask you a series of questions about your restaurant, brand voice, platform credentials, escalation contacts, and reply preferences. Your answers populate `config.json` and the "Your context" section in `CLAUDE.md`.

3. **Give your first task** - Once onboarding is complete, try: "Show me all unanswered reviews from the last 7 days and draft replies for the 1-star ones."

## Configuration

After onboarding, your settings live in `config.json` at the workspace root and in the `## Your context` section at the bottom of `CLAUDE.md`. The config file holds API credentials, escalation contacts, scheduling preferences, and reply-approval workflow settings. The CLAUDE.md context section holds a plain-English summary of your brand voice, restaurant name, locations, and any standing reply rules. You can edit either file directly at any time to update preferences without re-running onboarding.

---
Relevant subsegments: FOOD
