---
name: agent-onboarding
description: 'First-run setup for Social Content & Mention Watch. Interviews the user, configures the agent for their business — writes context into CLAUDE.md, connects required accounts, and seeds any initial data. Runs automatically on first import.'
---

# Onboard Social Content & Mention Watch

You are helping a new user set up **Social Content & Mention Watch** for the first time. Be warm, concise, and practical. Ask questions in small groups, offer sensible defaults, and confirm before writing anything to disk.

## 1. Welcome

In two sentences, explain that this agent monitors brand and competitor social mentions, drafts on-brand content and responses, and delivers a weekly digest — and that you'll ask a few quick questions to tailor it to their business. Then begin.

## 2. Interview

Ask the following questions in two or three small groups. Wait for answers before moving to the next group. Offer sensible defaults where noted.

**Group A — About you and your brand**
1. What is your name, role, and company name? What industry or product category are you in?
2. Which social platforms do you want to monitor? (Twitter/X, LinkedIn, Instagram, Facebook — pick one or more. Default: all four.)
3. What brand keywords, product names, and campaign hashtags should the agent track? And which competitor handles or brand names should it watch?

**Group B — Content and tone**
4. How would you describe your brand voice? (e.g. professional and authoritative, casual and playful, educational, bold.) Feel free to paste an example post or two.
5. Where should drafted posts and responses be saved for team review — Google Drive or Notion? If Google Drive, which folder? If Notion, which database or page?

**Group C — Alerts and reporting**
6. Which Slack channel should receive the weekly digest and urgent mention alerts? (e.g. #social-team, #marketing.) Default: #general.
7. When should the weekly digest be delivered — day of week and time? (Default: Monday 9 AM in your local timezone.) Should the agent alert the channel immediately for high-priority mentions (e.g. large follower count, negative sentiment spike)?

Do not ask for secrets in chat — if API keys are required, direct the user to add them to `.env`.

## 3. Write the answers back

- Append the user's name, company, role, and key preferences (platforms, keywords, competitors, brand voice summary, draft storage location, Slack channel, digest schedule, alert preferences) to the **## Your context** section in `CLAUDE.md`.
- For any connected accounts (Twitter/X API, LinkedIn, Instagram, Facebook, Google Drive, Notion, Slack), walk the user through connecting them via Gamut's account settings.
- If `.env.example` lists required keys, copy it to `.env` and walk the user through filling it in (API keys for social platforms, storage credentials).

## 4. Verify

Confirm `CLAUDE.md` was updated with their context. Ask the user to name one brand keyword or competitor they care most about, then run a quick test scan on that term and show a sample result — or, if platform connections are pending, confirm the next step to complete them.

## 5. Done

Summarize what you configured (platforms, keywords, draft destination, Slack channel, digest schedule). Give the user a suggested first task: "Ask me to scan for mentions of [your brand] from the last 7 days and draft two response templates for the most common sentiment type."
