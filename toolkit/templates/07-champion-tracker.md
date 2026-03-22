# Champion Network Tracker

> Copy this into a Google Sheet. Update it after every tour and during monthly check-ins. This is your growing network of builders across the organization.

---

## Instructions

1. Add one row per champion identified during a tour
2. Check in monthly — update confidence, support needs, and teaching status
3. Celebrate champions who start teaching others — they're multiplying your impact
4. Use the "Needs Support" column to prioritize where to spend between-tour time

---

## Champion Registry

| Name | Team | Tour # | Date Identified | What They Learned | What They Own (solution name) | Confidence (1-5) | Last Check-In | Needs Support? | Teaching Others? | Notes |
|:-----|:-----|:-------|:---------------|:-----------------|:----------------------------|:-----------------|:-------------|:--------------|:----------------|:------|
| | | | | | | | | Y / N | Y / N | |
| | | | | | | | | | | |
| | | | | | | | | | | |

---

## Column Definitions

| Column | What to put |
|:-------|:-----------|
| **Name** | Champion's name |
| **Team** | Their team |
| **Tour #** | Which tour you identified them on |
| **Date Identified** | When they became a champion (YYYY-MM-DD) |
| **What They Learned** | Key skills: Apps Script, APIs, dashboards, triggers, etc. |
| **What They Own** | The solution they're responsible for maintaining |
| **Confidence (1-5)** | How confident they are building/maintaining on their own. Update this monthly. |
| **Last Check-In** | Date of your last conversation with them (YYYY-MM-DD) |
| **Needs Support?** | Do they need help with something right now? |
| **Teaching Others?** | Are they training other people on their team? This is the multiplier signal. |
| **Notes** | Anything else — what they're struggling with, ideas they have, etc. |

---

## Confidence Scale

| Score | Meaning |
|:------|:--------|
| 1 | Needs significant support. Can't operate independently yet. |
| 2 | Can do basic tasks but gets stuck on anything new. |
| 3 | Comfortable with what was built. Can make small changes. Gets stuck on bigger modifications. |
| 4 | Confident. Can modify, extend, and debug most things independently. |
| 5 | Self-sufficient. Teaching others. Proposing new ideas. Could run a mini-tour themselves. |

---

## Monthly Check-In Template

*Use this as a quick Slack DM or 15-minute conversation.*

> Hey [name]! Quick Pathfinder check-in:
>
> 1. How's [solution name] going? Any issues?
> 2. Have you made any changes or improvements to it?
> 3. Has anyone else on the team started using or learning it?
> 4. Anything you need help with?
> 5. Any new pain points or automation ideas?

---

## Network Health Metrics

Add these to a "Summary" tab in the Google Sheet:

```
Total champions:                    =COUNTA(A2:A)
Average confidence:                 =AVERAGE(G2:G)
Champions at confidence 4-5:        =COUNTIFS(G2:G, ">=4")
Champions teaching others:          =COUNTIF(J2:J, "Y")
Champions needing support:          =COUNTIF(I2:I, "Y")
Overdue check-ins (30+ days):       =COUNTIFS(H2:H, "<" & TODAY()-30, H2:H, "<>")
Multiplier rate:                    =COUNTIF(J2:J, "Y") / COUNTA(A2:A)
```

**The multiplier rate is the key metric.** What percentage of your champions are now teaching others? That's your force multiplication in action.

---

## Triggers to Set Up

Consider building these automations (Apps Script):
- **Monthly reminder:** Auto-DM champions you haven't checked in with in 30+ days
- **Confidence trend:** Track confidence over time — are champions growing or stagnating?
- **Teaching alert:** When a champion marks "Teaching Others = Y" for the first time, celebrate it
