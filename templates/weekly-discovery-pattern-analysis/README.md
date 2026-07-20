> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/product-engineering/weekly-discovery-pattern-analysis)** — one-click deploy, no setup.

# Weekly Discovery Pattern Analysis

> Turns each week's discovery calls into evidence-based problem statements and the patterns worth acting on.

## What it does

Every week, this agent pulls your discovery calls from your call recorder, drafts a crisp problem
statement for each account built from what the prospect actually said, and reads across the calls to
surface recurring patterns — the language prospects use, the pains they volunteer, the competitors they
name. It posts the analysis to a channel you choose, ending with three actionable "So What" takeaways.
Useful for sharpening your content, prospecting POVs, and discovery approach.

## What you'll need

- **Accounts:** a call recorder (Gong, Chorus, Fireflies, Otter, or similar), a chat tool for delivery
  (e.g. Slack), and optionally a CRM (Salesforce, HubSpot, Pipedrive, …) for matching calls to accounts
  and filtering by stage.
- **API keys:** none by default (accounts connect via OAuth). See `.env.example` if a service needs a key.
- **Other:** the exact tag or call-type labels your recorder uses for discovery calls — getting these
  right is the single most important setup step.

## Getting started

1. Import this template into Gamut (drag the zip into the agent import dialog, or install it from the
   marketplace).
2. On import, a setup session starts automatically. The **agent-onboarding** skill will ask you:
   - Which call recorder and (optionally) CRM to scan
   - Which tags identify discovery calls, which stages to include, your lookback window and duration
     minimum
   - Your problem-statement style and which patterns matter most to you
   - Thresholds, output options, where to post, and your schedule
3. Once setup finishes, run the smoke test it offers: *"Pull the last discovery call in your system —
   just one. Show me the raw problem statement you'd draft and the quotes you'd use. Don't post yet."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill — especially
to refine your problem-statement style once you've seen real output.

## What's inside

- `CLAUDE.md` — the agent's role and method (pull → draft → analyze patterns → post), plus the exact
  output format.
- `.claude/skills/agent-onboarding/` — the first-run setup interview.
- `.env.example` — environment variables, if a connected service requires a key.

## Notes

- **Says "fewer than 2 discovery calls found" but you had calls?** Your call-type tags don't match how
  your recorder labels calls. Open the recorder and check the exact tag — it's case- and space-sensitive.
  Common mismatch: "Discovery" in your config, "Discovery Call" in the recorder.
- **Problem statements sound like marketing copy, not transcripts?** Your `problem_statement_style` is
  too abstract. Rewrite it with 2–3 concrete "good" examples and one "bad" one — the agent imitates
  whatever pattern you give it.
- **Patterns are surface-level (everyone wants growth) not specific?** Either you don't have enough calls
  per week (you need ~4+ for meaningful patterns) or your `pattern_focus_areas` are too broad. Narrow
  them to specific themes — "language prospects use to describe ramp time" beats "pain points."
- **Competitor mentions section never appears?** The agent may be missing soft mentions. Ask it to flag
  any competitor named OR described (e.g. "a CRM vendor" when context makes them identifiable).
- **"So What" reads like a summary, not insights?** The agent is defaulting to safe summarization. Push
  it: the takeaways must contain things you wouldn't get from skimming the patterns above. If they're
  just rephrased pattern names, the work isn't done.
