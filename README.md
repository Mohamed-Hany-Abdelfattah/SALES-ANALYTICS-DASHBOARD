# Sales Analytics Dashboard (2022–2025)

An **interactive Excel sales performance dashboard** that turns 720 transactions
into live KPIs, drill-down filters, YoY growth analysis, and a currency toggle —
all driven by pure formulas and data validation, with **zero macros**.

![Dashboard Preview](dashboard-preview.png)

---

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Data Overview](#data-overview)
- [Key Performance Indicators](#key-performance-indicators)
- [Dashboard Walkthrough](#dashboard-walkthrough)
- [The Calc Engine](#the-calc-engine)
- [How It Works](#how-it-works)
- [Business Insights](#business-insights)
- [Getting Started](#getting-started)
- [Project Files](#project-files)
- [Built With](#built-with)
- [Possible Next Steps](#possible-next-steps)

---

## Overview

This workbook is a complete BI-style reporting solution built entirely in Excel.
A raw transaction table feeds a **read-only formula engine** (`Calc`), which in
turn powers a formatted, interactive report (`Dashboard`). Selecting any filter
instantly recalculates every KPI and chart — no refresh, no macros, no add-ins.

The current default view (Year = **2024**) shows:

- **4,914,196 EGP** total revenue at a **38% profit margin**
- **+48.7%** year-over-year growth vs 2023
- Best month (**December**) and top performers highlighted automatically

### Why this project is useful

- Shows how to build a **macro-free interactive dashboard** in Excel for non-technical teams
- Demonstrates a clean 3-layer architecture: `Data` → `Calc` → `Dashboard`
- Every KPI, ranking, and chart is **fully reusable** for any future dataset

---

## Key Features

- **8 interactive filters** — Year, Quarter, Month, Region, Category, Salesperson, Product
- **Active Filters bar** — always shows exactly what's applied
- **Dynamic KPI cards** — Revenue, Profit, Margin, Orders, Units, Avg Order Value, and more
- **YoY growth engine** — compares the selected year vs the previous year automatically
- **Growth % target + Projected Revenue** — scenario what-if modelling (0–100%)
- **Currency toggle** — instant EGP ↔ USD view
- **On/Off Target overlay** — compare actuals against targets
- **7 live charts** — trends, breakdowns, rankings, and a heatmap matrix
- **Rankings** — Top 10 / Bottom 5 products, top salespeople, best category

---

## Data Overview

| Dimension | Values |
|---|---|
| Time span | 2022 – 2025 (4 years) |
| Regions | North, South, East, West, Central |
| Categories | Electronics, Furniture, Clothing, Sports, Grocery |
| Products | 25 SKUs |
| Salespeople | 6 |
| Transactions | 720 records (180 / year, 15 / month) |
| Schema | Date, Year, Quarter, Month Num, Month, Region, Category, Product, Salesperson, Units, Unit Price, Revenue, Cost, Profit |

---

## Key Performance Indicators

All KPI cards update live. Default view = **Year 2024**:

| KPI | Value |
|---|---|
| Total Revenue | 4,914,196 EGP |
| Total Cost | 3,046,802 EGP |
| Total Profit | 1,867,395 EGP |
| Profit Margin | 38% |
| Cost Ratio | 62% |
| Total Orders | 180 |
| Total Units | 3,831 |
| Avg Order Value | 27,301 EGP |
| Avg Profit / Order | 10,374 EGP |
| YoY Growth (2024 vs 2023) | +48.7% |
| Best Month | December |
| Peak Month Revenue | 931,832 EGP |
| Best Category | Electronics (49.6% revenue share) |
| Top Salesperson | Mona Adel (27.2% revenue share) |
| Projected Revenue | 7,862,714 EGP |

Full 4-year dataset: **Revenue 14,974,642 EGP · Profit 5,689,164 EGP**.

---

## Dashboard Walkthrough

The `Dashboard` sheet is organized into clear zones:

1. **Header** — title, subtitle, "last updated" timestamp, and a shortcut to the `Calc` sheet.
2. **Filter Strip** — the dropdown controls that drive the whole report.
3. **Active Filters** — a human-readable sentence summarizing every applied filter.
4. **KPI Cards** — 12 headline metrics + highlight cards (Best Category, Top Salesperson, Projected Revenue).
5. **Charts** — revenue trend, quarterly distribution, regional share, category breakdown, top/bottom product rankings, and the Region × Category heatmap.

---

## The Calc Engine

`Calc` is the formula backbone. It mirrors your filter selections and pre-computes
every aggregation the dashboard needs (17 sections):

| # | Section | Purpose |
|---|---|---|
| 1 | Current Selections | Mirrors dashboard controls (engine + readable) |
| 2 | Dropdown List Sources | Feeds all in-cell dropdowns |
| 3 | Monthly Totals | Revenue / orders / units / cost by month |
| 4 | Quarter Totals | Revenue / orders / units / profit by quarter |
| 5 | Region Totals | Revenue, orders, units and revenue share % |
| 6 | Category Totals | Revenue, profit, margin % and share % |
| 7 | Salesperson Totals | Revenue, orders, units and share % |
| 8 | Product Totals | All 25 SKUs with margin % |
| 8b | Top 10 Products | Auto-ranked by revenue |
| 9 | Year Totals | Yearly revenue / profit for YoY comparison |
| 10 | Region × Category Matrix | Revenue cross-tab — heatmap source |
| 11 | Currency View | EGP ↔ USD output |
| 12 | Growth % Values | 0–100 (step 5) dropdown list |
| 13 | KPI Helpers | YoY growth engine (latest vs previous year) |
| 14 | Bottom 5 Products | Auto-ranked by revenue |
| 15 | Top 5 by Profit | Highest absolute profit |
| 16 | Year Compare | Latest vs previous year with Δ% |
| 17 | Extra Order Metrics | Avg orders/month, units/order, best quarter, etc. |

---

## How It Works

```
┌─────────────┐     ┌──────────────┐     ┌──────────────────┐
│   Data      │ ──▶ │     Calc     │ ──▶ │    Dashboard     │
│  raw facts  │     │  aggregation │     │   KPIs + charts  │
└─────────────┘     └──────────────┘     └──────────────────┘
        ▲                                      │
        └────────── filter selections ◀────────┘
```

1. You pick a filter on the `Dashboard` (data-validation dropdown).
2. `Calc` reads that choice in *Current Selections*.
3. Every aggregation (`SUMIFS`-style formulas, INDEX/MATCH lookups) recalculates.
4. KPI cards and charts read straight from `Calc` and update instantly.
5. No macros, no pivot refresh, no external connections.

---

## Business Insights

- **Seasonality:** December is the strongest month (931,832 EGP); Q4 drives **28%** of annual revenue.
- **Category concentration:** Electronics = ~**50%** of all revenue — key to protect.
- **Salespeople:** Mona Adel leads with **27.2%** share; the bottom two reps (Nour Ibrahim, Omar Mostafa) together trail her alone.
- **Quality of growth:** 2024 grew **+48.7%** YoY while holding a consistent **38%** margin.
- **Regional mix:** South (29%) and West (22%) are the top regions; North (13%) is the smallest.

| Region | Revenue Share |
|---|---|
| South | 29.2% |
| West | 22.0% |
| Central | 18.6% |
| East | 17.0% |
| North | 13.1% |

---

## Getting Started

1. Open `Sales Analytics Dashboard - FINAL.xlsx` in Microsoft Excel (desktop or web).
2. Use the dropdowns in the filter strip on the `Dashboard` sheet.
3. Watch every KPI and chart recalculate instantly.
4. Switch `Currency` (EGP/USD) or set a `Growth %` target to re-baseline projections.
5. Open `Calc` to inspect or extend the formula engine.

> Compatible with Excel 2016+ and Excel for the web. No macro security prompts required.

---

## Project Files

| File | Description |
|---|---|
| `Sales Analytics Dashboard - FINAL.xlsx` | The complete interactive dashboard workbook |
| `dashboard-preview.png` | Static preview of the dashboard |
| `README.md` | This documentation |

---

## Built With

- **Microsoft Excel** — SUMIFS / INDEX-MATCH / XLOOKUP-style aggregation, data validation, named ranges
- **Conditional formatting** — heatmap for the Region × Category matrix
- **Charts & dashboard layout** — Excel chart objects and design styling

---

## Possible Next Steps

- Connect the raw data to Power Query for automated refreshes
- Export the top-K charts to PowerPoint or a weekly email report
- Build a small Python (openpyxl/Pandas) script to regenerate the dataset
- Add benchmarks, targets per region, or a 12-month rolling forecast