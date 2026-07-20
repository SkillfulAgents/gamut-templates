> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/legal-compliance/contract-review-redline)** — one-click deploy, no setup.

# Contract Review & Redline

> Reviews inbound agreements and NDAs against your playbook, produces a clause-by-clause redline with fallback positions, and flags off-policy terms for counsel.

## What it does

Contract Review & Redline activates when an inbound contract, NDA, or agreement arrives. It compares each clause to your contract playbook, classifies every clause as accepted-as-is, needing a redline (preferred or fallback position), or off-policy (must escalate to counsel), produces the exact proposed language for every change, and delivers a structured redline summary the team can act on. Designed for in-house counsel, procurement, and any organization that reviews a steady stream of inbound contracts.

## What you'll need

- **Accounts:** Contract/playbook storage (Google Drive, SharePoint, Notion, or CLM like Ironclad), output storage for redline summaries, Slack or email for notifications
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** A written contract playbook with preferred positions, fallback positions, and off-policy terms for the contract types you review most often

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - Your role and the contract types you review
   - Where your contract playbook lives (or helps you build a starter playbook)
   - Your off-policy terms that are never acceptable
   - Your preferred governing law and jurisdiction
   - Who to escalate off-policy items to
   - Where to save redline summaries and send notifications
3. Once setup finishes, give the agent its first task: `"Review this [contract type] from [counterparty] — [attach or describe]"`

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's instructions.
- `.claude/skills/agent-onboarding/` — first-run setup interview.

## Notes

- Produces a draft redline only — the agent never sends, signs, or uploads the contract.
- Every proposed change cites the playbook section it's based on.
- Off-policy items always escalate to the designated legal owner — the agent never accepts a compromise position on them.
- The quality of redlines depends on the quality of your playbook — the more specific your preferred language, the more useful the output.

Relevant subsegments: RVTK, MTTK, CSTK, CYBR, DEVT, DATA, AICO, FNTK, INSR, HRTK, LGTK, PPTK, SCTK, ECTK, SAAS, EDTK, CLTK, HLTK, LAWF, MGMT, GCON, MFGR, WHSL, CRE, RDEV, IBMA, PEVC, ACCT
