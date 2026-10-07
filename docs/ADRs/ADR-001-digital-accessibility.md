# ADR-001: Accessibility is a baseline requirement (WCAG 2.2 AA)

- **Status:** Accepted
- **Date:** 2026-10-07
- **Applies to:** everything built from this repository
- **Context tags:** accessibility, WCAG, Section 508, ARIA, ADA Title II

> **Not legal advice.** This ADR records an engineering commitment and its basis. Whether ADA Title II applies to a specific organization, and its exact compliance date, is a question for your counsel or compliance office.

## Context

Tools built quickly with AI are an easy way for inaccessible content to reach the public. Deciding the accessibility target before the build costs far less than fixing it afterward.

Many people using this kit work for public colleges, schools, or government agencies. For them, the U.S. Department of Justice's ADA Title II rule on web content and mobile apps (published April 24, 2024) sets **WCAG 2.1 Level AA** as the technical standard. The rule covers public schools, community colleges, and public universities, including content produced by contractors and vendors. An interim final rule published in April 2026 extended the compliance dates by one year:

| Entity size | Compliance date |
|---|---|
| 50,000 or more population | April 26, 2027 |
| Under 50,000 population, or special district | April 26, 2028 |

The rule allows exceeding WCAG 2.1 AA. Its limited exceptions (archived content, some pre-existing documents, and similar) do not cover new interactive tools like the ones built here.

## Decision

Accessibility is a **baseline requirement**, not a feature or a final polish step.

- **Target: WCAG 2.2 Level AA.** **Floor: WCAG 2.1 Level AA**, the Title II standard. WCAG 2.2 AA adds a few criteria (such as minimum target size and visible focus that isn't hidden) and costs little extra for small tools.
- **Semantic HTML first.** Use native elements (`button`, `label`, `fieldset`, headings) before ARIA. Use WAI-ARIA authoring practices only to fill gaps.
- The AI reads this ADR before writing code and applies it by default.

## Requirements (EARS)

| ID | Requirement |
|---|---|
| A1 | Every tool built from this repository shall conform to WCAG 2.2 Level AA, with WCAG 2.1 Level AA as the minimum. |
| A2 | When a SPEC or TAD is written, it shall include accessibility acceptance criteria. |
| A3 | Interactive components shall use semantic HTML first and WAI-ARIA authoring practices only where native elements fall short. |
| A4 | When the tool shows feedback, a score, or any status change, the tool shall announce it to assistive technology and shall not rely on color alone. |
| A5 | If a build cannot meet a criterion, then the builder shall record the criterion, the reason, and the accessible alternative in the TAD. Silent non-conformance is not allowed. |

## Consequences

Every build must pass these checks before it counts as done:

- Every interactive element works with a keyboard alone, in a logical order, with a visible focus indicator that isn't hidden.
- Text contrast is at least 4.5:1 (3:1 for large text, meaningful graphics, and control borders).
- Click and tap targets are at least 24 by 24 CSS pixels.
- Images have alt text; decorative images are hidden from assistive technology.
- Form controls have visible, programmatically associated labels.
- Content reflows at 320 CSS pixels wide without horizontal scrolling and works at 200% zoom.
- Motion and timers can be paused, stopped, or extended.
- The page has a `lang` attribute, a meaningful `<title>`, and headings in order.

**How we check:** a keyboard-only pass, an automated scan (WAVE, axe, or your institution's scanner), and a screen reader spot check (NVDA, VoiceOver, or Narrator) where possible. Automated tools catch only a portion of issues, so the manual checks are required.

**Costs:** a few extra minutes per build for manual testing.

## Sources

- U.S. DOJ, "Fact Sheet: New Rule on the Accessibility of Web Content and Mobile Apps Provided by State and Local Governments," https://www.ada.gov/resources/2024-03-08-web-rule/
- W3C, Web Content Accessibility Guidelines (WCAG) 2.2, https://www.w3.org/TR/WCAG22/
- W3C, ARIA Authoring Practices Guide, https://www.w3.org/WAI/ARIA/apg/
