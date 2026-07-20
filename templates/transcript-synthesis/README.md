> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/productivity-internal-ops/transcript-synthesis)** — one-click deploy, no setup.

# Transcript Synthesis

> Clusters recurring themes across a batch of call transcripts, weights each theme by the ARR of the accounts that raised it, and backs every theme with verbatim quotes and source links.

## What it does

Transcript Synthesis pulls a batch of call transcripts (sales calls, discovery, user interviews, CS calls), clusters the recurring themes, and ranks them by the ARR or deal value of the accounts that raised them - not by how many times they came up. The result: the loudest theme is no longer mistaken for the most valuable one. A complaint raised by ten free-trial users and a feature gap raised by your three largest renewals get sorted by what they are actually worth, side by side.

Every theme is backed by verbatim quotes with the call and source link it came from, and the ARR weighting is fully transparent - you can see exactly which accounts and dollar figures produced each theme's score. It summarizes and reports; it never contacts customers or touches your deals.

Works for product teams prioritizing the roadmap, sales leaders reading the field, CS teams spotting churn signals, UX researchers synthesizing interviews, VCs digesting diligence calls, and consultants distilling stakeholder interviews.

## What you'll need

- **Accounts:**
  - Transcript source: Gong, Granola, Fireflies, Otter, or Zoom
  - CRM (for ARR / deal weighting): Salesforce, HubSpot, or similar
  - Output storage: Notion, Google Docs, Google Sheets, or similar
  - Slack (for the digest)
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** a clear idea of which calls to include (call types and time window) and which CRM field carries the value you want to weight by (ARR, ACV, or open deal value)

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - Your role and what kind of calls you're synthesizing (product, sales, CS, research, etc.)
   - Which transcript source, CRM, output location, and Slack channel to use
   - Which calls to include - call types and the time window
   - Whether to use your own theme taxonomy or let the agent cluster themes freely
   - Which CRM field to weight by (ARR, ACV, or open deal value)
   - Output format and digest cadence
3. Once setup finishes, give the agent its first task: *"Pull this week's calls but do NOT write anything to my output location or post to Slack. Show me the theme clusters, the ARR weighting behind each, and two verbatim quotes per theme so I can sanity-check before you run for real."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` - the agent's instructions and your configuration (written by onboarding).
- `.claude/skills/agent-onboarding/` - first-run setup interview.

## Notes

- This agent is read-and-report only. It never contacts customers, replies to call participants, or updates your CRM or deals.
- Every theme is backed by at least one verbatim quote with the account, call type, date, and a link to the source. Themes with no quote behind them are dropped.
- The ARR weighting is transparent by design - the synthesis always shows the accounts and dollar values behind each theme, so you can audit the ranking.
- Accounts that don't match a CRM record still count toward mentions but carry zero weight, and they're flagged in the coverage notes. The agent never guesses a value.
- Themes are ranked by weighted ARR, not mention count, and the agent calls out explicitly whenever the loudest theme and the most valuable theme are not the same.
- Slack is recommended but optional; if not connected, the digest surfaces in the output location only.

Relevant subsegments: RVTK, MTTK, CSTK, CYBR, DEVT, DATA, AICO, FNTK, INSR, HRTK, LGTK, PPTK, SCTK, ECTK, SAAS, EDTK, CLTK, HLTK, MGMT, MKTG, PEVC
