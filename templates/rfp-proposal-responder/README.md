> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/bid-proposal-drafter/rfp-proposal-responder)** — one-click deploy, no setup.

# RFP / Proposal Responder

> Turns an inbound RFP, bid, RFQ, grant, or CIM into a first-pass proposal drafted from your firm's past proposals, IP, bios, and case studies — with a missing-info checklist.

## What it does

RFP / Proposal Responder activates when a new RFP, bid, RFQ, grant application, or CIM arrives. It parses the requirements, searches your proposal library for the best-matching past proposals, case studies, bios, and boilerplate, assembles a first-pass response section by section, and produces a missing-info checklist showing exactly what the team needs to supply before submission. Flags content that's over 18 months old and pricing sections always left blank — the agent never invents past performance or credentials.

Serves the widest range of organizations: consulting, marketing agencies, construction, AEC, law firms, investment banking, nonprofits, hospitality, logistics, and manufacturing — anyone who responds to formal competitive bids.

## What you'll need

- **Accounts:** Proposal library storage (Google Drive, SharePoint, or Notion), output storage for draft proposals, Slack or email for notifications
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** A well-organized proposal library with past proposals, case studies, team bios, and boilerplate sections

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - Your organization name and types of proposals you respond to
   - Where your proposal library lives
   - Whether you have a standard proposal template
   - Content age threshold and minimum lead time before deadline
   - Where to save drafts and send notifications
3. Once setup finishes, give the agent its first task: `"Draft a response for [organization] RFP — [attach or describe the RFP]"`

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's instructions.
- `.claude/skills/agent-onboarding/` — first-run setup interview.

## Notes

- Drafts only — this agent never submits, emails, or uploads to a procurement portal.
- Pricing sections are always left as explicit placeholders — the agent never invents numbers.
- Every piece of library content used is cited by source file so reviewers can verify.

Relevant subsegments: RVTK, MTTK, CSTK, CYBR, DEVT, DATA, AICO, FNTK, INSR, HRTK, LGTK, PPTK, SCTK, ECTK, SAAS, EDTK, CLTK, HLTK, MGMT, MKTG, PRCM, GCON, SUBC, CLEN, AEC, LAWF, IBMA, HOSP, LGST, MFGR, NGO
