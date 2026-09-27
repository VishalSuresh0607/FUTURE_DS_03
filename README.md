# Marketing Funnel & Conversion Performance Analysis

A Power BI analysis of marketing funnel performance across regions, products, channels, and time, using impressions, clicks, conversions, spend, revenue, CTR, CPC, and ROI.

> **Context:** Final analytics task for the Future Interns project portfolio.

## What this project covers

The analysis follows the funnel from **impressions → clicks → conversions** and connects funnel activity to commercial outcomes through **spend, revenue, CTR, CPC, and ROI**.

The Power BI report includes KPI cards, slicers, channel and regional comparisons, revenue distribution by product, quarterly/region revenue trends, and a region × product conversion matrix.

## Repository structure

```text
marketing-funnel-conversion-analysis/
├── data/
│   ├── marketing_analytics_dataset.xlsx
│   └── README.md
├── dashboards/
│   ├── marketing_funnel_conversion_analysis.pbix
│   └── README.md
├── docs/
│   ├── analysis_insights.md
│   ├── dashboard_guide.md
│   ├── data_dictionary.md
│   └── data_quality.md
├── .gitignore
├── CHANGELOG.md
├── CONTRIBUTING.md
├── LICENSE
└── README.md
```

## Quick reference

| File | Purpose |
|---|---|
| `data/marketing_analytics_dataset.xlsx` | Source dataset used by the Power BI report. Contains 100 marketing observations in `Sheet1`. |
| `dashboards/marketing_funnel_conversion_analysis.pbix` | Final Power BI dashboard/report. Open in Power BI Desktop to interact with the visuals and slicers. |
| `docs/data_dictionary.md` | Field definitions, expected meaning, and metric formulas. |
| `docs/dashboard_guide.md` | Visual-by-visual dashboard documentation and interpretation guidance. |
| `docs/analysis_insights.md` | Key findings calculated from the provided dataset. |
| `docs/data_quality.md` | Validation results and important caveats for future extensions. |
| `CHANGELOG.md` | Repository version history. |

## How to view the dashboard

1. Install **Power BI Desktop**.
2. Open `dashboards/marketing_funnel_conversion_analysis.pbix`.
3. Use the **Date** and **Product** slicers to change the report context.
4. Review the KPI cards first, then use the channel, region, product, and time visuals for drill-down analysis.
5. Refer to `docs/dashboard_guide.md` for the exact aggregation used by each visual.

The PBIX already contains the report model needed for the dashboard; the Excel workbook is kept in the repository as the source-data reference.

## How to understand the Excel data

Open `data/marketing_analytics_dataset.xlsx` and inspect `Sheet1`.

The dataset has **100 rows and 13 columns** covering:

- Date
- Region
- Product
- Marketing channel
- Quarter
- Spend
- Impressions
- Clicks
- Conversions
- Revenue
- CTR
- CPC
- ROI

See `docs/data_dictionary.md` for the field-level definitions and formulas.

## Dashboard KPIs at dataset level

Using the same source values and aggregation logic documented in the PBIX:

| KPI | Dataset-level value | Dashboard logic |
|---|---:|---|
| Total Spend | 261,166.32 | SUM(Spend) |
| Total Impressions | 570,069 | SUM(Impressions) |
| Total Clicks | 55,973 | SUM(Clicks) |
| Total Conversions | 2,531 | SUM(Conversions) |
| Revenue | 1,042,479.69 | SUM(Revenue) |
| Avg CTR | 0.138638 (13.86%) | AVERAGE(CTR) |
| Average CPC | 6.5707 | AVERAGE(CPC) |
| Avg ROI | 4.476132 (447.61%) | AVERAGE(ROI) |

Two additional funnel rates are useful for interpretation but are **derived audit metrics, not dedicated dashboard cards**:

- Aggregate CTR = `Total Clicks / Total Impressions` = **9.82%**
- Click-to-conversion rate = `Total Conversions / Total Clicks` = **4.52%**

Because CTR, CPC, and ROI are stored as row-level fields and averaged by the report, these dashboard averages are not the same as weighted/aggregate rate calculations.

## Important interpretation notes

The source contains a `Quarter` column that does not consistently match the calendar quarter derived from `Date` (77 of 100 rows differ). The PBIX also uses **two different quarter concepts**: the area chart uses the Power BI **Date Hierarchy → Quarter**, while the spend waterfall uses the raw `Quarter` field. See `docs/data_quality.md` before extending the report.

The regional chart title mentions “Average of ROI,” but its ROI tooltip is configured as **SUM(ROI)**. The channel waterfall title also says “Revenue” while its Y-axis measure is **SUM(Spend)**. These are documented as report-definition notes rather than silently “corrected” in the repository.

## Prerequisites

- Power BI Desktop for the `.pbix` file
- Microsoft Excel or another `.xlsx`-compatible viewer for the source dataset
- Git (optional) for cloning/versioning the repository

No Python environment, package installation, or notebook is required to open or use the final dashboard.

## Suggested GitHub topics

`marketing-analytics` `funnel-analysis` `conversion-analysis` `power-bi` `data-analytics` `business-intelligence` `marketing-performance` `future-interns`

## Project status

**Version 1.0.0 — ready for portfolio/repository use.**

The repository preserves the provided Excel and PBIX assets and adds documentation needed to understand, review, and extend the analysis.
