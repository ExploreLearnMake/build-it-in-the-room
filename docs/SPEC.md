# SPEC: [Tool name]

> Template. Replace everything in [brackets]. Delete this line when done.

## Purpose

[One sentence: what job does this tool do, and for whom?]

## Users

- **Who opens it:** [role, e.g., students in an intro course, new HR hires, members of the public]
- **What they already know:** [prior knowledge]
- **Device and setting:** [phone, laptop, in class, at home]

## Requirements

Each requirement is one testable behavior, written in EARS. IDs let tasks and tests point back here.

| ID | Requirement |
|---|---|
| R1 | The [tool] shall [response]. |
| R2 | When [trigger], the [tool] shall [response]. |
| R3 | While [state], the [tool] shall [response]. |
| R4 | If [unwanted condition], then the [tool] shall [response]. |
| R5 | Where [optional feature is included], the [tool] shall [response]. |

### EARS patterns

- **Ubiquitous** (always true): The `<system>` shall `<response>`.
- **Event-driven:** When `<trigger>`, the `<system>` shall `<response>`.
- **State-driven:** While `<state>`, the `<system>` shall `<response>`.
- **Unwanted behavior:** If `<condition>`, then the `<system>` shall `<response>`.
- **Optional feature:** Where `<feature is included>`, the `<system>` shall `<response>`.

## Accessibility criteria

[The ADR-001 checks that matter most for this tool, e.g., "Every answer choice is a native radio button with a visible label."]

## Out of scope

- [Something we are deliberately not building]

## Done when

- [ ] Every requirement above passes when tested by hand.
- [ ] The tool meets ADR-001 (keyboard-only pass, automated scan, screen reader spot check).
- [ ] The tool meets ADR-002 (one file, no outside requests, works in an iframe).
- [ ] [Any other acceptance check]
