> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/review-reputation/cleaning-review-reputation)** — one-click deploy, no setup.

# Cleaning/Janitorial - Review & Reputation Replies

Running a cleaning or janitorial business means your reputation lives and dies on reviews — but between managing staff, scheduling jobs, and handling client calls, who has time to check Google, Yelp, and Facebook every day? This Gamut agent monitors your reviews across all three platforms, drafts on-brand replies ready for your approval, escalates 1-2 star complaints straight to your operations manager, and delivers a weekly rating trend digest so you always know where you stand.

## Who this is for

Cleaning and janitorial business owners — residential, commercial, or both — who are losing new business because reviews go unanswered and service complaints slip through the cracks.

If you've ever cringed at a 1-star review you didn't see for three days, or realized you've never replied to a single Google review, this agent is for you.

Relevant subsegments: CLEN

## What it does

1. **Monitor and detect new reviews** — polls Google Business Profile, Yelp, and Facebook daily and logs every new review with rating, source, and text.
2. **Triage and prioritize** — classifies reviews by severity (escalate, reply needed, standard thank-you) and flags any that mention staff by name.
3. **Draft on-brand replies** — writes a personalized, human-sounding reply for every review, ready for your approval before posting. Never auto-posts.
4. **Escalate service failures** — for 1-2 star reviews with specific complaints, immediately alerts your operations manager with review details and a recommended follow-up. Cross-references job history in Swept or Janitorial Manager if connected.
5. **Weekly rating trend digest** — every Monday delivers a summary of new reviews by platform, average rating vs. prior week, unresolved escalations, and top positive/negative themes.

## Key integrations

- **Swept** — field operations and scheduling data for cross-referencing job history against complaints
- **Janitorial Manager** — work order and client records for complaint context and follow-up

The agent also connects to Google Business Profile, Yelp, and Facebook via their respective APIs or connected accounts configured during onboarding.

## Getting started

1. **Import this workspace** into Gamut by uploading the zip file through the workspace import flow.
2. **Run the `agent-onboarding` skill** — type `run agent-onboarding` in your first message. The agent will walk you through setup with a short series of questions (business name, review platforms, brand voice, escalation contact, etc.).
3. **Send your first task prompt** — once onboarding is complete, try: "Check for new reviews and show me any drafts that need approval."

## Configuration

After onboarding, your settings are stored in `config.json` at the workspace root and your business context is written into the `## Your context` section of `CLAUDE.md`. You can update either file directly if your details change (new operations manager, adjusted brand voice, different digest day, etc.).

## Pattern

Vertical / NON-TECH — Cleaning & janitorial reputation management
