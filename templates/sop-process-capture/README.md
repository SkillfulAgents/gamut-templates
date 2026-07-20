> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/productivity-internal-ops/sop-process-capture)** — one-click deploy, no setup.

# SOP / Process Capture Drafter

> Turns a recorded or narrated process into a reviewed SOP or playbook, and flags drift from existing documentation.

## What it does

SOP / Process Capture Drafter turns any captured or recorded process — a call recording, screen narration, interview, or written walkthrough — into a clean, structured SOP. It extracts steps, formats them into your preferred template, and if you have existing docs, flags every place where current practice has drifted from what was documented before. Produces a draft with [VERIFY] markers where the source was ambiguous — so a human always reviews before publishing.

Works for any team standardizing repeatable work: operations, HR, sales, customer success, finance, or field services.

## What you'll need

- **Accounts:** Documentation storage (Google Drive, Notion, Confluence, or SharePoint), Slack or email for notifications
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** A recording, transcript, or written walkthrough of the process to document

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - Your role and the types of processes you document
   - Where your SOPs are stored
   - Your preferred SOP format (or use the standard template)
   - Whether to auto-detect drift from existing docs
   - Where to notify you when a draft is ready
3. Once setup finishes, give the agent its first task: `"Draft an SOP from this [transcript/recording/description]: [paste or attach]"`

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's instructions.
- `.claude/skills/agent-onboarding/` — first-run setup interview.

## Notes

- This agent drafts only — it never publishes or overwrites existing docs.
- Drift detection requires read access to your existing documentation storage.
- Any step the agent can't confidently extract is marked [VERIFY] so a human reviews it before the SOP is published.

Relevant subsegments: ALL
