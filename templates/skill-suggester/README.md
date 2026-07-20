> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/productivity-internal-ops/skill-suggester)** — one-click deploy, no setup.

# Skill Suggester

> Finds the manual work you keep repeating and turns it into automated skills.

## What it does

Every week, Skill Suggester scans your Slack channels, CRM activity, and recent agent sessions for
workflows you've done by hand more than once. It posts a ranked list of skills worth automating to a
channel you choose. You reply with the ones you want, and the agent builds them and saves them to your
skill library.

## What you'll need

- **Accounts:** Slack, and a CRM (Salesforce, HubSpot, Pipedrive, or similar).
- **API keys:** none by default (accounts connect via OAuth). See `.env.example` if your CRM needs a key.
- **Other:** a Slack channel you actually check at the start of the week.

## Getting started

1. Import this template into Gamut (drag the zip into the agent import dialog, or install it from the marketplace).
2. On import, a setup session starts automatically. The **agent-onboarding** skill will ask you:
   - Which Slack channels and which CRM to scan
   - Where to post the weekly list, and your repeat threshold / lookback window
   - What counts as "repeated" for you (your methodology), and your schedule
3. Once setup finishes, give it its first task, e.g.: *"Run your weekly scan over the last 2 days and show me whatever you find."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's role and method (scan → rank → post → build).
- `.claude/skills/agent-onboarding/` — the first-run setup interview.
- `.env.example` — environment variables, if your CRM requires a key.

## Notes

- **No suggestions but you know there's repeated work?** Your repeat threshold is likely too high — drop it to 2 for the first month.
- **Suggestions feel generic?** Your `pattern_guidance` is too abstract — rewrite it with specific examples of what you actually do.
- **Same suggestions every week?** The agent has no memory of dismissed items across runs — build them or add them to your exclude keywords.
- The agent only suggests skills that don't already exist in your library, and asks for build details before writing any code.
