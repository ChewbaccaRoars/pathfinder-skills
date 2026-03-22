# Solution Registry

> The master list of everything built across all Pathfinder tours. Copy this into a Google Sheet. This is the foundation for the Pathfinder Dashboard and pattern detection.

---

## Instructions

1. Copy the table into a Google Sheet
2. Add one row every time you build a solution on a tour
3. Update the Status and Reuse Count over time
4. This becomes your portfolio, your pattern detector, and your impact tracker

---

## Registry

| ID | Tour # | Team | Date Built | Solution Name | Type | Problem It Solves | Tech Used | Services/APIs | Time Saved (hrs/week) | People Impacted | Guide Link | Repo Link | Status | Adopted By (other teams) | Reuse Count | Tags |
|:---|:-------|:-----|:-----------|:-------------|:-----|:-----------------|:----------|:-------------|:---------------------|:---------------|:-----------|:----------|:-------|:------------------------|:-----------|:-----|
| 001 | | | | | dashboard / automation / agent / script / guide / workshop | | Apps Script / Python / Claude / other | | | | GitHub or GitLab URL | GitHub or GitLab URL | active / retired / superseded | | 0 | |
| 002 | | | | | | | | | | | | | | | | |
| 003 | | | | | | | | | | | | | | | | |

---

## Column Definitions

| Column | What to put |
|:-------|:-----------|
| **ID** | Sequential number (001, 002, etc.) |
| **Tour #** | Which tour this was built during |
| **Team** | The team you were embedded with |
| **Date Built** | When it was completed (YYYY-MM-DD) |
| **Solution Name** | Clear, descriptive name |
| **Type** | dashboard, automation, agent, script, guide, workshop |
| **Problem It Solves** | One sentence: what pain point this addresses |
| **Tech Used** | Apps Script, Python, Claude Code, HTML, etc. |
| **Services/APIs** | Gmail API, Sheets API, Slack webhook, ServiceNow, etc. |
| **Time Saved** | Estimated hours saved per week |
| **People Impacted** | How many people benefit |
| **Guide Link** | URL to the published guide |
| **Repo Link** | URL to the code repo |
| **Status** | active = in use, retired = no longer needed, superseded = replaced by newer solution |
| **Adopted By** | Names of other teams that adopted this solution |
| **Reuse Count** | Number of times this solution was reused by other teams |
| **Tags** | Keywords for searching: reporting, email, data-sync, dashboard, calendar, etc. |

---

## Summary View (auto-calculated in Google Sheets)

Add these formulas to a "Summary" tab:

```
Total solutions built:        =COUNTA(D2:D)
Active solutions:             =COUNTIF(N2:N, "active")
Total hours saved per week:   =SUM(J2:J)
Total hours saved per year:   =SUM(J2:J) * 52
Total people impacted:        =SUM(K2:K)
Total tours completed:        =MAX(B2:B)
Average solutions per tour:   =COUNTA(D2:D) / MAX(B2:B)
Reuse rate:                   =SUM(P2:P) / COUNTA(D2:D)
Most common type:             =INDEX(F2:F, MATCH(MAX(COUNTIF(F2:F, F2:F)), COUNTIF(F2:F, F2:F), 0))
```

---

## Pattern Detection

After 3+ tours, review the Tags and Problem columns. Look for:

- **Same problem across teams:** Multiple teams have the same pain point → build a reusable solution
- **Same tech stack:** Most solutions use the same tools → create templates and accelerators
- **Same type:** Lots of dashboards? Create a dashboard template. Lots of automations? Create an automation scaffold.
- **Declining time-to-build:** Are tours getting faster? That's the compounding effect.
