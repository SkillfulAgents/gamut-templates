> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/review-reputation/retail-multi-location-review-reputation)** — one-click deploy, no setup.

# Retail (Multi-Location) - Review & Reputation Replies

Managing online reviews across five, ten, or fifty retail locations is a full-time job that rarely gets one. Reviews pile up on Google and Yelp, complaints go unacknowledged, and the store in a struggling market quietly slides toward a 3.2-star average while no one on the leadership team notices until it is too late. This agent handles the monitoring, drafting, routing, and reporting so your team can focus on the reply approvals that actually need human judgment - not the inbox hygiene.

## Who this is for

Multi-location retail operators who need consistent, on-brand review management across locations without hiring a dedicated reputation team. Fits specialty retail, general merchandise, home goods, sporting goods, apparel, and similar formats where each location has its own Google Business Profile and Yelp listing, and where product and transaction data lives in Lightspeed or Shopify POS.

## What it does

1. **Monitors reviews across all locations.** Pulls new Google Business Profile and Yelp reviews for every configured store location on a daily cadence, tags each by location, platform, rating, and complaint category.

2. **Drafts store-voiced replies.** Writes a reply for every unaddressed review using each location's configured voice profile - formal or casual, with the right sign-off and regional tone. Presents drafts for approval before posting.

3. **Routes complaints to location managers.** Flags 1-2 star reviews and explicit complaint language, then notifies the assigned manager with a complaint summary, review link, and suggested reply draft. Pulls relevant transaction or inventory records from Lightspeed or Shopify POS when a review references a specific product or purchase.

4. **Delivers a weekly rating digest.** Every Monday, sends a structured per-location report covering average ratings, week-over-week changes, review volume, top complaint themes, and any locations trending below your configured threshold.

5. **Tracks reply status and response time.** Logs every review through its lifecycle (drafted, approved, posted, skipped) and surfaces approvals that have been sitting for more than 48 hours so nothing falls through.

## Key integrations

- **Google Business Profile** - Source for all Google reviews across your location listings. The agent reads new reviews and posts approved replies directly to each location's listing.
- **Yelp** - Source for Yelp reviews across locations. Read access for review ingestion; reply posting via the Yelp Fusion API or Business Owner portal depending on your access level.
- **Lightspeed** - Point-of-sale and inventory system for locations using Lightspeed. Used to look up transaction and product records when a review references a specific purchase or item.
- **Shopify POS** - Point-of-sale system for locations using Shopify POS. Same lookup role as Lightspeed for locations on the Shopify stack.

## Getting started

1. **Import the workspace.** In Gamut, import this workspace zip to create a new agent workspace.

2. **Run agent-onboarding.** Type `run agent-onboarding` to start the setup skill. It will walk you through your location list, POS systems, review platform credentials, manager routing, and voice profiles. Your answers are saved to config.json and written into the agent's context.

3. **Give your first task.** Once onboarding is complete, try: "Pull all new reviews from the past 7 days across all locations and draft replies for anything unanswered."

## Configuration

Your setup is stored in `.claude/config.json` (created during onboarding) and in the `## Your context` section at the bottom of `CLAUDE.md`. To add a new location, update the locations array in config.json and re-run onboarding for that location, or edit the files directly and confirm with the agent.

---

Relevant subsegments: RETL
