> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/productivity-internal-ops/inbox-triage)** — one-click deploy, no setup.

# Inbox Triage

> Classifies incoming email, drafts replies in your voice, and posts a digest — nothing auto-sends.

## What it does

Inbox Triage runs every 30 minutes during work hours, reads new messages in your inbox, and applies a label to each one (Action needed, FYI, Schedule, Newsletter, Spam/promo — or your own categories). For messages that need a reply, it drafts a response in your voice and saves it to your drafts folder. At the end of each run it posts a single digest to Slack summarizing what was triaged, what was drafted, and what still needs your direct attention. You review and approve everything — nothing is ever sent automatically.

## What you'll need

- **Accounts:** Gmail or Outlook (required), Slack (recommended), CRM — Salesforce, HubSpot, Attio, Affinity, or similar (optional)
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** 2–3 sample emails you've written recently — these are what make the drafted replies sound like you, not a robot

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - Which email provider and CRM you use
   - What triage categories you want applied to your inbox
   - Whether to draft replies for all flagged messages, CRM contacts only, or not at all
   - Which senders or domains should never get a draft (board, legal, personal contacts, etc.)
   - Where to deliver the Slack digest
   - 2–3 real emails you've written, to establish your voice
3. Once setup finishes, give the agent its first task: "Triage the last 10 messages in my inbox but do not draft anything and do not apply labels — just show me how you'd classify each one and which you'd draft for."

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's instructions and your saved configuration.
- `.claude/skills/agent-onboarding/` — first-run setup interview.

## Notes

- **Nothing auto-sends.** Every draft is saved to your email drafts folder for your review. This is a hard rule the agent cannot override.
- **Voice samples matter.** The quality of the drafted replies depends almost entirely on the examples you provide during onboarding. Paste real, recent emails — casual ones work best.
- **CRM is optional** but improves draft quality by giving the agent sender context (company, role, last interaction).
- **Slack is recommended** but not required — if you skip it, the digest won't be delivered anywhere. You can connect it later by re-running onboarding.
- The default schedule is `*/30 9-18 * * 1-5` (every 30 minutes, 9am–6pm Mon–Fri, Eastern). Change the timezone and hours in Gamut's task settings to match your work hours.

Relevant subsegments: ALL
