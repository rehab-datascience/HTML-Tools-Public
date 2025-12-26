# ShiftCrafter Part 6 (Class-Based)

This is the **ShiftCrafter Class-Based** version, a multi-functional shift scheduling tool.
It supports staff skill class management, detailed shift requests, and separate staffing requirements for weekdays and holidays.

## Directory Structure
- `index.html`: Japanese version
- `index_en.html`: English version

## Key Features

### 1. Staff Class & Attribute Management
You can distinguish skill levels and attributes by appending `:A` or `:S` to staff names.

Format: `Name:Class:Attribute`

- **Class**: A (Leader) or B (General). Defaults to B if omitted.
  - Class A staff are prioritized to meet the "Minimum Class A" requirements for day and night shifts.
- **Attribute**: S (Short-time)
  - Staff with the S attribute follow the "Monthly Night Cap (Short/S)" setting.
  - For **staff who cannot do night shifts**, add `:S` and set "Monthly Night Cap (Short/S)" to `0` in the settings.

Example:
```
Smith:A       (Leader, Normal)
Johnson:B     (General, Normal)
Davis:B:S     (General, Short-time)
```

### 2. Detailed Request Input
In addition to the traditional "Off" request, you can specify:
- **Off**: Request a day off
- **Day**: Request a day shift
- **Night**: Request a night shift
- **NoNight**: Request NO night shift (Day shift or Off is acceptable)

Example:
```
2025-11-03 Smith Off
2025-11-05 Johnson Night
2025-11-10 Davis NoNight
```

### 3. Weekday/Holiday Staffing Requirements
You can set required staffing numbers separately for "Weekdays" and "Holidays" (Sat/Sun/Public Holidays).
This allows for operations like "more staff on weekdays, fewer on holidays".
*Sat/Sun are auto-detected. Public holidays can be manually entered in the list.*

### 4. Matrix CSV Output
The CSV export format has been changed to a calendar (matrix) format with staff as rows and dates as columns.
This is ideal for printing or further processing in Excel.

### 5. Shift Limits
- **Monthly Night Cap (Normal)**: Applies to most staff.
- **Monthly Night Cap (Short/S)**: Applies only to staff with the `:S` attribute. Set to `0` to exempt them from night shifts.
- (Weekly night cap setting has been removed)

### 6. Automatic Off-Day Calculation
The "target number of off days" for each staff member is automatically calculated based on the number of **Saturdays, Sundays, and Holidays** in the month.
The scheduler will limit the total working days (so effectively ensuring the target off days) during generation.

### 7. Verification Report
Clicking the "Verification Report" button shows:
- Unfulfilled requests (Request vs Result discrepancy)
- Work days check (Warning if a staff exceeds the maximum working days limit)

---
[ShiftCrafter Top](../README.md)
