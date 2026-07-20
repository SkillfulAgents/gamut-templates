> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/sales-pipeline/stale-deal-alert)** — one-click deploy, no setup.

# Stale Deal Alert

> Catches open deals going dark before they die quietly, and tells you how to revive them.

## What it does

Every weekday morning, Stale Deal Alert checks your CRM for open deals with no activity in 7+ days,
tiers them by urgency (🟡 Watch, 🟠 Needs Attention, 🔴 Critical), and posts an alert to a Slack channel
you choose. Each deal optionally comes with a one-line, tailored re-engagement move so you know exactly
what to do next.

## What you'll need

- **Accounts:** a CRM (Salesforce, HubSpot, Pipedrive, or similar), and Slack.
- **API keys:** none by default (accounts connect via OAuth). See `.env.example` if your CRM needs a key.
- **Other:** your CRM's exact pipeline stage names (copy/paste from your CRM), and a Slack channel you
  check first thing.

## Getting started

1. Import this template into Gamut (drag the zip into the agent import dialog, or install it from the
   marketplace).
2. On import, a setup session starts automatically. The **agent-onboarding** skill will ask you:
   - Which CRM, and which stages to monitor vs. always skip (exact names matter)
   - Your deal filters (staleness threshold, minimum value, whose deals to watch)
   - Your urgency tiers, delivery channel, and whether to tag owners / suggest actions
   - Your re-engagement style (so suggestions sound like you), and your schedule
3. Once setup finishes, run the smoke test it offers, e.g.: *"Run your stale deal check at a 1-day
   threshold and just show me the raw list here — don't post to Slack."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's role and method (query → filter → tier → suggest → post).
- `.claude/skills/agent-onboarding/` — the first-run setup interview.
- `.env.example` — environment variables, if your CRM requires a key.

## Notes

- **No alert but you have stale deals?** Your `active_stages` likely don't match your CRM exactly —
  capitalization and trailing spaces (e.g. "Discovery " vs "Discovery") break the match. Copy/paste the
  stage names straight from your CRM.
- **Missing deals you'd expect to see?** The deal's owner field may not match what `owner_filter: "me"`
  resolves to. Make sure your CRM identifies you with the same email/username you used to connect.
- **Suggestions feel generic?** Your `reengagement_style` needs more specifics — add 2–3 concrete
  examples of recent outreach that worked and why.
- **Owners not being @mentioned even with `tag_owner` on?** Slack handles aren't resolving from CRM
  emails. Either align deal-owner emails with their Slack emails, or accept the plain-name fallback and
  check your Slack workspace's email-visibility setting.
- **Deals flagged Critical that you just touched?** Your CRM may not log certain activity types as
  "last activity" — emails sent from the CRM compose UI usually log; replies from your inbox often
  don't. Check the deal's activity timeline in the CRM directly.
