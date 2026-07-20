> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/customer-success-support/support-ticket-triage)** — one-click deploy, no setup.

# Support Ticket Triage & Draft Reply

> Categorizes and prioritizes inbound support tickets, drafts KB-grounded replies for agent review, flags knowledge gaps, and compiles a weekly Voice-of-Customer summary.

## What it does

This agent watches your helpdesk for new tickets and, for each one, picks a category, sets a priority against your SLA, and drafts a reply that is grounded in your knowledge base, written in your support voice. The draft waits for an agent to review and send. When the knowledge base does not actually answer the question, the agent refuses to invent an answer and instead flags a KB gap so your team knows what content is missing. Once a week it rolls everything up into a Voice-of-Customer digest: ticket volume, top themes, category and priority mix, SLA performance, recurring KB gaps, and churn-risk tickets that need a human.

It works for SaaS support desks, consumer and retail support teams, fintech, healthcare, education, and any team running a high-volume inbox of customer questions through a helpdesk.

## What you'll need

- **Accounts:**
  - Helpdesk: Zendesk, Intercom, Freshdesk, Help Scout, or similar
  - Knowledge base: a help center, Notion, Confluence, Google Docs, Guru, or wherever your support articles live
  - Slack (for the weekly Voice-of-Customer digest and escalation alerts)
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** your category list and priority rules, your SLA targets, and 2-3 real replies from your team so the drafts sound like your support voice (not a generic bot)

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - Which helpdesk, knowledge base, and Slack channel to use
   - Your category taxonomy and how you set priority (and your SLA targets)
   - Your reply voice and any existing macros or saved replies
   - Which categories, if any, should auto-send vs. always draft for review
   - How escalations should route and which actions always need human approval
   - Where and how often to post the Voice-of-Customer digest
3. Once setup finishes, give the agent its first task: *"Pull the last 10 tickets but do NOT send anything and do NOT change any ticket. Show me how you'd categorize and prioritize each one, the draft reply you'd write, which KB article you'd ground it in, and any KB gaps you'd flag."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` - the agent's instructions and your configuration (written by onboarding).
- `.claude/skills/agent-onboarding/` - first-run setup interview.

## Notes

- Replies are drafts by default. Nothing auto-sends unless you explicitly opt a category in during onboarding, and even then the agent holds back on anything urgent, angry, ungrounded, or that makes a promise.
- Every drafted answer is grounded in your knowledge base and cites the article it used in an internal note. If the KB does not cover the question, the agent flags a gap instead of guessing.
- The agent never promises a refund, credit, discount, or date on its own. Those always get left as a draft and routed to a human.
- Slack is recommended but optional; if not connected, the Voice-of-Customer digest and escalation alerts can be delivered another way you choose during onboarding.
- This is a helpdesk/support workflow. It is distinct from general email inbox triage. It expects tickets, categories, a knowledge base, and SLAs.
- The KB-gap list compounds over time, so recurring gaps in the weekly digest tell you exactly which articles to write next.

Relevant subsegments: RVTK, MTTK, CSTK, CYBR, DEVT, DATA, AICO, FNTK, INSR, HRTK, LGTK, PPTK, SCTK, ECTK, SAAS, EDTK, CLTK, HLTK, DTC, CPG, RETL
