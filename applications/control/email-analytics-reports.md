# Email Analytics (Reports)

**Email Analytics** provides an account-wide view of email performance across all campaigns. It helps you understand deliverability, engagement, and patterns like the best time/day to send, audience device/email client breakdowns, geographic distribution, and bounce-rate anomalies.

### How to access Email Analytics

1. In the left-hand menu, click **Reports**
2. You’ll land on **Campaign Overview**
3. Click the **Email Analytics** tab (next to Campaign Overview)

### What you’ll see in Email Analytics

#### 1) Summary metrics (top cards)

These cards summarize performance across all campaigns:

| Metric                | Description                                                                                                 |
| --------------------- | ----------------------------------------------------------------------------------------------------------- |
| **Total Delivered**   | Total emails successfully delivered and the number of unique recipients.                                    |
| **Unique Opens**      | Number of distinct recipients who opened at least once, plus the open rate.                                 |
| **Unique Clicks**     | Number of distinct recipients who clicked at least once, plus the click rate.                               |
| **Unique Replies**    | The total number of unique recipients who replied to an email. The percentage shows the overall reply rate. |
| **Unsubscribes**      | Total unsubscribe events.                                                                                   |
| **Spam Complaints**   | Total spam complaint events (if supported by the sending/tracking system).                                  |
| **Countries Reached** | Number of countries detected from tracking/location signals.                                                |
| **Bot Open %**        | Portion of opens flagged as automated (security scanners, link prefetching, etc.).                          |

> Tip: If **Spam Complaints** are elevated, address deliverability first before optimizing opens/clicks.

#### 2) Best Time to Send (UTC)

A chart showing which **hour(s)** tend to produce the highest open rates, displayed in **UTC**.

Use this to:

* Choose sending windows that historically perform best
* Compare performance across time blocks (morning vs afternoon vs evening)

> Note: This chart is in **UTC**. If your team operates in a different timezone, convert the peak hours accordingly.

#### 3) Best Day to Send

A chart showing which **day(s) of the week** produce the best open rates.

Use this to:

* Identify the strongest day to schedule key outreach
* Avoid days that consistently underperform

#### 4) Email Client Types

Breakdown of what email clients recipients use to open emails, such as:

* Browser-based opens
* Mobile clients
* Unknown/other

This is useful for:

* Understanding where your audience reads email most often
* Diagnosing tracking differences (some clients block or limit tracking)

#### 5) Device Breakdown

Shows devices used to open emails, typically:

* **Desktop**
* **Mobile**
* **Unknown**

Use this to:

* Validate whether your campaigns should be optimized primarily for mobile or desktop
* Inform content layout and CTA placement (mobile-first vs desktop-first)

#### 6) Daily Activity (All Time)

A time-series chart showing activity trends over time, commonly including:

* **Delivered**
* **Opened**
* **Failed**

Use this to:

* Spot spikes and dips in sending volume
* See whether engagement rises when volume rises
* Identify days with unusually high failures

#### 7) Geographic Breakdown

Displays where recipients are opening from (country distribution).

This helps with:

* Segmenting by region
* Scheduling sends by geography/timezone
* Understanding where your engaged audience is concentrated

> Note: Geography depends on available tracking signals and can be incomplete due to VPNs, privacy features, or security tooling.

#### 8) Bounce Rate Spikes

A highlighted section that flags campaigns/subjects with **abnormally high bounce rates**, typically including:

* Subject / campaign
* Delivered
* Failures
* Bounce rate
* First sent date

Use this to quickly investigate deliverability issues such as:

* Poor list quality (invalid addresses)
* Domain blocks or reputation issues
* Misconfigured sender/domain authentication (where applicable)

Recommended actions:

* Review the recipient list source for those sends
* Validate sender/domain settings and suppression lists
* Consider pausing high-bounce sequences until resolved

#### 9) All Campaign Performance

A table summarizing per-subject (or per-campaign) metrics such as:

* **Delivered**
* **Opens**
* **Clicks**
* **Failures**
* **Unsubs**
* **Open %**
* **Bounce %**

Use this to:

* Compare performance across campaigns/subjects at a glance
* Identify top-performing and underperforming outreach patterns
* Prioritize which subject lines or sequences to iterate on

### How to use Email Analytics to improve performance

#### Improve deliverability first

If **Bounce Rate Spikes** or **Spam Complaints** are high:

* Clean your lists (remove invalid/old contacts)
* Review sending patterns and audience targeting
* Investigate domain-specific issues via failures and domain patterns (if available elsewhere)

#### Improve engagement (opens & clicks)

If delivered is healthy but opens/clicks are low:

* Use **Best Time to Send** and **Best Day to Send** to choose better send windows
* Test subject lines and first lines
* Ensure CTAs are clear and early, especially if **mobile** dominates the Device Breakdown

#### Interpret “Bot Open %” carefully

If **Bot Open %** is high:

* Treat opens as directional, not definitive
* Use clicks (and downstream conversions) as stronger intent signals

### FAQ

**Is Email Analytics mission-specific?**\
No. Email Analytics aggregates performance **across all campaigns** for the account.

**Why is “Best Time to Send” shown in UTC?**\
To provide a consistent reference timezone across reporting. Convert peak hours into your local timezone for scheduling.

**Why might country/device/client data be incomplete?**\
Some email clients and security tools limit tracking or mask location/device details (privacy features, VPNs, scanners).
