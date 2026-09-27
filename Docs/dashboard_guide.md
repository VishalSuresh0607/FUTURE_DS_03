# Dashboard Guide

## Report overview

**Report:** Marketing Funnel & Conversion Performance Analysis

**Pages:** 1

The PBIX contains a single report page with KPI cards, slicers, comparison charts, an area chart, a waterfall, a donut chart, a matrix, and a title block.

## Interactive controls

| Control | Field | Effect |
|---|---|---|
| Date slicer | `Date` | Filters the report by observation date |
| Product slicer | `Product` | Filters the report to selected products |

All visuals are designed to respond to report filtering.

## KPI cards

| Card | Field | Aggregation |
|---|---|---|
| Total Spend | `Spend` | SUM |
| Total Impression | `Impressions` | SUM |
| Total Clicks | `Clicks` | SUM |
| Conversion | `Conversions` | SUM |
| Revenue | `Revenue` | SUM |
| Avg ROI | `ROI` | AVERAGE |
| Average CPC | `CPC` | AVERAGE |
| Avg CTR | `CTR` | AVERAGE |

### Why the average cards matter

The report averages the existing row-level `CTR`, `CPC`, and `ROI` columns. It does **not** calculate the cards as weighted ratios such as:

```text
CTR = SUM(Clicks) / SUM(Impressions)
CPC = SUM(Spend) / SUM(Clicks)
ROI = (SUM(Revenue) - SUM(Spend)) / SUM(Spend)
```

Those aggregate formulas are useful for independent funnel validation and can produce different numbers because observations have different volumes.

## Visual inventory

### Revenue and Total Spend by Channel

- **Type:** Column chart
- **Category:** `Marketing_Channel`
- **Values:** SUM(Revenue), SUM(Spend)
- **Business question:** How much revenue and spend are associated with each marketing channel?

### Revenue by Channel and Quarter

- **Type:** Waterfall chart
- **Breakdown:** `Quarter`
- **Category:** `Marketing_Channel`
- **Value:** SUM(Spend)
- **Business question:** How is spend distributed across channels and the source-provided quarter labels?
- **Important:** The title says **Revenue**, but the configured value is **SUM(Spend)**. Also, the `Quarter` field here is the raw source column, not the Date Hierarchy quarter.

### Revenue by Product

- **Type:** Donut chart
- **Category:** `Product`
- **Value:** SUM(Revenue)
- **Business question:** Which products contribute the largest share of revenue?

### Total Spend & Average of ROI by Region

- **Type:** Clustered column chart
- **Category:** `Region`
- **Values:** SUM(Revenue), SUM(Spend)
- **Tooltip:** SUM(ROI)
- **Business question:** How do regional revenue and spend compare?
- **Important:** The visual title says **Average of ROI**, but the configured tooltip aggregation is **SUM(ROI)**.

### Regional revenue over time

- **Type:** Area chart
- **Category:** Date Hierarchy → Quarter
- **Series:** `Region`
- **Value:** SUM(Revenue)
- **Business question:** How does revenue change by calendar quarter across regions?
- **Important:** This quarter comes from the actual `Date` hierarchy, so it can differ from the source `Quarter` field.

### Region × Product Conversion Matrix

- **Type:** Matrix/pivot table
- **Rows:** `Region`
- **Columns:** `Product`
- **Values:** SUM(Conversions)
- **Business question:** Which region-product combinations generate the most conversions?

## Suggested dashboard reading order

1. Start with the KPI cards to understand total activity and commercial output.
2. Use the Date and Product slicers to define the analysis context.
3. Compare revenue and spend by channel and region.
4. Use the product donut and conversion matrix to identify concentration by product and region.
5. Review the area chart for time/region patterns.
6. Use the documentation notes when comparing quarter-based visuals because the PBIX mixes the source `Quarter` field with the date-derived quarter hierarchy.
