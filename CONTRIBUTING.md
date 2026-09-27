# Contributing

## Before changing the dashboard

1. Review `docs/data_dictionary.md` and `docs/data_quality.md`.
2. Confirm whether the requested metric should be row-level averaged or aggregate/weighted.
3. Keep field names consistent with the source workbook unless a documented transformation is introduced.
4. Update `docs/dashboard_guide.md` when a visual's fields, aggregation, or business meaning changes.
5. Update `CHANGELOG.md` for material repository changes.

## Data changes

When replacing or extending the source dataset, validate:

- schema and column names
- null values
- duplicate rows
- date continuity/validity
- click and conversion relationships
- formula consistency for CTR, CPC, and ROI
- the definition of quarter/time dimensions

## Dashboard changes

When changing the PBIX, document:

- newly added measures or calculated columns
- visual field mappings
- filter/slicer behavior
- changes in KPI aggregation
- any new business assumptions
