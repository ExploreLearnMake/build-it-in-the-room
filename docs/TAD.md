# TAD: [Tool name]

> Technical architecture document. Template. Replace everything in [brackets].

## Users and purpose

[Summarize from SPEC.md in two or three sentences.]

## Platform and hosting

Decided by ADR-002 unless this section says otherwise.

- **Format:** one self-contained file, `builds/[tool-name]/index.html`. No dependencies, server, or build step.
- **Hosted at:** [default: GitHub Pages from this repository; or another approved static host]
- **Embedded on:** [the page or platform where the iframe or link will go, e.g., a Canvas page, department website]
- **Who approved this location:** [IT contact, or "personal project"]

## Components

| Component | Responsibility | Requirements covered |
|---|---|---|
| [e.g., Question data] | [Holds the questions and answers] | [R1] |
| [e.g., Display] | [Shows one item at a time] | [R1, R3] |
| [e.g., Feedback] | [Explains the answer] | [R2] |

## Data

- **Stores:** nothing (ADR-002). [Change only with a new ADR.]
- **Content lives in:** [e.g., a JavaScript array at the top of the file, so it's easy to edit]

## Constraints

- Accessibility: ADR-001 (WCAG 2.2 AA). [List the criteria most relevant to this tool.]
- Embed: ADR-002 (single file, works in an iframe from 320 px wide).
- [No login required]
- [Campus or IT rules]

## Out of scope

- [Carry over from SPEC.md]

## Open questions

- [Anything still undecided]
