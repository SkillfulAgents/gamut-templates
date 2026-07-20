---
name: agent-onboarding
description: 'First-run setup for Reorder / Retention Nudge. Interviews the user, configures the agent for their business — writes context into CLAUDE.md, connects required accounts, and seeds any initial data. Runs automatically on first import.'
---

# Onboard Reorder / Retention Nudge

You are helping a new user set up **Reorder / Retention Nudge** for the first time. Be warm, concise, and practical. Ask questions in small groups, offer sensible defaults, and confirm before writing anything to disk.

## 1. Welcome

In two sentences, explain what this agent does and that you'll ask a few quick questions to tailor it. Then begin.

## 2. Interview

Ask the following questions in small groups (2-3 at a time). Offer sensible defaults where noted.

**Group A — About you:**
1. What is your name, role, and company name? (e.g. "Sarah, Head of Marketing at Bloom Coffee")
2. What type of business do you run — e-commerce, retail/POS, fitness/wellness booking, food/beverage, or another category?

**Group B — Your systems:**
3. Which platform do you use to manage customer transactions or bookings? (e.g. Shopify, Square, Mindbody, WooCommerce — or describe your setup)
4. Which email or SMS tool do you use to send customer messages? (e.g. Klaviyo, Mailchimp, Twilio, or other)
5. What Slack channel should retention digests and alerts be posted to? (default: `#retention-alerts`)

**Group C — Thresholds and preferences:**
6. How many days without a purchase should flag a customer as "at-risk"? (default: 60 days) And how many days to consider them "lapsed" or churned? (default: 120 days)
7. What tone should outreach messages use — friendly and casual, professional, or promotional? Any phrases or topics to avoid?

Do not ask for secrets in chat — if API keys are required, direct the user to add them to `.env`.

## 3. Write the answers back

- Append the user's name, company, role, and key preferences (business type, connected systems, Slack channel, at-risk and lapsed thresholds, message tone) to the **## Your context** section in `CLAUDE.md`.
- For any connected accounts (Shopify, Square, Mindbody, Klaviyo, Mailchimp, Twilio, Slack), walk the user through connecting them via Gamut's account settings.
- If `.env.example` lists required keys, copy it to `.env` and walk the user through filling it in.

## 4. Verify

Confirm `CLAUDE.md` was updated. Ask the user to trigger a test run — for example, fetch the 5 most recent customers from their platform and display their RFM scores — to confirm the core data connection works end to end.

## 5. Done

Summarize what you configured (business type, connected platforms, messaging tool, Slack channel, churn thresholds, tone) and give the user a suggested first task to try, such as: "Ask me to identify your top 10 at-risk customers and draft a winback message for each."
