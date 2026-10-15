# TAD: Trip Fuel Cost Calculator

> Worked example. Compare it with the blank template in `docs/TAD.md`.

## Users and purpose

Staff and students estimating the fuel cost of a drive, usually on a phone, sometimes splitting the cost with others. See `SPEC.md` for requirements R1 to R7.

## Platform and hosting

Decided by ADR-002.

- **Format:** one self-contained file, `builds/trip-cost-calculator/index.html`. No dependencies, server, or build step.
- **Hosted at:** GitHub Pages from this repository.
- **Embedded on:** a travel or student-life web page, in an iframe 600 px tall.
- **Who approved this location:** example only. A real campus deployment needs the web team's sign-off.

## Components

| Component | Responsibility | Requirements covered |
|---|---|---|
| Input form | Four labeled text inputs (distance, MPG, price, people) and a Round trip checkbox | R1, R3, R5 |
| Validation | Reads each input, shows an inline error for empty, zero, negative, or non-numeric values | R4 |
| Calculation | miles = distance × (2 if round trip); gallons = miles ÷ MPG; cost = gallons × price; per person = cost ÷ people | R2, R3, R5 |
| Result area | Shows cost, miles, gallons, and per-person cost in a polite live region | R2, R5, R6 |

## Data

- **Stores:** nothing (ADR-002). No cookies, `localStorage`, or network requests (R7).
- **Content lives in:** the page itself. There is no data to edit.

## Constraints

- Accessibility: ADR-001 (WCAG 2.2 AA). Visible labels with units, text errors tied to fields, live region for results, 24 px minimum targets, visible focus.
- Embed: ADR-002. Single file, system fonts, usable at 320 px wide; scrolls inside a 600 px frame on narrow phones.
- No login.

## Out of scope

- Map or route lookup, live gas prices, reimbursement rates, tolls, metric units, saving trips (from `SPEC.md`).

## Open questions

- None for the example. A real deployment would ask whether to link to the institution's travel reimbursement policy.
