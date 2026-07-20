> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/productivity-internal-ops/pack-builder)** — one-click deploy, no setup.

# Pack Builder

> Assembles your recurring deck, board pack, LP update, or QBR by pulling the latest numbers from your data sources into your branded template as a draft for human review.

## What it does

Pack Builder runs on your reporting cadence, pulls the latest numbers and updates from your data sources, and drops them into a fresh copy of your branded template - producing a DRAFT for you to review, refine, and finish. It does the hours of copy-paste assembly that eat up the days before every recurring report: opening five tabs, finding the right figures, pasting them into the right slots, refreshing the charts, and writing the first pass of commentary.

It works for founder board decks, finance and FP&A board packs, VC/PE LP updates, customer success QBRs, and consulting status decks - anywhere you rebuild the same report every month, quarter, or week from the same set of sources.

Pack Builder never sends or presents the pack. It hands you a draft in your own template, with every number traced back to its source, so you can review the figures, polish the story, and decide when it's ready to go.

## What you'll need

- **Accounts:**
  - Data sources: Google Sheets, a data warehouse (BigQuery, Snowflake, Redshift), a CRM (Salesforce, HubSpot), or finance tools (QuickBooks, NetStreet, Stripe, etc.)
  - Template + draft storage: Google Slides, Google Docs, PowerPoint, or similar
  - Slack (for the review handoff and flag alerts)
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** your existing branded template (the one you rebuild every cycle), and a clear sense of which section pulls from which source

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - What kind of pack you build and your role (founder, FP&A lead, VC, CS manager, consultant, etc.)
   - Which data sources to pull from, where your branded template lives, and where drafts should be saved
   - The section-to-source mapping: which metric or section comes from which source
   - Your cadence and reporting period (monthly, quarterly, weekly)
   - Who reviews the draft, and the narrative tone for any commentary sections
3. Once setup finishes, give the agent its first task: *"Build a draft of the pack for the most recent period, but tell me first which sources you can reach and which sections you'd fill - do NOT finalize anything. Show me the source trace and any gaps."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` - the agent's instructions and your configuration (written by onboarding).
- `.claude/skills/agent-onboarding/` - first-run setup interview.

## Notes

- Pack Builder produces a DRAFT only. It never sends, presents, or shares the pack with a board, LP, customer, or any external audience - a human always finishes and sends it.
- Every number in the draft traces back to its source. The agent includes a source trace mapping each figure to where it came from.
- The agent never fabricates a missing number. If a source is unreachable or returns no data, it leaves a "[MISSING]" placeholder and flags it for you rather than guessing.
- Your master template is never edited. The agent always works in a fresh copy and keeps the word DRAFT in the file name until you remove it.
- One source per section keeps the trace clean. If a section needs blending across sources, the agent flags it for you instead of guessing how to combine them.
- Slack is recommended but optional; if not connected, the review handoff and flags will surface in the draft itself.
- For board-level and regulated reporting, the agent prefers flagging an uncertainty over filling it in.

Relevant subsegments: RVTK, MTTK, CSTK, CYBR, DEVT, DATA, AICO, FNTK, INSR, HRTK, LGTK, PPTK, SCTK, ECTK, SAAS, EDTK, CLTK, HLTK, PEVC, IBMA, MGMT, RDEV, NGO, ASSN
