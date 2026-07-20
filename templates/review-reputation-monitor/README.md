> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/review-reputation/review-reputation-monitor)** — one-click deploy, no setup.

# Review & Reputation Monitor

> Monitors Google, Yelp, and Facebook reviews across your locations, drafts on-brand replies for approval, alerts immediately on low-star reviews, and posts a weekly rating-trend digest.

## What it does

Review & Reputation Monitor checks your review profiles on a regular cycle, logs every new review to your tracker, and drafts replies in your brand voice - not a generic bot tone. The moment a 1 or 2 star review lands, it alerts your team and tags an owner so you can respond fast. Each week it posts a digest showing how your rating is trending by source and by location, which locations are climbing, which need attention, and the recurring themes customers keep mentioning.

By default nothing gets posted to a public review site without your approval. You can keep it in draft-only mode (the agent writes the reply, you copy-paste and post it) or let it post automatically once you have approved each draft.

Works for multi-location local and operator businesses: home and field services (HVAC, pest control, landscaping, cleaning, painting, alarm/security), restaurants and QSR, retail, fitness and salons, hospitality, auto, multi-unit and franchise groups, and residential real estate.

## What you'll need

- **Accounts:**
  - Review profiles: your Google Business Profile, Yelp, and/or Facebook pages (accessed via the browser)
  - Tracker: Airtable, Notion, Google Sheets, or similar (to log reviews and replies)
  - Slack and/or Email (for low-star alerts and the weekly digest)
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** the review profile URLs for each of your locations, and 2-3 real replies you have posted before (these are what make the drafts sound like your brand, not a bot)

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - Your business name and brand voice
   - Your locations and their review profile URLs
   - Which review sources to monitor (Google, Yelp, Facebook)
   - Whether replies should be draft-only or auto-posted after your approval
   - Which channel gets low-star alerts and who the escalation owner is
   - Where and how often to post the weekly digest
   - 2-3 real replies you have posted before so the agent matches your voice
3. Once setup finishes, give the agent its first task: *"Check all my review profiles but do NOT post anything and do NOT update any rows. Show me what you'd do - which new reviews you found, which you'd alert on, and a draft reply for each."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` - the agent's instructions and your configuration (written by onboarding).
- `.claude/skills/agent-onboarding/` - first-run setup interview.

## Notes

- Nothing auto-posts to a public review site unless you choose auto-after-approval mode AND approve the specific draft. The default is draft-only.
- 1 and 2 star reviews always get a human in the loop before any reply is posted, no matter which mode you pick.
- Reviews are read through the browser using your connected profiles - the agent does not need a paid reputation-management API.
- Slack is recommended for instant low-star alerts; if you only connect email, alerts and the digest arrive by email instead.
- The agent never argues with reviewers, never shares private customer details in a public reply, and escalates legal threats or serious-harm allegations straight to your owner instead of drafting a reply.
- The weekly digest tracks trends by source and by location, so multi-location operators can see which sites are pulling their average down.

Relevant subsegments: HVAC, PEST, RSTR, LAND, CLEN, PNTG, ALRM, FOOD, RETL, FITN, HOSP, AUTO, MULT, FRNC, RESI, CRE
