# Stats Insights

> Category: Content & Detail

## Purpose
Charts and trends summarizing user progress or data over time.

## Key Elements
- Period switcher: Day / Week / Month / Year
- Headline metric with delta vs previous period
- Primary trend chart (bar/line/timeline)
- Breakdown list or secondary tiles
- Plain-language comparison sentence ("up 12% from last week")

## States & Variations
- Insufficient data ("keep logging to see trends") with progress toward unlock
- Loaded per period; empty period
- Per-widget loading; anomaly/highlight callouts

## Design Notes
- One headline number per view; a wall of charts communicates nothing
- Label data directly on the chart; legends force cross-referencing
- The written comparison sentence often lands harder than the chart itself (see Fi's rest comparison)

## Technical Considerations
- Aggregate server-side (or via SQL in the local DB) — never ship raw event lists to the chart layer
- Timezone-correct bucketing: a "day" is the user's local midnight-to-midnight; recompute when the user changes timezone
- Chart implementation: Swift Charts / Vico / MPAndroidChart, or custom Canvas for signature visuals like 24h sleep timelines
- Cache computed aggregates keyed by (metric, period, tz); invalidate on new data
- Accessibility: charts need a text equivalent (summary label or data table) for screen readers
- Watch for division-by-zero/NaN in delta calculations with sparse data

## References
- Fi Rest weekly timeline (Mobbin) — best-in-class dependent-tracking stats
- Apple Health trend cards
