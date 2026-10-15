# TASKS: Trip Fuel Cost Calculator

> Worked example. Each task is small enough to check by hand in under a minute.

- [x] **T1.** Page shell: `index.html` with `lang`, title, viewport, heading, and system fonts (covers: ADR-002; depends on: none)
- [x] **T2.** Input form with labeled distance, MPG, price, and people fields plus the Round trip checkbox, checked by default (covers: R1, R3, R5; depends on: T1)
- [x] **T3.** Calculation that updates as the user types (covers: R2, R3, R5; depends on: T2)
- [x] **T4.** Validation with inline error messages and `aria-invalid` (covers: R4; depends on: T2)
- [x] **T5.** Result area as a polite live region (covers: R6; depends on: T3)
- [x] **T6.** Accessibility pass against ADR-001: keyboard only, 320 px width, focus visible, automated scan (depends on: T1 to T5)
- [x] **T7.** Test every requirement and record results below (depends on: all)

## Test results

| ID | Pass/Fail | Notes |
|---|---|---|
| R1 | Pass | Distance, MPG, and price fields with units in the labels. |
| R2 | Pass | 120 mi round trip, 30 MPG, $3.60 shows $28.80, 240 miles, 8 gallons. |
| R3 | Pass | Unchecking Round trip shows $14.40 and 120 miles. |
| R4 | Pass | 0, -5, "abc", and empty each show an error and hide the cost. |
| R5 | Pass | 2 people shows $14.40 per person; 1 or empty shows no per-person line. |
| R6 | Pass | Result region has `aria-live="polite"`. |
| R7 | Pass | No requests beyond the file itself (checked in the browser's Network tab). |
