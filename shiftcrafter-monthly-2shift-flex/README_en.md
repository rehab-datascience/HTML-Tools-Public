# ShiftCrafter Part 4 — Short-Shift Support (Monthly, 2-shift + short day)

Auto-assign monthly schedules for a **2-shift system** (Day 08:30–17:00 / Night 17:00–09:00) with **short day shifts** (e.g., 09:00–16:00).  
Runs **client-side only** (no data sent out). Exports **CSV / ICS / Validation CSV**.

## TL;DR
- Short day shifts are counted with a **weight** (default **0.8**) toward day coverage.
- Assignment order: **Night → Day (full) → Day (short)**.
- Hard rules: **No Day after a Night**; no double booking on the same day.

## Quick Start
1. Open `index_en.html` (Chrome recommended).
2. Input on the left panel:
   - Target month (YYYY-MM)
   - Required headcount: **Day (as full-day equivalents)** / **Night**
   - Night caps (weekly / optional monthly)
   - Staff lists: **Full-day/night eligible** and **Short-day only**
   - Day-off requests (e.g., `2025-11-03 Alice`)
   - Short-shift **weight** (default 0.8) and **time window** (default `09:00-16:00`)
3. Click **Generate**, then download **CSV / ICS / Validation CSV**.

## Outputs
- **CSV** `schedule_monthly_part4.csv` (wide):

- **ICS** `shift_monthly_part4.ics` (Asia/Tokyo):
- Day (Full): 08:30–17:00  
- Day (Short): UI setting (default 09:00–16:00)  
- Night: 17:00–09:00 (next day)  
- `SUMMARY: Day (Full): NAME / Day (Short): NAME / Night: NAME`
- **Validation CSV** `validation_summary_part4.csv` (key columns):
- `weighted_day_coverage_pct` — monthly **weighted** day coverage (full=1.0, short=weight)
- `off_fulfillment_pct` — day-off request fulfillment (per person)
- `weekly_night_cap_violations` / `monthly_night_cap_violation`
- `consec_night_2plus` — consecutive nights (≥2)
- `day_after_night_violation` — day shift right after a night (should be 0 under the rule)

## Assignment Logic (MVP)
1. Assign **Night** first (respect weekly/monthly caps and day-off requests).
2. Fill **Day (Full)** up to `need_day` if possible.
3. If still short, add **Day (Short)** until **weighted coverage** reaches `need_day`.

> Short-day staff are **not assigned to Night**.  
> CSV is UTF-8 with BOM; ICS uses `Asia/Tokyo`.

## Known Limitations
- `need_day`/`need_night` are uniform across the month (per-day profile planned).
- Fairness/optimization is simplified (minimize totals/nights first).
- Adjust the **short-shift weight** to match your local rules.

## Roadmap
- Staff attributes: **Weekend-off**, **No-night**
- Per-day demand profiles (weekday/weekend/holiday)
- Per-person working minutes and optimization-based fairness
- Per-staff ICS export and anonymization options

## License
MIT (planned)