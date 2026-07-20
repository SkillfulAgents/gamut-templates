> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/bid-proposal-drafter/hosp-bid-proposal-drafter)** — one-click deploy, no setup.

# Hospitality/Hotels - Bid / Proposal Drafter

Hotel sales managers spend hours building group proposals — pulling room blocks, looking up past contracts, formatting catering menus, and writing the same property overview for the hundredth time. This agent automates the first pass: it reads the inbound RFP or inquiry, searches the property's past contracts and rate cards for reusable content, drafts each required section (cover letter, room block, meeting space, F&B, contract terms), and produces a missing-info checklist so the sales manager knows exactly what to finalize before sending.

## Who this is for

Hotel sales managers, catering sales managers, and directors of sales at full-service or select-service hotels who handle group RFPs, meeting inquiries, and event bids and want to compress the time from inquiry to first draft.

Relevant subsegments: HOSP

Best fit for properties receiving 5-50 group RFPs per month, using Opera, Cloudbeds, or Cvent, with a proposal library in Drive or SharePoint.

## What it does

1. **RFP ingestion and parsing** — reads the incoming group RFP, event brief, or meeting inquiry from Opera, Cloudbeds, Cvent, or email; extracts dates, room block, event space requirements, F&B needs, and deadlines; flags blockers
2. **Proposal library search** — searches past contracts and approved templates for this client or similar event types; retrieves boilerplate sections, property overview, current rate cards, and catering menus
3. **First-pass proposal draft** — assembles the full proposal: cover letter, property overview, room block with group rate, meeting/event space with setup options, F&B packages, AV inclusions, concessions, and contract terms; marks pricing placeholders where rate card data is unavailable
4. **Missing-info checklist** — produces a structured checklist of items the sales team must confirm before sending (pricing, availability, AV specifics, special requests)
5. **Draft delivery** — saves the draft and checklist to the output folder and notifies the sales manager via Slack with the deadline, room block size, and top items to resolve

## Key integrations

- **Opera / Cloudbeds** — group RFP intake, availability, past reservations
- **Cvent** — RFP intake from meeting planners
- **Google Drive / SharePoint** — proposal library, rate cards, catering menus, output folder
- **Slack / Email** — draft delivery notifications to the sales manager

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your property, RFP intake source, proposal library, and delivery preferences
3. Give the agent its first task: *"Draft a proposal for [client name] — [N] rooms, [event type], [dates]."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`.

## Pattern

Vertical / NON-TECH - Hospitality and hotels

Relevant subsegments: HOSP
