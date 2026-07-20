---
name: agent-onboarding
---

Welcome to the Retail (Multi-Location) - Review & Reputation Replies agent. I will walk you through setup so the agent knows your locations, systems, voice, and routing preferences before it starts monitoring reviews.

This should take about 10 minutes. Your answers will be saved to config.json and written into the agent's context so you do not have to repeat them.

Let's get started.

**Question 1 - Your locations**
List each retail location you want to monitor. For each one, provide: the store name (as it appears on Google/Yelp), the city and state, and a short internal nickname (e.g., "Austin-Domain", "Chicago-Lincoln"). If you have more than 10 locations, you can paste a list or describe a pattern.

**Question 2 - Review platforms and credentials**
For each location, confirm which review platforms are active:
- Google Business Profile: do you have API access via a service account, or will you be connecting via OAuth? Provide the location IDs or listing names if known.
- Yelp: do you have a Yelp Fusion API key and Business Owner access for reply posting?

**Question 3 - Point-of-sale system per location**
For each location (or group of locations), which POS system is in use - Lightspeed or Shopify POS? If mixed, note which locations use which. Provide the API credentials or store identifiers for each system so the agent can look up transaction and product records when a review references a specific purchase.

**Question 4 - Location manager routing**
For each location, who is the assigned manager who should receive complaint escalations (1-2 star reviews and flagged complaints)? Provide their name, email, and preferred notification channel (email, Slack, or SMS). If multiple locations share a manager, note that.

**Question 5 - Voice profiles**
Describe the tone and voice for your brand's public replies. You can set one global voice or customize per location. For each, note:
- Formality level: formal, semi-formal, or casual
- Any regional phrasing or personality to include
- Preferred sign-off: manager's name, "The [Store Name] Team", or generic
- Any phrases or topics to avoid in public replies

**Question 6 - Rating alert threshold**
At what rolling 30-day average star rating should the agent flag a location as requiring immediate attention in the weekly digest? (Common choices: below 3.5 or below 4.0.)

**Question 7 - Weekly digest delivery**
Who should receive the weekly rating digest, and how? Provide email addresses and/or Slack channels. What day and time should it be sent (include timezone)?

**Question 8 - Auto-post preference**
Should approved replies be posted automatically once marked approved, or do you want a final manual confirmation step before each reply goes live? Note this per platform if your preference differs between Google and Yelp.

---

## After collecting answers

Once you have the answers to the questions above, do the following:

**1. Write config.json**

Save the configuration to `.claude/config.json` using this structure:

```json
{
  "locations": [
    {
      "nickname": "Austin-Domain",
      "displayName": "Store Name as on Google/Yelp",
      "city": "Austin",
      "state": "TX",
      "googleLocationId": "GOOGLE_LOCATION_ID",
      "yelpBusinessId": "YELP_BUSINESS_ID",
      "pos": "lightspeed",
      "posStoreId": "LIGHTSPEED_STORE_ID",
      "manager": {
        "name": "Manager Name",
        "email": "manager@example.com",
        "notificationChannel": "email"
      },
      "voice": {
        "formality": "semi-formal",
        "regionalNotes": "",
        "signOff": "The [Store Name] Team",
        "avoidPhrases": []
      }
    }
  ],
  "globalVoice": {
    "formality": "semi-formal",
    "signOff": "The Team",
    "avoidPhrases": []
  },
  "reviewPlatforms": {
    "google": {
      "authMethod": "service_account",
      "credentialsPath": ".claude/credentials/google-service-account.json"
    },
    "yelp": {
      "apiKey": "YELP_API_KEY"
    }
  },
  "alertThreshold": {
    "rollingAvgBelow": 3.5,
    "windowDays": 30
  },
  "weeklyDigest": {
    "recipients": ["email@example.com"],
    "slackChannels": [],
    "dayOfWeek": "Monday",
    "timeLocal": "08:00",
    "timezone": "America/Chicago"
  },
  "replyApproval": {
    "autoPostOnApproval": false,
    "staleDraftAlertHours": 48
  }
}
```

Add one object to the `locations` array for each location. Set `pos` to `"lightspeed"` or `"shopify_pos"` depending on the system for that location.

**2. Update CLAUDE.md**

Update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-English summary covering:
- How many locations are configured and their nicknames
- Which POS system(s) are in use and for which locations
- The global brand voice and any location-specific overrides
- The rating alert threshold
- Who receives weekly digests and when
- Whether auto-post is enabled and on which platforms

**3. Confirm setup and suggest a first task**

Tell the user: "Setup is complete. Your [N] locations are configured and ready for monitoring."

Then suggest a first task, for example:

"Pull all unaddressed reviews from the past 7 days across all locations and draft replies for each one, starting with the lowest-rated reviews first."
