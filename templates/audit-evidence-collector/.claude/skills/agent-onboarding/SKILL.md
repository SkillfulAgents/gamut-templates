---
name: agent-onboarding
description: 'First-run setup for Audit Evidence Collector. Interviews the user, configures the agent for their business — writes context into CLAUDE.md, connects required accounts, and seeds any initial data. Runs automatically on first import.'
---

# Onboard Audit Evidence Collector

You are helping a new user set up **Audit Evidence Collector** for the first time. Be warm, concise, and practical. Ask questions in small groups, offer sensible defaults, and confirm before writing anything to disk.

## 1. Welcome

In two sentences, explain that this agent automates evidence collection across compliance and infrastructure systems, maps controls to the audit framework, and flags gaps so audits are faster and less painful — and that you'll ask a few quick questions to tailor it to their environment. Then begin.

## 2. Interview

Ask the following questions in two or three small groups (not all at once). Wait for answers before continuing.

**Group 1 — About you and your audit**
1. What is your name, role, and company name? (e.g., "Sarah, Head of Security at Acme Corp")
2. Which compliance framework(s) are you preparing for? (e.g., SOC 2 Type II, ISO 27001, HIPAA, food safety / FSMA, PCI-DSS — list all that apply)
3. When does your next audit window open, and how often do you run audits? (e.g., "Annual SOC 2 starting September", "continuous readiness")

**Group 2 — Your systems**
4. Which compliance platform do you use — Vanta, Drata, Tugboat Logic, or something else? If none, say so.
5. Which identity provider manages your user access — Okta, Azure AD, or another? And which ticketing system do you use for remediation work — Jira, Linear, or another?
6. What tools do you use for MDM (device management) and vulnerability scanning? (e.g., Jamf + Snyk, Intune + Qualys — or "not yet set up")

**Group 3 — Preferences**
7. Where should the agent post gap alerts and audit summaries — which Slack channel? And where should the assembled evidence package be saved — Google Drive folder name/path or Confluence space?

Do not ask for secrets or API keys in chat. If any integration requires an API key, direct the user to `.env` after onboarding.

## 3. Write the answers back

- Append the user's name, company, role, target framework(s), audit cadence, connected systems, preferred Slack channel, and evidence package destination to the **## Your context** section in `CLAUDE.md`.
- For each connected account (compliance platform, IdP, ticketing, MDM, scanner, Drive/Confluence, Slack), walk the user through connecting it via Gamut's account settings if not already connected.
- If `.env.example` lists required API keys, copy it to `.env` and walk the user through filling in each key for their specific tools.

## 4. Verify

Confirm that `CLAUDE.md` was updated with the user's context. Then ask the user to trigger a test evidence pull — for example, "fetch the latest access review report from your IdP" — to confirm the core connection works end to end.

## 5. Done

Summarize in 3-4 bullet points what you configured (frameworks, systems connected, notification channel, package destination). Then suggest a first task, such as: "Run an evidence harvest for your SOC 2 CC6 access control domain and show me the gap report."
