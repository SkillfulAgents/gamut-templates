> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/marketing-content/dtc-growth-creative-test-loop)** — one-click deploy, no setup.

# DTC Growth / Creative Test Loop

Most DTC and CPG brands are sitting on winning creative signals they never act on fast enough. The performance data is in Meta and Google, the customer voice is in Amazon and Shopify reviews, and the inventory risk is in your warehouse — but connecting those signals to a new creative brief, and that brief to a queued ad, happens manually (if it happens at all). This agent closes that loop automatically: it finds what is working, writes the next test brief, queues it for your team, and keeps an eye on reviews and stock so nothing undercuts your best-performing campaigns.

## Who this is for

Growth marketers, performance teams, and brand operators at DTC and CPG brands running paid social and marketplace ads. If your team spends hours each week manually pulling ad performance data, mining reviews for copy hooks, or chasing down stock-out risk on active campaigns — this agent is built for you.

Relevant subsegments: CPG, DTC, ECTK, RETL

## What it does

1. **Monitor and detect winning signals** — Pulls Meta and Google Ads performance on a configured cadence, identifies creatives crossing your ROAS/CTR/CPA threshold, and surfaces Amazon listing shifts and Shopify inventory risk.
2. **Generate creative variant briefs** — For each winning creative, produces 2–3 structured test briefs with hook angle, format, copy direction, CTA, and hypothesis — informed by Amazon and Shopify review mining.
3. **Queue for launch** — Formats briefs as structured Slack messages (and optional project management task cards) in your creative ops channel, ready for human review and approval. No autonomous ad launches.
4. **Log outcomes** — After variants run, pulls results and compares to the source creative. Logs what worked, what did not, and which hypothesis types are validated — building a feedback loop over time.
5. **Alert and digest** — Sends a weekly growth digest (top creatives, new briefs, review summary, inventory flags) and real-time alerts for stock-out risk, review score drops, and ad spend anomalies.

## Key integrations

- **Meta Ads** — Ad performance data, creative identification, spend monitoring
- **Google Ads** — Ad performance data, campaign pacing, spend monitoring
- **Amazon** — Listing performance, BSR tracking, review mining
- **Shopify** — Inventory levels, SKU-to-campaign mapping, product review data
- **Slack** — Creative brief queue, weekly digest, real-time alerts

## Getting started

1. **Import this workspace** into Gamut by uploading the zip file via the workspace import flow.
2. **Run agent-onboarding** — type `/agent-onboarding` (or "start onboarding") to walk through setup. The skill will ask about your brand, connected ad accounts, and notification preferences, then write your configuration automatically.
3. **First task prompt** — Once onboarding is complete, try: "Pull last week's top-performing creatives from Meta and Google, mine reviews for the top 3 SKUs, and queue briefs for the best candidates."

## Configuration

Onboarding writes a `config.json` file in the workspace root and fills in the `## Your context` section of `CLAUDE.md`. You can edit either file directly to adjust thresholds, cadence, connected accounts, or alert preferences. Key settings include: winning KPI and threshold, brief cadence, inventory lookahead window, Slack channel names, and evaluation window for outcome logging.

## Pattern

Vertical / NON-TECH — Consumer brand growth & creative ops
