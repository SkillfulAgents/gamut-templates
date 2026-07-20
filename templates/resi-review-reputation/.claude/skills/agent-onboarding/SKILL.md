---
name: agent-onboarding
---

Welcome to the Residential Real Estate - Review & Reputation Replies agent. I'll walk you through a quick setup so I can start monitoring your reviews and drafting replies in your voice right away.

I have a few questions. Take them one at a time or answer them all together - whichever is easier.

1. **Google Business Profile** - What is the Google Business Profile location ID or business name I should monitor for reviews? If you have multiple locations, list each one. If you don't use Google Business Profile, let me know and I'll skip it.

2. **Zillow and Realtor.com profiles** - What are the URLs or profile IDs for the agent's or team's Zillow and Realtor.com profiles? For example: `zillow.com/profile/your-name` or your Realtor.com agent ID. Skip any platforms you don't actively use.

3. **CRM setup** - Do you use Follow Up Boss, kvCORE, both, or neither? If you use one (or both), I'll need the API credentials or connection details so I can cross-reference reviews with contact records. Please share the API key or let me know if you'd prefer to set that up separately.

4. **Agent voice and tone** - Paste 2-3 examples of replies you've already written to reviews, or describe your preferred tone in a few sentences. For example: "I like to keep it warm but brief, always use the reviewer's first name, and sign off with my first name only." This is what I'll use to calibrate every reply I draft.

5. **Review approval workflow** - Should I auto-post approved replies, or do you want to review every draft before anything goes live? If you want a review step, who should receive the drafts and by what channel (email, Slack, etc.)?

6. **Service failure escalation** - Who should receive internal escalation notes when a review comes in at 2 stars or below? Please provide their name, role (e.g., broker, team lead), and preferred contact method (email address or Slack handle). You can also set a different star threshold if 2 stars isn't right for your team.

7. **Weekly digest** - Who should receive the weekly rating trend digest, on which day, and at what time? List names and email addresses. If you want the digest sent to a Slack channel instead, provide the channel name.

8. **Reply SLA** - How long should a review go unaddressed before I send an alert? The default is 48 hours. Let me know if you'd like a shorter or longer window.

## After collecting answers

Once you have the answers above, do the following:

**Write `config.json`** to the workspace root with this structure:

```json
{
  "platforms": {
    "google_business_profile": {
      "enabled": true,
      "location_ids": []
    },
    "zillow": {
      "enabled": true,
      "profile_urls": []
    },
    "realtor_com": {
      "enabled": true,
      "profile_ids": []
    }
  },
  "crm": {
    "follow_up_boss": {
      "enabled": false,
      "api_key": ""
    },
    "kvcore": {
      "enabled": false,
      "api_key": ""
    }
  },
  "reply_workflow": {
    "auto_post": false,
    "draft_delivery_channel": "email",
    "draft_recipients": []
  },
  "escalation": {
    "star_threshold": 2,
    "escalation_contact_name": "",
    "escalation_contact_email": "",
    "escalation_contact_slack": ""
  },
  "digest": {
    "enabled": true,
    "send_day": "Monday",
    "send_time": "08:00",
    "recipients": []
  },
  "sla": {
    "unaddressed_alert_hours": 48
  },
  "agent_voice": {
    "tone_summary": "",
    "sample_replies": []
  }
}
```

Fill in every field based on the answers collected. Set `enabled` to `false` for any platform or CRM the user skipped.

**Update `## Your context` in `CLAUDE.md`** with a plain-English paragraph summarizing: which platforms are monitored, which CRM(s) are connected, the agent's voice and tone, who receives escalations, who receives the weekly digest, the reply approval workflow, and the SLA window. This is what the agent reads at the start of every session to orient itself.

**Confirm setup and suggest a first task.** Tell the user setup is complete and suggest they start with:

"Pull all reviews from the last 7 days across [configured platforms] and draft replies for each one, then show me the queue."
