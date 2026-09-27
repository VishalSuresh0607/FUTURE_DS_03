# Analysis Insights

These findings are based on the 100 source observations in `Sheet1` and are intended to document the completed analysis, not to introduce new dashboard logic.

## Overall performance

| Metric | Value |
|---|---:|
| Total spend | 261,166.32 |
| Total revenue | 1,042,479.69 |
| Total impressions | 570,069 |
| Total clicks | 55,973 |
| Total conversions | 2,531 |
| Aggregate CTR | 9.82% |
| Click-to-conversion rate | 4.52% |
| Average row-level CTR | 13.86% |
| Average row-level CPC | 6.5707 |
| Average row-level ROI | 4.4761x / 447.61% |
| Aggregate ROI | 2.9916x / 299.16% |

The difference between **average row-level ROI (447.61%)** and **aggregate ROI (299.16%)** demonstrates why the aggregation method should always be stated when reporting ROI.

## Channel observations

| Channel | Revenue | Spend | Conversions | Aggregate CVR |
|---|---:|---:|---:|---:|
| Email | 302,491.70 | 79,171.52 | 693 | 3.68% |
| Social Media | 295,320.58 | 68,719.06 | 638 | 5.16% |
| Search Engine | 269,164.13 | 57,352.72 | 606 | 4.27% |
| Direct Mail | 175,503.28 | 55,923.02 | 594 | 5.61% |

Email accounts for the largest revenue total and the largest conversion count in the source data. Direct Mail has the highest aggregate click-to-conversion rate among the four channels, while producing the lowest revenue total.

## Product observations

| Product | Revenue | Spend | Conversions | Avg row-level ROI |
|---|---:|---:|---:|---:|
| Product C | 345,183.16 | 74,208.40 | 742 | 5.57x |
| Product B | 263,435.48 | 74,135.67 | 696 | 4.27x |
| Product A | 219,967.15 | 58,368.76 | 564 | 4.02x |
| Product D | 213,893.90 | 54,453.49 | 529 | 3.81x |

Product C has the highest revenue, conversion volume, and average row-level ROI in this dataset.

## Regional observations

| Region | Revenue | Spend | Conversions | Avg row-level ROI |
|---|---:|---:|---:|---:|
| East | 308,543.81 | 69,841.67 | 665 | 5.20x |
| West | 306,119.49 | 76,409.43 | 733 | 4.98x |
| North | 266,923.58 | 67,187.74 | 745 | 3.74x |
| South | 160,892.81 | 47,727.48 | 388 | 3.70x |

East has the highest revenue total and average row-level ROI. North has the highest conversion count despite not having the highest revenue.

## Time observations using the Date field

The date-derived calendar-quarter revenue totals used by the area chart are:

| Calendar quarter from `Date` | Revenue |
|---|---:|
| Q1 | 310,460.58 |
| Q2 | 235,086.49 |
| Q3 | 277,766.51 |
| Q4 | 219,166.11 |

These values are based on the actual dates, not the source `Quarter` column.

## Negative ROI observations

There are **6 rows with negative row-level ROI**. They occur where spend exceeds recorded revenue. This is useful for outlier review and campaign-level investigation.

## Practical interpretation

The dataset shows meaningful variation across channel, product, and region. The most important analytical caution is not the volume of data but the **definition and aggregation of rates**: row-level CTR/CPC/ROI are already provided, and the PBIX averages those fields for the KPI cards. For future iterations, a clearly defined measures layer with weighted/aggregate formulas would make cross-period and cross-segment comparisons more robust.
