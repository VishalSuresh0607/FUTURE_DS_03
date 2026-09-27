# Data Dictionary

## Source

**Workbook:** `data/marketing_analytics_dataset.xlsx`

**Worksheet:** `Sheet1`

**Observations:** 100 rows

**Fields:** 13

The workbook is a compact marketing-performance dataset. Categorical dimensions describe **when, where, what, and how** activity occurred; numeric measures quantify delivery, engagement, conversion, cost, and revenue.

## Field definitions

| Field | Type | Meaning | Typical use |
|---|---|---|---|
| `Date` | Date | Observation date | Time trends and Power BI date hierarchy |
| `Region` | Category | Geographic segment: East, North, South, West | Regional performance comparison |
| `Product` | Category | Product segment: Product A–D | Product mix and revenue/conversion analysis |
| `Marketing_Channel` | Category | Acquisition channel: Email, Search Engine, Social Media, Direct Mail | Channel effectiveness |
| `Quarter` | Category | Source-provided quarter label (`Q1`–`Q4`) | Waterfall breakdown in the PBIX |
| `Spend` | Numeric | Marketing expenditure for the observation | Cost and budget analysis |
| `Impressions` | Numeric | Number of recorded impressions | Top-of-funnel reach |
| `Clicks` | Numeric | Number of recorded clicks | Engagement |
| `Conversions` | Numeric | Number of recorded conversions | Bottom-of-funnel outcome |
| `Revenue` | Numeric | Revenue attributed to the observation | Commercial outcome |
| `CTR` | Ratio | Click-through rate, stored as a decimal | Engagement efficiency |
| `CPC` | Numeric | Cost per click | Click acquisition efficiency |
| `ROI` | Ratio | Return on investment, stored as a decimal | Return efficiency |

## Core formulas

The source metrics are already populated in the Excel workbook and are not formula cells in the workbook. Their values are consistent with the following business definitions, subject to the rounding noted below.

### CTR

```text
CTR = Clicks / Impressions
```

### CPC

```text
CPC = Spend / Clicks
```

### ROI

```text
ROI = (Revenue - Spend) / Spend
```

### Derived funnel conversion rate

The source does not contain a dedicated conversion-rate field. For analysis, a click-to-conversion rate can be derived as:

```text
Conversion Rate = Conversions / Clicks
```

## Rounding behavior observed

- `CTR` is stored to approximately 4 decimal places.
- `CPC` is stored to 2 decimal places.
- `ROI` is stored to approximately 4 decimal places.

A validation of the source values against the formulas above shows the expected small differences caused by rounding, rather than large calculation errors.

## Categorical values

- **Regions:** East, North, South, West
- **Products:** Product A, Product B, Product C, Product D
- **Marketing channels:** Direct Mail, Email, Search Engine, Social Media
- **Quarter labels:** Q1, Q2, Q3, Q4

## Dataset scope

The dates run from **2023-01-01 through 2024-11-24**, with one observation date per row and 100 unique dates.
