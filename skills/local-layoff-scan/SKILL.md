---
name: local-layoff-scan
description: "Scan recent U.S. layoffs and plant closings in one place from WARN Act notices: near a city or ZIP code, in a state, or in a census region, for a time period. Use when the user asks which employers near a place filed layoff notices, what layoffs happened in a state or area this week, month or quarter, or how a local area compares with the period before."
---

# Local layoff scan

Summarize WARN layoff notices for one place and period, using the DataCEVA US Layoff Notices connector. Before
answering for the first time in a conversation, read `references/warn-data-notes.md` for what the data covers and
how to cite it.

## Steps

1. **Pin down the place and period.**
   - Place: a city as `City, ST`, a 5-digit ZIP, a state, or a census region (Northeast, Midwest, South, West).
     The data covers U.S. states and D.C. only; for anywhere else, say so and stop.
   - Radius: 25 miles unless the user says otherwise (up to 100).
   - Period: turn "this month", "last quarter" and similar into `filed_after` / `filed_before` dates. With no
     period, use the last 90 days and say so.
2. **List the notices.** Call `search_layoff_notices` with the place (or `states` / `census_region`) and dates,
   `sort: "largest"`, `limit: 20`. If `total_matching` is larger than what came back, say how many more there
   are.
3. **Break it down.** Call `summarize_layoffs` with the same filters and `group_by: "industry"`. For periods
   longer than two months, also call it with `group_by: "month"`.
4. **Compare with the period before.** Call `summarize_layoffs` again with the same filters for the previous
   period of the same length, and compare notices and workers.
5. **Check coverage.** Call `get_data_coverage` for the state (or each state in the region, if few), so you can
   say whether its list is current.
6. **Write the scan** in the format below.

## Format

**Answer** (two or three sentences): how many notices and workers in the place and period, the largest one,
and the change from the period before (as numbers, not just "up" or "down").

**Notices** (table, largest first): company, city, filed date, layoff date, workers, type, industry, source
link (`notice_url`, or the agency's `state_warn_page`).

**By industry** (table: industry, notices, workers), with a note that industry comes from some states only.

**Compared with the period before** (one short paragraph). Don't call a change a trend when the counts are
small (for example 3 notices vs 2).

**Limits** (bullets that apply): approximate locations (ZIP, city or county centre); states that publish only a
planned layoff date (GA, NJ, PA and much of MI) are left out of filed-date results unless
`include_scheduled_only` is set; any state that is partial, saved-history-only or unavailable; the as-of date.

## Rules

- Use only what the tools return; don't add layoffs from memory or the news.
- Keep filed date and layoff date distinct, and label which one a date is.
- Never describe or look for individual employees.
- If nothing is found, say no WARN notices were filed in the covered data for that place and period, not that
  there were no layoffs.
