---
description: System Event Messages & Activity Log (Live Chat + Copilot)
---

# System & Muted Actions Visibility Matrix

Support for **muted system messages** has been extended within conversation transcripts for both **Live Chat** and **Copilot**. By incorporating a broader range of system events into the interface, tracking user actions and restoring activity logs is more transparent and efficient for administrative monitoring.

This page explains:

* What **general**, **muted**, and **system** events are
* Where each event appears (Transcript vs Activity Log)
* Who can see each event (End User vs Copilot User/Admin)



### Event types

* **General actions** — visible to all participants of the conversation (end users and admins) inside the transcript.
* **Muted actions** — visible only to admins inside the conversation transcript. These appear as muted/informational messages and are also logged in the Activity Log.
* **System actions** — occur automatically and cannot be manually triggered or reproduced by platform users. These are recorded in the Activity Log and typically do not appear as muted messages in the transcript.



### Legend

| Symbol | Meaning        |
| ------ | -------------- |
| ✅      | Visible        |
| ❌      | Not visible    |
| n/a    | Not applicable |

###

### Visibility matrix (Transcript vs Activity Log)

<table><thead><tr><th>Event Type</th><th>Action / Event</th><th width="113.296875" align="right">Live Chat (End User)</th><th width="120.58984375" align="right">Copilot (User)</th><th width="116.7578125" align="right">Copilot (Admin)</th><th align="right">Activity Log</th></tr></thead><tbody><tr><td>General</td><td>Conversation escalated</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td></tr><tr><td>General</td><td>Conversation under audit</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td></tr><tr><td>General</td><td>Mode changed: AI on/off</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td></tr><tr><td>General</td><td>Mode changed: AI off</td><td align="right">❌</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td></tr><tr><td>General</td><td>In-chat button clicked (e.g., Book a Demo)</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td></tr><tr><td>Muted</td><td>Document uploaded to agent memory</td><td align="right">n/a</td><td align="right">❌</td><td align="right">✅</td><td align="right">✅</td></tr><tr><td>Muted</td><td>Auto-archive triggered</td><td align="right">❌</td><td align="right">❌</td><td align="right">✅</td><td align="right">✅</td></tr><tr><td>General</td><td>Conversation archived manually</td><td align="right">n/a</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td></tr><tr><td>General</td><td>Transcript downloaded</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td></tr><tr><td>General</td><td>Conversation rated</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td></tr><tr><td>General</td><td>Conversation renamed manually</td><td align="right">n/a</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td></tr><tr><td>General</td><td>Conversation un-/favorited</td><td align="right">n/a</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td></tr><tr><td>Muted</td><td>Conversation state changed</td><td align="right">n/a</td><td align="right"><p>❌ / ✅</p><p>depending on copilot settings</p><p><br></p></td><td align="right">✅</td><td align="right">✅</td></tr><tr><td>Muted</td><td>Conversation re-/un-/assigned</td><td align="right">n/a</td><td align="right">n/a</td><td align="right">✅</td><td align="right">✅</td></tr><tr><td>General</td><td>Message feedback added/edited/deleted</td><td align="right">n/a</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td></tr><tr><td>System</td><td>Conversation started/ended</td><td align="right">n/a</td><td align="right">❌</td><td align="right">❌</td><td align="right">✅</td></tr><tr><td>System</td><td>Conversation automatically re-/named</td><td align="right">n/a</td><td align="right">❌</td><td align="right">❌</td><td align="right">✅</td></tr><tr><td>System</td><td>Conversation summary generated</td><td align="right">n/a</td><td align="right">❌</td><td align="right">❌</td><td align="right">✅</td></tr><tr><td>General</td><td>Conversation escalation resolved</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td><td align="right">✅</td></tr></tbody></table>

> Note: Events such as **button clicked** and **conversation state changed** are tracked and duplicated into the **Activity Log** for auditing and monitoring.
