# Employee Burnout Analysis — BIS CN3031

> **Team:** Gh0st Sh3ll &nbsp;|&nbsp; **Module:** Business Information Systems (CN3031) &nbsp;|&nbsp; **University of East London** &nbsp;|&nbsp; **April 2026**


---

## 📁 Repository Contents

```
 BIS-Burnout-Analysis
 ├──  BIS.pbix                   # Power BI dashboard (3 pages)
 ├──  CN3031_proj.pdf            # LaTeX report (submitted via Overleaf)
 └──  README.md                  # This file
```

---

##  Project Overview

This project transforms the **Employee Burnout Analysis** dataset (22,750 records) into an executive-ready Power BI dashboard and business report. The analysis focuses on identifying the key drivers of employee burnout and translating them into actionable management recommendations.

**Dataset fields analysed:**

| Field | Type | Description |
|---|---|---|
| Employee ID | Identifier | Unique employee record key |
| Date of Joining | Date | Used for temporal slicing |
| Gender | Category | Demographic segmentation |
| Company Type | Category | Product vs Service comparison |
| WFH Setup Available | Category | Remote work support flag |
| Designation | Numeric (0–5) | Seniority level |
| Resource Allocation | Numeric (1–10) | Workload intensity score |
| Mental Fatigue Score | Numeric (0–10) | Self-reported fatigue level |
| Burn Rate | Numeric (0–1) | Burnout outcome measure |

---

##  Dashboard — `BIS.pbix`

The Power BI dashboard is structured across **3 pages**, each targeting a distinct audience question.

### Page 1 — Overview
Headline KPIs and top-line comparisons for executive consumption.

- 4 KPI Cards — Avg Burn Rate · Avg Mental Fatigue · High-Risk % · WFH Availability
- Stacked bar chart — Burn rate distribution by designation level
- Donut chart — Company type split (Service 65% / Product 35%)
- Line chart — Avg burn rate trend by join month
- Clustered bar — WFH vs No-WFH burn rate by gender

### Page 2 — Demographics
Workforce composition and data quality.

- Donut — Gender split (Female 52% / Male 48%)
- Column chart — Headcount by designation level
- Table — Missing data summary (Burn Rate 4.9% · Fatigue 9.3% · Resource 6.1%)

### Page 3 — Burnout Drivers
Deep-dive into the causal factors behind burnout.

- Scatter plot — Mental fatigue score vs burn rate (r = 0.9445)
- Heatmap matrix — Designation × Resource Allocation, coloured by avg burn rate
- Box-whisker chart — Burn rate spread per designation level
- Gauge — Burnout index (0–1 scale, target ≤ 0.30)

**Slicers on every page:** Gender · Company Type · WFH Status · Designation · Date of Joining

---

##  Report — `CN3031_proj.pdf`

The written report was authored in LaTeX via Overleaf and exported as PDF. It covers:

1. **Dataset Description** — field definitions and dataset profile
2. **Data Cleaning (ETL)** — Power Query M transformation steps
3. **Data Modeling & DAX** — star-schema structure and all DAX measures
4. **Dashboard & Business Insights** — visual walkthroughs and key findings
5. **Conclusion & Recommendations** — 4 actionable management recommendations

---

##  Key Findings

### 1 · Burnout escalates sharply with seniority
Average burn rate climbs from **0.151** at Level 0 to **0.857** at Level 5 — a **5.7× increase**. Senior and specialised roles are the highest-risk group and should be treated as a priority for intervention, not assumed to be more resilient.

### 2 · WFH support is measurably protective
Employees with WFH availability average a burn rate of **0.396** versus **0.518** for those without — a **24% reduction in risk**. Expanding remote-work eligibility is the highest-leverage, lowest-cost policy lever available.

### 3 · Mental fatigue is the dominant leading indicator
Mental fatigue score and burn rate correlate at **r = 0.9445** — the strongest signal in the dataset. Monitoring fatigue monthly gives management an early-warning window before burnout becomes a retention crisis.

### 4 · Company type is not the key differentiator
Product and Service employees show nearly identical burn rates (0.451 vs 0.453), so improvement efforts should focus on **work design, fatigue management, and flexibility** rather than business model.

---

##  Recommendations

| # | Action | Impact |
|---|---|---|
| 1 | **Workload audit for Level 4–5 staff** — structured review within 30 days | Directly targets the highest-risk segment |
| 2 | **Expand WFH eligibility** to the remaining 46% of staff | Data-backed 24% average burn rate reduction |
| 3 | **Track mental fatigue as a leading KPI** — quarterly survey, team-level reporting | Gives HR a 90-day early-warning window |
| 4 | **Use dashboard slicers for segment-level action** — HR and operations can slice by role, WFH, gender | Moves from reporting to intervention |

---

##  DAX Measures Used

```dax
Avg Burn Rate       = AVERAGE('in'[Burn Rate])
Avg Mental Fatigue  = AVERAGEX(FILTER('in', NOT ISBLANK('in'[Mental Fatigue Score])), 'in'[Mental Fatigue Score])
High Burnout %      = DIVIDE(CALCULATE(COUNTROWS('in'), 'in'[Burn Rate] > 0.70), COUNTROWS('in'))
WFH Availability %  = DIVIDE(CALCULATE(COUNTROWS('in'), 'in'[WFH Setup Available] = "Yes"), COUNTROWS('in'))

-- Calculated column
Burn Level          = IF('in'[Burn Rate] < 0.3, "Low", IF('in'[Burn Rate] <= 0.7, "Mid", "High"))
```

---

##  How to Open the Dashboard

1. Install **Power BI Desktop** (free) from [powerbi.microsoft.com](https://powerbi.microsoft.com/desktop)
2. Clone or download this repository
3. Open `BIS.pbix` in Power BI Desktop
4. If prompted about data source paths, update the Excel file path under **Home → Transform Data → Data Source Settings**

> **Note:** The dataset (`employee_burnout_analysis-AI.xlsx`) is not included in this repository due to file size. Ensure you have the original file locally and update the data source path accordingly.

---

##  Dataset Profile

| Metric | Value |
|---|---|
| Total records | 22,750 |
| Average burn rate | 0.452 |
| Average mental fatigue score | 5.73 |
| Employees with burn rate > 0.70 | 2,198 (9.66%) |
| Employees with WFH support | 12,290 (54.02%) |
| Female employees | 11,908 (52.3%) |
| Male employees | 10,842 (47.7%) |
| Service company records | 14,833 (65.2%) |
| Product company records | 7,917 (34.8%) |
| Missing — Mental Fatigue Score | 2,117 (9.3%) |
| Missing — Burn Rate | 1,124 (4.9%) |
| Missing — Resource Allocation | 1,381 (6.1%) |

---

<div align="center">

**BIS CN3031 &nbsp;·&nbsp; Gh0st Sh3ll &nbsp;·&nbsp; University of East London &nbsp;·&nbsp; April 2026**

</div>

