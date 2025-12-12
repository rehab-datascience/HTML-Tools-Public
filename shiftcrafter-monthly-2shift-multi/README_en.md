# ShiftCrafter Part 5 — Multi-Shift (Monthly, Early/Day/Late/Night + Short)

Auto-assign monthly schedules for a **Multi-shift system** (Early / Day / Late / Night) combined with **short day shifts**.  
Runs **client-side only** (no data sent out). Exports **CSV / ICS / Validation CSV**.

## TL;DR
- Supports **Early, Day, Late, and Night** shifts plus **Short Day**.
- Assignment order: **Night → Early → Late → Day (Full + Short)**.
- Hard rules: **No shift after a Night shift**; no double booking on the same day.

## Quick Start
1. Open `index_en.html` (Chrome recommended).
2. Input on the left panel:
   - Target month (YYYY-MM)
   - Required headcount: **Early / Day / Late / Night**
   - Night caps (weekly / optional monthly)
   - Staff lists: **Full-time (Early/Day/Late/Night)** and **Short-day only**
   - Day-off requests (e.g., `2025-11-03 Alice`)
   - Time settings for Early, Late, and Short shifts
3. Click **Generate**, then download **CSV / ICS / Validation CSV**.

## Outputs
- **CSV** `schedule_multi.csv` (wide)

- **ICS** `shift_multi.ics` (Asia/Tokyo):
  - Early: User defined (default 07:00–15:30)
  - Day (Full): 08:30–17:00  
  - Late: User defined (default 11:30–20:00)
  - Day (Short): User defined (default 09:00–16:00)  
  - Night: 17:00–09:00 (next day)  
  - `SUMMARY: Early: NAME / Day (Full): NAME / Late: NAME / Night: NAME / Day (Short): NAME`

- **Validation CSV** `validation_summary.csv`:
  - Counts for Early, Late, Day, Night shifts per person
  - `weekly_night_cap_violations` / `monthly_night_cap_violation`
  - `consec_night_2plus` — consecutive nights (≥2)
  - `day_after_night_violation` — shift right after a night (should be 0 under the rule)

## Assignment Logic (MVP)
1. Assign **Night** first (respect caps and requests).
2. Assign **Early** shifts.
3. Assign **Late** shifts.
4. Fill **Day** requirement with Full and Short staff (weighted).

> Short-day staff are **only assigned to Day shifts**.  
> CSV is UTF-8 with BOM; ICS uses `Asia/Tokyo`.

## Known Limitations
- `need_*` headcounts are uniform across the month.
- Fairness logic is simplified (prioritize those with fewer shifts).

## License
MIT
