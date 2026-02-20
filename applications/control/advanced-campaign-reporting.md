# Advanced Campaign Report

The Campaign Report gives you a performance overview of a mission’s email campaign—delivery, opens, clicks, bounces, and engagement breakdowns so you can quickly understand what happened and what to improve next.

### How to open the Campaign Report

1. Go to Missions
2. Click a mission **name** to open it
3. In the top-right corner, click **Campaign Report**

This opens a dashboard-style report with summary metrics, insights, charts, and breakdown tables.

### What you’ll see in the report

#### 1) Summary metrics (top cards)

These cards give a quick snapshot of campaign performance:

<table data-header-hidden><thead><tr><th width="211.48046875">Metric</th><th>Description</th></tr></thead><tbody><tr><td>Delivered</td><td>The total number of emails that were successfully delivered to the recipients’ inboxes. Often also shows unique recipients (how many distinct people received the email).</td></tr><tr><td>Total Opens</td><td>The total number of times your emails were opened by recipients. This includes multiple opens by the same recipient.</td></tr><tr><td>Unique Opens</td><td>The number of unique recipients who opened your email at least once.</td></tr><tr><td>Open Rate</td><td>The percentage of unique opens relative to the number of delivered emails. Typically calculated as: Unique Opens ÷ Delivered × 100</td></tr><tr><td>Clicks</td><td>The total number of clicks on the links within your emails. Often includes unique clickers (distinct recipients who clicked at least once).</td></tr><tr><td>Bounces / Failures</td><td>The number of emails that could not be delivered to the recipients’ inboxes (hard/soft bounces depending on the provider).</td></tr><tr><td>Countries Reached</td><td>The number of different countries where your emails were opened (based on available tracking/location data).</td></tr><tr><td>Recipient Domains</td><td>The number of unique email domains to which the emails were sent (e.g., gmail.com, company.com).</td></tr><tr><td>Bot Opens</td><td>The percentage of opens that are suspected to be from bots. Useful to avoid overestimating real human engagement.</td></tr></tbody></table>

#### 2) Key Insights (summary box)

This section highlights important takeaways in plain language, such as:

* **Delivery rate** (e.g., “100% delivered, 0 failed”)
* **Open rate** and whether it suggests improvement opportunities
* **Repeat engagement** (e.g., “Openers averaged X opens each”)

Use this section as a quick “health check” before drilling into the charts/tables.

#### 3) Daily Activity (chart)

A bar chart showing campaign activity over time, typically by day:

* **Delivered** – how many emails were delivered that day
* **Opened** – how many open events occurred
* **Clicked** – how many click events occurred

This helps you spot:

* Which day(s) performance peaked
* Whether engagement happened immediately or over multiple days
* Whether clicks happened without opens (can indicate link scanning or certain email client behaviors)

#### 4) Top Recipient Domains (table)

A breakdown of results by email domain (e.g., gmail.com, company.com), typically including:

* **Delivered**
* **Opened**
* **Failed**

This is useful for diagnosing deliverability or engagement patterns by domain:

* If a domain shows high **failed**, it can indicate domain-specific blocking or invalid addresses.
* If delivered is fine but opens/clicks are low, content or targeting may need improvement.

#### 5) Most Common Email Subjects (table)

Shows which subject lines appeared most in the campaign and how frequently they were used.Common uses:

* Validate which subject lines were used the most (especially if A/B testing or personalization is involved)
* Identify whether certain subject styles correlate with better opens/clicks (compare with engagement metrics)

### How to use Campaign Report to improve results

Here are the most common workflows:

#### Improve deliverability

* If **Bounces/Failures** > 0:
  * Review list quality (invalid/old emails)
  * Verify sender configuration (SPF/DKIM/DMARC if applicable)
  * Avoid spam-trigger formatting (overuse of links, aggressive wording, etc.)

#### Improve opens

* If **Open Rate** is low:
  * Test shorter, clearer subject lines
  * Personalize the opening line and subject where appropriate
  * Try sending at a different time/day and watch the **Daily Activity** chart

#### Improve clicks

* If opens exist but **Clicks** are low:
  * Make the CTA clearer and earlier in the email
  * Reduce competing links
  * Ensure the CTA is relevant to the recipient segment

#### Watch out for bot activity

* If **Bot Opens** is high:
  * Treat open rate with caution
  * Use **Clicks** and replies/conversions as stronger signals of intent

### Notes & troubleshooting

#### “0 opens” or “0% open rate” even though people say they opened

Possible causes:

* Image blocking or privacy features in the recipient’s email client
* Open tracking disabled or blocked by security tools
* The email was read in a way that didn’t trigger the tracking pixelIn these cases, **Clicks** can be a more reliable engagement signal than opens.

#### High clicks but low opens

This can happen when:

* Security scanners automatically follow links
* Email clients prefetch links

Check **Bot Opens** and overall behavior across domains for hints.

### FAQ

1. **Do "Total Opens" and "Unique Opens" mean the same thing?**

No. Total Opens counts every open event (including multiple opens by the same recipient). Unique Opens counts how many distinct recipients opened at least once.



2. **What's the difference between "Clicks" and "Unique Clickers"?**

Clicks counts every click event (including multiple clicks by the same recipient). Unique Clickers counts how many distinct recipients clicked at least once.



3. **Why does domain/country data sometimes look incomplete?**

Domain and country reporting depends on the tracking data available from the recipient's email client and network. Privacy features, VPNs, and security tools can block or mask this data, so it may not always be captured.
