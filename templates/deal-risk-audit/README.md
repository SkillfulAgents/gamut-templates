> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/sales-pipeline/deal-risk-audit)** — one-click deploy, no setup.

# Deal Risk Audit

> Reads your open deals and their call recordings every week, scores discovery, and tells you exactly what's missing — before it costs you the deal.

## What it does

Every week, Deal Risk Audit pulls your open deals from your CRM, reads the recent call recordings for
each one, and scores every deal against *your* discovery methodology. Deals with thin or missing
discovery get flagged with the specific gap and a concrete suggested fix. It posts a ranked audit
(Red → Yellow → Green) to a chat channel you choose, so you start the week knowing which deals need work
and what to do about them.

## What you'll need

- **Accounts:** a CRM (Salesforce, HubSpot, Pipedrive, or similar), a call recorder (Gong, Chorus,
  Fireflies, Otter, …), and a chat workspace to post to.
- **API keys:** none by default (accounts connect via OAuth). See `.env.example` if one of your systems
  needs a key.
- **Other:** your exact CRM stage names, and 4–6 discovery criteria that reflect how you actually
  qualify deals.

## Getting started

1. Import this template into Gamut (drag the zip into the agent import dialog, or install it from the marketplace).
2. On import, a setup session starts automatically. The **agent-onboarding** skill will ask you:
   - Which CRM and call recorder to use, and which deal stages to audit (and skip)
   - Your **discovery criteria** — the core of the agent: what "good discovery" means for you, and what
     evidence confirms each one
   - Your risk thresholds, where to post, and your schedule
3. Once setup finishes, give it its first task, e.g.: *"Pick one deal from my pipeline and run the full discovery audit on it — show me the evidence behind every score."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's role and method (pull deals → read calls → score → post).
- `.claude/skills/agent-onboarding/` — the first-run setup interview.
- `.env.example` — environment variables, if one of your systems requires a key.

## Notes

- **Deals flagged "no call recordings" but you know there are calls?** Either the call recorder isn't
  returning transcripts via the integration (check permissions), or the company name in your CRM doesn't
  match how the recorder tags calls (CRM "Acme Corp" vs. Gong "Acme").
- **Everything shows as 🔴 Red?** Your `risk_thresholds` are likely too aggressive — if green is set
  higher than the number of criteria you defined, no deal can ever go green. Align the thresholds with
  your criteria count.
- **Suggested actions feel generic ("follow up with champion")?** The `discovery_criteria` do the heavy
  lifting — each criterion's `evidence_needed` should be specific enough that missing evidence implies a
  clear question to ask. Vague criteria produce vague suggestions.
- **The same deal is flagged Red every week with no progress?** That's working as intended — it means the
  suggestions aren't being actioned. Consider a behavior rule to escalate deals that stay Red for 3+
  weeks.
- **Audit takes a long time to run?** Tighten `active_stages` or raise `min_deal_value` — each deal
  requires reading 1–3 full transcripts, which is the bottleneck.
