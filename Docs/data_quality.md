# Data Quality and Validation Notes

## Validation summary

The provided Excel source was checked before documenting the repository.

| Check | Result |
|---|---|
| Row count | 100 data rows |
| Column count | 13 columns |
| Missing values | None detected in the populated table |
| Duplicate rows | None detected |
| Unique dates | 100 |
| Date range | 2023-01-01 to 2024-11-24 |
| Clicks greater than impressions | None |
| Conversions greater than clicks | None |
| Negative spend | None |
| Negative revenue | None |
| Negative row-level ROI | 6 rows |
| Quarter vs Date-derived quarter mismatch | 77 of 100 rows |

## Key issue: `Quarter` is inconsistent with `Date`

When the calendar quarter is derived from `Date`, the source `Quarter` field disagrees in **77 rows**.

This does not necessarily mean the source is unusable; it means the field should not be silently assumed to be a calendar-quarter derivation of `Date`.

The PBIX uses both definitions:

- **Area chart:** Date Hierarchy → Quarter (calendar quarter derived from `Date`)
- **Waterfall:** raw `Quarter` column from `Sheet1`

Future work should explicitly choose one definition and use it consistently across visuals and measures.

## KPI aggregation caveat

`CTR`, `CPC`, and `ROI` are stored as precomputed row-level values. The report defines its KPI cards using `AVERAGE` over those fields.

For independent aggregate reporting, consider these measures:

```text
Aggregate CTR = SUM(Clicks) / SUM(Impressions)
Aggregate CPC = SUM(Spend) / SUM(Clicks)
Aggregate ROI = (SUM(Revenue) - SUM(Spend)) / SUM(Spend)
Conversion Rate = SUM(Conversions) / SUM(Clicks)
```

These are not replacements made in the supplied PBIX; they are recommended definitions for a future semantic/measures layer.

## Source-value rounding

The row-level fields are rounded:

- CTR ≈ 4 decimals
- CPC = 2 decimals
- ROI ≈ 4 decimals

Formula rechecks match within rounding tolerance. No evidence of missing or structurally invalid numeric rows was found during this audit.

## Report-definition notes

Two label/configuration mismatches are present in the PBIX:

1. The waterfall title says **“Revenue by Channel and Quarter”**, but the configured Y value is **SUM(Spend)**.
2. The regional comparison title says **“Total Spend & Average of ROI by Region”**, but ROI appears in the tooltip as **SUM(ROI)**, not AVERAGE(ROI).

These notes are preserved in the repository documentation so future maintainers understand the current report behavior.
