---
name: agent-onboarding
---

Welcome to the DTC Growth / Creative Test Loop agent. Setup takes about 5 minutes. I'll walk through a few questions one at a time to configure the agent for your brand, then write everything automatically so you are ready to run.

Let's start.

---

**Question 1 of 6 — Your brand**

What is your brand name, and how would you describe your business type?

Choose the closest fit: **DTC brand** / **CPG brand** / **marketplace seller** / **other** (if other, briefly describe).

---

<!-- Wait for answer, then ask Question 2 -->

**Question 2 of 6 — Ad platforms**

Let's confirm your connected ad platforms. Answer yes or no for each:

- Is **Meta Ads** connected to this workspace?
- Is **Google Ads** connected?
- Is **Amazon Seller Central** connected?

If any are not yet connected, no problem — you can add them later. Just confirm which ones are live now.

---

<!-- Wait for answer, then ask Question 3 -->

**Question 3 of 6 — E-commerce platform**

What e-commerce platform does your brand run on?

Options: **Shopify** / **WooCommerce** / **BigCommerce** / **Amazon-only** / **other** (specify).

---

<!-- Wait for answer, then ask Question 4 -->

**Question 4 of 6 — Winning KPI and threshold**

What is your primary winning KPI and the threshold a creative must cross to be flagged as a winner?

For example:
- ROAS > 3.0
- CTR > 2.5%
- CPA < $18

Please specify the metric, direction (> or <), and the number that works for your brand.

---

<!-- Wait for answer, then ask Question 5 -->

**Question 5 of 6 — Brief cadence and volume**

How often should the agent run its creative review cycle — **daily** or **weekly**? And what is the maximum number of new briefs it should queue per cycle?

Default is **weekly** with a max of **3 briefs**. Let me know if you want different settings.

---

<!-- Wait for answer, then ask Question 6 -->

**Question 6 of 6 — Slack channel**

What Slack channel should the agent use for the **creative brief queue** and the **weekly growth digest**?

You can use a single channel for both (e.g., `#growth-ops`) or separate ones (e.g., `#creative-queue` for briefs and a different channel for the weekly digest). Let me know what works for your team.

---

<!-- Wait for answer, then confirm before saving -->

After collecting all six answers, display a confirmation summary before writing anything:

---

Thanks — here is a summary of your configuration before I save it:

- **Brand:** [Brand name] ([Business type])
- **Ad platforms:** [Connected platforms, comma-separated]
- **E-commerce platform:** [Platform]
- **Winning KPI threshold:** [KPI] [direction] [threshold]
- **Brief cadence:** [daily/weekly], max [N] briefs per cycle
- **Creative ops Slack channel:** [#channel]
- **Digest Slack channel:** [#channel]
- **Inventory lookahead window:** 14 days (default — edit config.json to change)

Does this look right? Reply **yes** to save, or tell me what to correct.

---

<!-- Only after the user confirms, perform both writes below -->

## Writes to perform on confirmation

### 1. Update CLAUDE.md

Find the `## Your context` section in CLAUDE.md and replace the `<!-- Filled in during onboarding -->` placeholder line with the following block (substituting user's answers):

```
## Your context

- **Brand:** [Brand name] ([Business type])
- **Ad platforms:** [Connected platforms]
- **E-commerce platform:** [Platform]
- **Winning KPI threshold:** [KPI] [direction] [threshold]
- **Brief cadence:** [daily/weekly], max [N] briefs per cycle
- **Creative ops Slack channel:** [#channel]
- **Inventory lookahead window:** 14 days (default — edit config.json to change)
```

### 2. Write config.json

Write `config.json` to the workspace root with this exact schema, filled in from the user's answers:

```json
{
  "brand_name": "",
  "business_type": "",
  "ad_platforms": [],
  "ecommerce_platform": "",
  "winning_kpi": "",
  "winning_threshold": null,
  "brief_cadence": "weekly",
  "max_briefs_per_cycle": 3,
  "inventory_lookahead_days": 14,
  "creative_ops_slack_channel": "",
  "digest_slack_channel": ""
}
```

Field mapping:
- `brand_name` — brand name string from Q1
- `business_type` — one of `"dtc"`, `"cpg"`, `"marketplace_seller"`, or `"other"`
- `ad_platforms` — array of connected platforms from Q2, e.g. `["meta_ads", "google_ads", "amazon_seller_central"]`
- `ecommerce_platform` — from Q3, e.g. `"shopify"`, `"woocommerce"`, `"bigcommerce"`, `"amazon_only"`, or `"other"`
- `winning_kpi` — metric name from Q4, e.g. `"ROAS"`, `"CTR"`, `"CPA"`
- `winning_threshold` — numeric threshold from Q4 (number type, not string)
- `brief_cadence` — `"daily"` or `"weekly"` from Q5
- `max_briefs_per_cycle` — integer from Q5 (default 3)
- `inventory_lookahead_days` — 14 (keep default unless user specified otherwise)
- `creative_ops_slack_channel` — Slack channel name including `#` from Q6
- `digest_slack_channel` — Slack channel name including `#` from Q6 (same as `creative_ops_slack_channel` if user chose one channel for both)

---

## Closing message

After writing both files, confirm to the user that setup is complete, then kick off the first task:

"You are all set. Configuration saved to `config.json` and `CLAUDE.md` updated with your brand context.

Here is your first task prompt to get started:

**Pull last week's top-performing creatives from Meta and Google, mine reviews for the top 3 SKUs, and queue briefs for the best candidates.**

Paste that in whenever you are ready."
