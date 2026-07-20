> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/productivity-internal-ops/company-brain)** — one-click deploy, no setup.

# Company Brain

> Answers questions about your company from your real docs — with a link to every source, and an honest "I don't know" when the answer isn't written down.

## What it does

Someone asks "what's our refund policy?" or "where's the latest security questionnaire?" and Company
Brain retrieves the answer from your connected knowledge sources — Notion, Drive, Slack history,
whatever you connect — synthesizes it, and replies with a direct link to every source it used. When
the sources don't actually cover the question, it says so and tags your escalation contact instead of
guessing. Once a week it sweeps the knowledge base and reports what's going stale, what people keep
asking that isn't documented, and where two sources contradict each other.

## What you'll need

- **Accounts:** Slack (where questions come in and answers go out), plus at least one knowledge source — Notion or Google Drive. Web Search is optional, for clearly public facts your internal sources don't cover.
- **API keys:** none by default (accounts connect via OAuth). See `.env.example` if a source needs a key.
- **Other:** a channel your team will actually post questions in, and a sense of which source wins when two disagree.

## Getting started

1. Import this template into Gamut (drag the zip into the agent import dialog, or install it from the marketplace).
2. On import, a setup session starts automatically. The **agent-onboarding** skill will ask you:
   - The channel to watch for questions, and your knowledge sources (the specific folders/wikis, not the whole Drive)
   - Source priority (which source wins a conflict), your answer voice, and your confidence rules (when to answer vs. abstain)
   - Your escalation contact, out-of-scope topics, and the weekly sweep's channel, threshold, and schedule
3. Once setup finishes, give it its first task, e.g.: *"Someone just asked what our PTO policy is — answer it with sources."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's role and method (answer on demand → sweep weekly) and its exact output format.
- `knowledge-store.json` — the list of sources the agent may read. Ships empty; onboarding seeds it.
- `.claude/skills/agent-onboarding/` — the first-run setup interview.
- `.env.example` — environment variables, if a source requires a key.

## Notes

- **It answers but never cites anything.** Citation style isn't set, or the source returned no linkable location. Confirm it's `inline-links` or `footnotes`, and that the source actually exposes document links — a raw text dump with no URLs can't be cited.
- **It confidently answers things that aren't written down.** Your confidence rules are too loose. Make abstention the default: with no directly supporting source, the only acceptable response is "I don't have a source for this" plus an escalation tag. Add a worked example of a question it should refuse.
- **It quotes an old deck over the current policy page.** Your source priority isn't specific enough. Name the canonical home for the contested topic explicitly ("the wiki wins for policy; the deck is never authoritative for pricing"). The agent follows the list literally — rank every source you connect.
- **The weekly sweep flags everything as stale.** Your freshness threshold is too short, or a source exposes no real last-updated date. Raise it to 9–12 months, and exclude sources with no modified date the agent can read rather than flagging them every week.
- **It read something from a private/HR channel it shouldn't have.** That source wasn't excluded. Add the channel or folder to your out-of-scope list — it only avoids what's named there. Out-of-scope is an exclusion list, not an inference.
- **Answers are correct but read like a robot.** Your answer style is too generic. Rewrite it with a concrete voice instruction and an example of a good answer.
