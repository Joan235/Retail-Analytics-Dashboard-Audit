# Retail Analytics Dashboard Audit

Auditing a flawed management dashboard, correcting the underlying data, and rebuilding a reliable version in Excel.

## Overview

A retail business had already built a dashboard and drawn a set of conclusions from its transaction data. This project independently reviewed that dashboard against the raw data, identified the data-quality issues undermining it, corrected them, and rebuilt a dashboard that can actually be trusted for decision-making.

## Business Problem

Management had received a dashboard reporting ₦47.5M in revenue and ₦16.6M in profit, with conclusions including "Abuja is the most profitable market" and "Electronics should receive more budget." These conclusions were about to inform real investment decisions — but the dashboard had never been independently checked against the raw data it was built from.

## Objectives

- Review the raw transaction dataset for data-quality issues
- Determine which of management's 8 stated conclusions actually hold up
- Correct the data and rebuild a reliable dashboard
- Recommend concrete next steps based on the corrected evidence

## Tools

- Microsoft Excel — data cleaning, formulas (VLOOKUP, IF, ISBLANK, TRIM, PROPER)
- PivotTables & PivotCharts
- Slicers (interactive filtering)
- Excel dashboard design

## Data Preparation

Four issues were found in the raw dataset (432 transactions) and corrected:

| Issue | Found | Fix |
|---|---|---|
| Duplicate transactions | 12 Transaction_IDs appeared twice with identical data | Removed duplicates - 432 → 420 rows |
| Inconsistent text labels | "Lagos" had 3 spelling variants; "Accessories" had 4 | Standardized casing/whitespace, merged into single labels |
| Missing cost data | 31 of 432 rows had no Cost_Per_Unit_NGN - dashboard had silently treated these as ₦0 | Imputed missing cost from each product's known fixed cost |
| Unreliable revenue field | 22 of 432 rows didn't match Units × Price × (1 − Discount) | Recalculated revenue for all rows from the formula |

## Analysis

Each of management's 8 original conclusions was tested against the corrected data:

| # | Claim | Verdict |
|---|---|---|
| 1 | Abuja is the most profitable market | **Incorrect** |
| 2 | Electronics is strongest — give it more budget | **Misleading** |
| 3 | Higher discounting improves profitability | **Incorrect** |
| 4 | Online has the lowest return rate | **Incorrect** |
| 5 | August is the strongest sales month | **Incorrect** |
| 6 | Lagos is underperforming | **Incorrect** |
| 7 | The reported Revenue field is usable directly | **Incorrect** |
| 8 | Dashboard is reliable without further cleaning | **Incorrect** |

A corrected Excel dashboard was built with KPI cards, PivotTable-driven charts (market, category, monthly trend, return rate by channel), comparison tables mirroring the original dashboard's layout, and interactive slicers (State, Category, Channel, Month).

<img width="1218" height="882" alt="dashboard-screenshot" src="https://github.com/user-attachments/assets/d3cafcca-29b4-4ced-b9c6-eaf03a6bd291" />

## Key Findings

- **Profit was overstated by ~₦2M.** The dashboard's reported profit (₦16.6M) only reconciles if 31 transactions with missing cost data were treated as ₦0 cost. Corrected profit: **₦14.59M**.
- **Lagos, not Abuja, is the top market.** Splitting Lagos's data across 3 label variants made it look like several small, weak markets instead of one strong one. Corrected profit by state: Lagos ₦4.58M (highest) → Abuja ₦1.70M (lowest).
- **Electronics drives revenue, not margin.** Electronics has the highest revenue (₦29.3M) but the lowest margin (30.6%); Accessories has far less revenue but the highest margin (46.8%).
- **Discounting hurts margin, not helps it.** Margin falls from 40.6% (0% discount) to 23.4% (25% discount) - the opposite of management's claim.
- **August is the weakest month, not the strongest.** Corrected revenue: August ₦3.17M (lowest) vs. May ₦7.01M (highest).

## Business Recommendations

1. **Prioritize Lagos** for continued investment - it is the actual top-performing market, not Abuja.
2. **Cap or review discounts above 15–20%**, since margin erodes sharply beyond that point.
3. **Fix data collection at the source** - enforce standardized dropdowns for state/category, require cost entry for every product, and add a duplicate-transaction check before the next reporting cycle.

---

*This project was completed as part of the Data Science Nigeria (DSN) AI Bootcamp 2026 — Data Analytics Track assessment.*
