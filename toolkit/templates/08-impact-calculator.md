# Impact Calculator

> Use this BEFORE building to estimate whether the solution is worth the effort. Copy into a Google Sheet for auto-calculation. Use the same sheet AFTER building to compare estimates vs. actuals.

---

## Instructions

1. Fill in the "Current State" section based on your observations during Week 1-2
2. Fill in the "Estimated Future State" based on what you plan to build
3. The calculator shows the projected impact
4. After building, fill in the "Actual Results" section and compare
5. Use the output in your impact report and tour retrospective

---

## Solution Info

| Field | Value |
|:------|:------|
| **Solution name** | |
| **Tour #** | |
| **Team** | |
| **Date estimated** | |
| **Problem being solved** | |

---

## Current State (Before)

*Capture these numbers by observing the team or asking them directly.*

| Metric | Value | How you measured it |
|:-------|:------|:-------------------|
| **Time per occurrence** | ___ minutes | Observed / self-reported / timed |
| **Frequency** | ___ times per day / week / month | |
| **People involved** | ___ people | |
| **Error rate** | ___ errors per ___ occurrences | Estimated / tracked |
| **Rework time per error** | ___ minutes | |

### Calculated Current Cost

*Use these formulas in Google Sheets:*

```
Weekly time cost:
= (Time per occurrence) x (Frequency per week) x (People involved)
= ___ minutes/week

Monthly time cost:
= Weekly time cost x 4.33
= ___ minutes/month → ___ hours/month

Annual time cost:
= Weekly time cost x 52
= ___ minutes/year → ___ hours/year

Annual error cost:
= (Error rate per week) x 52 x (Rework time per error)
= ___ hours/year

Total annual cost (time):
= Annual time cost + Annual error cost
= ___ hours/year
```

---

## Estimated Future State (After Automation)

*What do you expect after building the solution?*

| Metric | Estimated Value | Rationale |
|:-------|:---------------|:----------|
| **Time per occurrence** | ___ minutes | |
| **Frequency** | ___ (same, or reduced if process changes) | |
| **People involved** | ___ (same, or reduced) | |
| **Error rate** | ___ | |
| **Rework time per error** | ___ minutes | |

### Projected Savings

```
Weekly time saved:
= (Current weekly cost) - (Estimated weekly cost)
= ___ minutes/week

Annual time saved:
= Weekly time saved x 52
= ___ hours/year

Annual error reduction:
= (Current error cost) - (Estimated error cost)
= ___ hours/year

Total annual savings:
= Annual time saved + Annual error reduction
= ___ hours/year
```

---

## Build Effort

| Factor | Estimate |
|:-------|:---------|
| **Estimated build time** | ___ hours |
| **Estimated documentation time** | ___ hours |
| **Estimated training time** | ___ hours |
| **Total effort** | ___ hours |

### ROI Calculation

```
Payback period:
= Total effort / (Weekly time saved / 40 hours)
= ___ weeks until the investment pays for itself

First-year ROI:
= (Total annual savings - Total effort) / Total effort x 100
= ___% return

Break-even point:
= Total effort / (Weekly time saved in hours)
= ___ weeks
```

---

## Decision Framework

| Annual Savings | Build Effort | Verdict |
|:--------------|:-------------|:--------|
| > 100 hours | < 10 hours | **Build immediately** — massive ROI |
| 50-100 hours | < 10 hours | **Build it** — strong ROI |
| 20-50 hours | < 5 hours | **Build it** — good ROI, quick win |
| 20-50 hours | > 10 hours | **Consider it** — decent ROI but meaningful effort |
| < 20 hours | < 2 hours | **Build it** — low effort makes it worthwhile |
| < 20 hours | > 5 hours | **Skip it** — effort may not justify the savings |
| Any | Any | **Always consider:** non-time benefits (error reduction, consistency, morale, learning) |

---

## Actual Results (fill after building)

*Compare estimates vs. reality. This builds your calibration over time.*

| Metric | Estimated | Actual | Difference |
|:-------|:----------|:-------|:-----------|
| Time per occurrence (after) | | | |
| Error rate (after) | | | |
| Weekly time saved | | | |
| Annual time saved | | | |
| Build time | | | |
| Documentation time | | | |
| Training time | | | |

### Estimation Accuracy

```
Time savings accuracy:
= Actual annual savings / Estimated annual savings x 100
= ___% (over 100% = you underestimated the impact — good problem to have)

Build effort accuracy:
= Actual build time / Estimated build time x 100
= ___% (under 100% = you built faster than expected)
```

*Track this across tours. Your estimates will get more accurate over time.*

---

## Non-Time Impact (qualitative)

Don't forget to capture impact that's hard to quantify:

- [ ] **Consistency:** Output is now consistent every time (no human variation)
- [ ] **Morale:** Team members no longer dread this task
- [ ] **Scalability:** Process can now handle 10x the volume without more people
- [ ] **Risk reduction:** Single point of failure removed (tribal knowledge documented)
- [ ] **Speed:** Turnaround time dramatically reduced
- [ ] **Visibility:** Leadership can now see data they couldn't before
- [ ] **Reusability:** Solution can be adopted by other teams
- [ ] **Learning:** Team learned new skills during the build

---

## One-Line Summary for Impact Report

*Fill in the blanks:*

> We automated [process name] for [team name], saving approximately **[X] hours per week** ([Y] hours per year) and reducing errors by **[Z]%**. The solution took **[N] hours** to build, paying for itself in **[W] weeks**.
