> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/speed-to-lead/resi-speed-to-lead-booking)** — one-click deploy, no setup.

# Residential Real Estate - Speed-to-Lead & Booking

Every minute a lead goes unanswered is a minute a competitor can respond. Studies consistently show that the odds of qualifying an inbound real estate lead drop by over 80% after the first five minutes. This template solves that: it picks up every inbound buyer or seller lead - from Zillow, Realtor.com, your website, or your CRM - replies within 60 seconds, asks the right qualifying questions, books a showing or consultation against real agent availability, and follows up automatically on any lead that goes quiet.

## Who this is for

Residential brokerages, real estate teams, and solo agents who generate inbound leads from online portals (Zillow Premier Agent, Realtor.com), their own websites, or paid campaigns. Ideal for teams that struggle with consistent, fast follow-up because agents are busy with active clients, or for brokerages that want to standardize lead response across a distributed agent roster. Works best when leads flow into Follow Up Boss or kvCORE.

## What it does

1. **Sub-minute lead response** - Detects new leads across all configured sources and sends a personalized first reply within 60 seconds, referencing the specific property or search that brought the lead in.

2. **Structured qualification** - Walks each lead through a consistent set of qualifying questions covering buyer vs. seller intent, timeline, price range, neighborhood preferences, and financing status. Logs all answers to the lead's CRM record.

3. **Showing and consultation booking** - Checks the assigned agent's live calendar availability, offers 2-3 time slots, confirms the appointment, and sends reminders 24 hours and 2 hours before.

4. **Smart routing and agent notification** - Matches each lead to the right agent based on your configured rules (farm area, source, round-robin, or specialty), then notifies the agent immediately with a lead summary.

5. **Cold lead nudges and escalation** - Tracks which leads have gone uncontacted or unresponded, runs a multi-touch follow-up sequence, and escalates persistently unworked leads to the team lead before they go cold permanently.

## Key integrations

- **Follow Up Boss** - Primary CRM for logging lead records, contact notes, appointment details, pipeline status, and agent assignments. The agent reads and writes to FUB throughout the entire lead lifecycle.
- **kvCORE** - Alternative or supplemental CRM/IDX platform; used for lead ingestion, contact management, and drip campaign coordination where configured.
- **MLS** - Used to pull live listing data, comparable sales, and property details to personalize qualification conversations and first-touch messages.
- **Zillow Premier Agent** - Source of inbound buyer leads; the agent monitors ZPA lead notifications and triggers the response workflow immediately on receipt.
- **Realtor.com** - Additional inbound lead source; lead alerts from Realtor.com feed into the same qualification and booking workflow as all other sources.

## Getting started

1. **Import the workspace** - In Gamut, import this workspace zip to create a new agent workspace. All configuration files and skills are included.

2. **Run agent-onboarding** - Open the workspace and run the `agent-onboarding` skill. The skill will ask you setup questions about your CRM, lead sources, agent roster, and routing rules, then write your configuration automatically.

3. **Give your first task** - Once onboarding is complete, try: "We just got a new Zillow lead from Sarah Chen - she's interested in 3-bed homes in the Westside under $750k. Set her up and send the first reply."

## Configuration

During onboarding, the skill creates a `config.json` file in your workspace with your CRM credentials, agent roster, routing rules, and follow-up sequence timing. It also fills in the `## Your context` section of `CLAUDE.md` with a plain-English summary of your setup. You can edit either file directly if your setup changes - for example, to add a new agent, update routing rules, or adjust follow-up timing.

---

Relevant subsegments: RESI
