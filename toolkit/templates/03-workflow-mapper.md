# Workflow Mapper

> Use this to document how work actually flows through a team. Copy this into a Google Sheet for sorting and filtering. The conditional formatting rules at the bottom will highlight your quick wins automatically.

---

## Instructions

1. Copy the table below into a Google Sheet
2. Fill in one row per step in the workflow you're mapping
3. Score Pain Level (1-5) and Automation Potential (low/med/high)
4. Sort by Pain Level descending to find the biggest friction points
5. Filter for "high" Automation Potential to find quick wins
6. **Quick wins = high pain + high automation potential**

---

## Workflow Map

**Workflow name:**
**Team:**
**Date mapped:**
**Mapped by:**
**Source:** (who described this workflow — name and role)

| Step # | Step Name | Who Does It | Tool/System Used | Input (what triggers this step) | Output (what this step produces) | Time Per Occurrence | Frequency | Pain Level (1-5) | Automation Potential | Notes |
|:-------|:----------|:-----------|:----------------|:-------------------------------|:--------------------------------|:-------------------|:----------|:-----------------|:--------------------|:------|
| 1 | | | | | | | daily / weekly / per request | | low / med / high | |
| 2 | | | | | | | | | | |
| 3 | | | | | | | | | | |
| 4 | | | | | | | | | | |
| 5 | | | | | | | | | | |
| 6 | | | | | | | | | | |
| 7 | | | | | | | | | | |
| 8 | | | | | | | | | | |

---

## Scoring Guide

### Pain Level (1-5)

| Score | Meaning |
|:------|:--------|
| 1 | Works fine, minor inconvenience at most |
| 2 | A little annoying but manageable |
| 3 | Noticeable friction — people complain about this |
| 4 | Significant pain — causes delays, errors, or frustration regularly |
| 5 | Critical — breaks frequently, causes major rework, or blocks other work |

### Automation Potential

| Rating | Meaning |
|:-------|:--------|
| **Low** | Requires human judgment, creativity, or complex decision-making. Hard to automate. |
| **Med** | Partially automatable — some steps could be automated but others need a human. |
| **High** | Highly repetitive, rule-based, involves data transfer between systems. Perfect for automation. |

---

## Google Sheets Conditional Formatting Setup

After pasting into Google Sheets, add these rules to highlight opportunities:

1. **Select the Pain Level column**
   - Format > Conditional formatting
   - "Is greater than or equal to 4" → Background: light red
   - "Is equal to 5" → Background: red, bold text

2. **Select the Automation Potential column**
   - "Text is exactly 'high'" → Background: light green

3. **Quick win highlight** (optional, more advanced):
   - Select the entire row range
   - Custom formula: `=AND($I2>=4, $J2="high")` → Background: bright green
   - These are your top priorities — high pain AND high automation potential

---

## Summary (fill after mapping)

**Total steps in this workflow:** ___
**Steps with pain level 4-5:** ___
**Steps with high automation potential:** ___
**Quick wins (high pain + high automation):** ___

### Top 3 Opportunities

| Priority | Step | Why | Estimated Time Savings |
|:---------|:-----|:----|:----------------------|
| 1 | | | |
| 2 | | | |
| 3 | | | |

### Recommended First Build

**What:**
**Why:**
**Estimated effort:**
**Estimated impact:**
