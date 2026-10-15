# SPEC: Trip Fuel Cost Calculator

> Worked example, and the session's fallback build. It shows what a finished SPEC looks like. The finished tool is `builds/trip-cost-calculator/index.html`.

## Purpose

A calculator that estimates the fuel cost of a drive, so staff and students can plan a trip or split the cost with others.

## Users

- **Who opens it:** college staff planning travel to another campus or event, and students carpooling
- **What they already know:** roughly how far they're going and what their car gets per gallon
- **Device and setting:** phone or laptop, embedded on a travel or student-life page, under a minute of use

## Requirements

| ID | Requirement |
|---|---|
| R1 | The calculator shall accept a one-way distance in miles, fuel economy in miles per gallon, and a gas price in dollars per gallon. |
| R2 | When all required inputs hold numbers greater than zero, the calculator shall show the total fuel cost rounded to the cent, the miles driven, and the gallons used. |
| R3 | While Round trip is checked, the calculator shall double the distance. Round trip shall be checked by default. |
| R4 | If a required input is empty, zero, negative, or not a number, then the calculator shall show an error message next to that input and shall not show a cost. |
| R5 | Where more than one person is sharing the cost, the calculator shall also show the cost per person. |
| R6 | When the result changes, the calculator shall announce it to screen readers. |
| R7 | The calculator shall not store or send anything the user types. |

## Accessibility criteria

- Every input has a visible label with its unit, and an example in the hint text.
- Error messages appear in text next to the field and are tied to it with `aria-describedby`; fields are marked `aria-invalid` (R4).
- The result is in a polite live region (R6). Nothing relies on color alone.
- Inputs and the checkbox are at least 24 by 24 pixels and show a visible focus outline.

## Out of scope

- Looking up distances or routes on a map
- Live or local gas prices
- Mileage reimbursement rates, tolls, parking, or wear and tear
- Metric units
- Saving or sharing trips

## Done when

- [ ] R1 through R7 pass when tested by hand. Test case: 120 miles one way, round trip, 30 MPG, $3.60 per gallon gives 240 miles, 8 gallons, $28.80; with 2 people, $14.40 each.
- [ ] It meets ADR-001 (keyboard-only pass, automated scan, screen reader spot check).
- [ ] It meets ADR-002: `builds/trip-cost-calculator/index.html`, one file, no outside requests, works in a 600 px tall iframe from 320 px wide.
