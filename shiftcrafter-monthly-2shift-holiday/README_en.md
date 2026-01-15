# ShiftCrafter Monthly (2-Shift/Holiday)

ShiftCrafter Monthly 2-Shift Holiday is a browser-based tool for automatically generating **2-shift (Day/Night)** schedules.
It focuses specifically on **Strict Holiday Quota Management** and **Ensuring Consecutive Holidays**.

## Key Features

*   **2-Shift Scheduling**: Automatic assignment of Day (including Early/Late) and Night shifts.
*   **Holiday Quota Automation**:
    *   The total number of holidays for the month is fixed as the sum of "Saturdays", "Sundays", and "Public Holidays (User Input)".
    *   Schedules are generated so that all staff receive exactly this equal number of holidays.
*   **Weekend Consecutive Holidays**:
    *   Attempts to ensure that every staff member gets **at least 2 instances per month** of "Consecutive Holidays (2+ days) that include a Saturday, Sunday, or Monday".
*   **Balanced Staffing**:
    *   Optimizes monthly balance by conserving Class A staff and dynamically allocating surplus.
    *   Strictly adheres to holiday quotas by correctly accounting for "Post-Night" rest days.
*   **Visual Alerts**: Highlights understaffed days in Blue.
*   **Random Variation**: Generates slightly different schedule proposals each time you click the button.
*   **Matrix CSV Export**: Output in a format easy to process in Excel.
*   **iCalendar (.ics) Export**: Compatible with Google Calendar, etc.

## How to Use

1.  Open `index_en.html` in your browser.
2.  **Settings**:
    *   Select the Target Month.
    *   Enter the required number of staff for each shift.
    *   **Holiday Settings**: Enter the "Count (e.g., 2)" or "Specific Dates (e.g., 2026-02-11)" of public holidays for this month.
        *   *Note: Total holidays = Weekends + count entered here.*
3.  **Staff & Requests**:
    *   Enter the staff list and shift requests.
4.  Click "Generate Schedule".
5.  Use the **Validation Report** button to verify if all staff meet the holiday quota and consecutive holiday targets.

## Directory Structure

*   `index.html`: Japanese Version
*   `index_en.html`: English Version
*   `samples/`: Sample data for testing

## License

MIT License
