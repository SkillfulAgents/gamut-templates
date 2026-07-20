> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/sales-pipeline/prospect-finder)** — one-click deploy, no setup.

# Prospect Finder

> Finds public buying signals each week and turns them into a short, COI-framed list of accounts worth a conversation.

## What it does

Every week, Prospect Finder searches recent news and public signals — leadership hires, funding events,
headcount expansion, missed targets, GTM pivots, competitive displacement, or whatever triggers you
define — for events that mean it's a good time to reach out to a new prospect. It cross-checks each
account against your CRM (skipping existing pipeline, customers, and recently contacted accounts), then
posts a short ranked list to a channel you choose. Each entry includes the specific signal, where it
was found, and a Cost-of-Inaction (COI) framed reason to act now.

## What you'll need

- **Accounts:** a CRM (Salesforce, HubSpot, Pipedrive, or similar), and Slack.
- **API keys:** none by default (accounts connect via OAuth). See `.env.example` if your CRM needs a key.
- **Web search:** platform-native, nothing to connect.
- **Other:** a Slack channel you actually check at the start of the week.

## Getting started

1. Import this template into Gamut (drag the zip into the agent import dialog, or install it from the marketplace).
2. On import, a setup session starts automatically. The **agent-onboarding** skill will ask you:
   - Your CRM, and your **ICP** (who you're targeting — be specific)
   - Your **buying signals** (the events that mean it's time to reach out) and your **COI framing**
   - Exclusion rules, search scope, where to post, and your schedule
3. Once setup finishes, give it its first task, e.g.: *"Run your prospect search for one signal type only — [your strongest signal] — and show me the raw results without filtering against the CRM."*

Setup takes about 30–45 minutes. The ICP, buying signals, and COI framing are the most important to
think through carefully — they're what make the output sharp and sound like you. You can re-run
onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's role and method (search → cross-reference CRM → rank → COI → post).
- `.claude/skills/agent-onboarding/` — the first-run setup interview.
- `.env.example` — environment variables, if your CRM requires a key.

## Notes

- **Search returns mostly old news?** Your `lookback_days` is too generous, or keyword matches are surfacing aged articles. Tighten it to 7 and make sure the agent verifies the article date matches the signal date.
- **Everything gets filtered out by CRM checks?** Your `exclude_recently_contacted_days` is too long, or your CRM has lots of brief "touched" records inflating contact history. Start at 60 days and adjust.
- **Signals feel vague** ("company is expanding" rather than "posted 8 AE roles")? Your `buying_signals` descriptions need to name exactly what to search for, not the abstract concept.
- **COI angles all sound the same?** Your `coi_framing` is too generic — add 2–3 worked examples (actual calculations or framings from past deals) so the agent has patterns to mimic.
- **Fewer than 3 accounts every week?** Your `icp` is too narrow or your signals are too rare — broaden the ICP or add 1–2 more signal types.
- The agent never pads the list with weak signals, never fabricates sources, and cites every signal.
