> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/marketing-content/competitor-watch)** — one-click deploy, no setup.

# Competitor Watch

> Produces a weekly, fully-sourced diff of competitor moves - pricing, product, positioning, funding, hiring, content - and translates each into what it means for us, posted to your team.

## What it does

Competitor Watch runs once a week, visits each of your competitors' watched pages, and searches public signals across the dimensions you care about - pricing, product launches, messaging shifts, funding, hiring, and notable content. It compares everything to a baseline snapshot it kept from last week, builds a clean diff of exactly what changed, and translates every change into a short "what it means for us" implication grounded in your own positioning. The result is one sourced digest posted to your team channel.

The guarantee that makes it useful: every claimed move carries a source link and an observation date. The agent only watches public information and never reports a change it cannot source - no speculation, no rumor.

Works for SaaS vendors tracking rivals, marketing teams and agencies watching the field, CPG/DTC brands monitoring competitors, product managers maintaining a competitive landscape, and investors tracking a portfolio or market.

## What you'll need

- **Accounts:**
  - Snapshot storage: Google Drive, Notion, Airtable, Google Sheets, Dropbox, or similar (to keep one baseline per competitor week over week)
  - Browser (built into Gamut, for visiting watched pages)
  - Web search (built into Gamut, for funding/hiring/content signals)
  - Slack (for the weekly digest)
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** your competitor list (names + URLs + which pages to watch), and a short description of your own positioning so the implications are sharp

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - Who your competitors are - names, URLs, and which pages to watch per competitor (pricing, product, blog, etc.)
   - Which dimensions to track (pricing, product, positioning, funding, hiring, content)
   - Your own positioning, so each change can be turned into a real implication for you
   - Which day and cadence the digest should run, and which Slack channel it posts to
   - Any sources to always include or always exclude
   - Where to keep the baseline snapshots (Drive, Notion, Airtable, Sheets, etc.)
3. Once setup finishes, give the agent its first task: *"Capture a baseline snapshot of every competitor now and show me what you captured per page and source, but do NOT post anything to the team yet."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` - the agent's instructions and your configuration (written by onboarding).
- `.claude/skills/agent-onboarding/` - first-run setup interview.

## Notes

- The first run is always a baseline capture - there is nothing to diff against yet, so the first real diff arrives the following week.
- Public information only. The agent never logs into competitor accounts, never uses paywalled or private data, and never reports a change it cannot source.
- Every change in the digest carries a source link and an observation date; anything unverifiable is dropped, not guessed.
- If a watched page is unreachable, the agent reports the coverage gap rather than silently skipping it.
- Slack is recommended for the digest but you can route it to a DM instead.
- Implications are only as sharp as the positioning you give it - a clear positioning description makes the "what it means for us" lines genuinely useful.

Relevant subsegments: RVTK, MTTK, CSTK, CYBR, DEVT, DATA, AICO, FNTK, INSR, HRTK, LGTK, PPTK, SCTK, ECTK, SAAS, EDTK, CLTK, HLTK, MKTG, CPG, DTC, PEVC, MGMT
