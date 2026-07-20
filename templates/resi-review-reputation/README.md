> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/review-reputation/resi-review-reputation)** — one-click deploy, no setup.

# Residential Real Estate - Review & Reputation Replies

Every real estate agent and brokerage lives or dies by their online reputation, but keeping up with reviews on Google, Zillow, and Realtor.com - while also drafting thoughtful, on-brand replies for each one - takes time most agents don't have. Negative reviews left unaddressed erode trust; positive ones left without a reply are missed relationship opportunities. This template automates the full review management loop: monitoring all three platforms daily, drafting replies in the agent's own voice, routing service failures to the broker before they compound, and delivering a weekly rating trend digest so leadership always knows where things stand.

## Who this is for

This template is for residential real estate brokerages, agent teams, and individual agents who maintain active profiles on Google Business Profile, Zillow, and/or Realtor.com and want a systematic way to respond to reviews promptly and consistently. It fits any size operation - from a solo agent managing their own brand to a brokerage with multiple agents whose profiles all need monitoring. Teams using Follow Up Boss or kvCORE for CRM will get additional value from the contact cross-reference and pipeline flagging features.

## What it does

1. **Monitors reviews daily across all three platforms** - Pulls new reviews from Google Business Profile, Zillow, and Realtor.com on a configured schedule and deduplicates across cycles so nothing is processed twice.

2. **Drafts on-brand replies in the agent's voice** - For every new review, generates a draft reply tuned to the agent's established tone: specific and warm for positive reviews, empathetic and resolution-focused for negative ones, never defensive and never generic.

3. **Routes service failures to the broker** - Reviews at or below a configurable star threshold trigger an internal escalation note - summarizing the complaint and a suggested resolution path - routed to the broker or team lead for action before the situation worsens.

4. **Cross-references reviews with CRM contacts** - When a review references a transaction or property, the agent searches Follow Up Boss and kvCORE for the corresponding contact, attaches the review to the record, and flags active pipeline deals for relationship repair.

5. **Delivers a weekly rating trend digest** - Every week, sends a scannable digest covering total reviews, average ratings by platform, week-over-week changes, recurring themes, reply throughput, and any open escalations.

## Key integrations

- **Google Business Profile** - Primary source for Google reviews; the agent monitors the configured location ID for new reviews and posts approved replies via the API
- **Zillow** - Monitors the agent's or team's Zillow profile for new reviews and rating changes
- **Realtor.com** - Monitors the agent's or team's Realtor.com profile for new reviews and rating changes
- **Follow Up Boss** - CRM cross-reference for matching reviewers to contacts, attaching review notes to records, and flagging active pipeline deals
- **kvCORE** - Secondary CRM option for contact lookup, review note logging, and pipeline-stage flagging
- **MLS** - Verifies property or listing details mentioned in reviews against active or recently closed MLS records to catch factual inaccuracies before they go unaddressed

## Getting started

1. **Import this workspace** - In Gamut, import the workspace zip. This loads the agent instructions, onboarding skill, and config structure into a new workspace.

2. **Run agent-onboarding** - Type `run agent-onboarding` (or the equivalent slash command in your Gamut workspace). The onboarding skill will walk you through the setup questions - platform profile IDs, CRM credentials, preferred voice samples, escalation contacts, and reply approval settings - and write the results to config.json and the agent's context section.

3. **Give the agent its first task** - Once onboarding is complete, start with: "Pull all reviews from the last 7 days across Google, Zillow, and Realtor.com and draft replies for each one." The agent will work through the queue and surface drafts for your review.

## Configuration

After onboarding, your settings live in `config.json` at the workspace root and in the `## Your context` section of `CLAUDE.md`. The config file holds credentials, profile IDs, thresholds, and scheduling settings. The context section in CLAUDE.md holds a plain-English summary of the agent's voice, escalation contacts, and any standing preferences. Both can be edited directly if you need to update a setting after the initial setup.

---

Relevant subsegments: RESI
