# SPEC: AI Use Self-Check

> Example spec, and the session's fallback build. It shows what a finished SPEC looks like.

## Purpose

A five-question self-check that helps employees and students test their understanding of basic, responsible AI use before they use AI tools for work or coursework.

## Users

- **Who opens it:** college employees and students new to generative AI
- **What they already know:** little or nothing about AI policies
- **Device and setting:** phone or laptop, on their own, about three minutes

## Requirements

| ID | Requirement |
|---|---|
| R1 | The self-check shall present five multiple-choice questions, one at a time. |
| R2 | When the user selects an answer and chooses Check, the self-check shall show whether the answer is correct and a one-sentence explanation. |
| R3 | If no answer is selected, then the self-check shall keep the Check button disabled. |
| R4 | While feedback is showing, the self-check shall offer a Next button and prevent changing the answer. |
| R5 | When the user finishes the fifth question, the self-check shall show the number correct out of five and offer a Start over button. |
| R6 | The self-check shall announce feedback and the final score to screen readers. |
| R7 | The self-check shall not store or send any user data. |
| R8 | Where a link to the institution's AI guidance is configured, the self-check shall show it on the results screen. |

## Accessibility criteria

- Answer choices are native radio buttons in a `fieldset` with a `legend` holding the question.
- Feedback and the final score are announced through a polite live region (R6).
- Correct and incorrect are shown with text and an icon, not color alone.

## Out of scope

- Logins, names, or saving scores
- Randomized question banks
- Timers

## Done when

- [ ] R1 through R8 pass when tested by hand.
- [ ] It meets ADR-001 (keyboard-only pass, automated scan, screen reader spot check).
- [ ] It meets ADR-002: `builds/ai-use-self-check/index.html`, one file, no outside requests, works in a 600 px tall iframe.

## Question content

To be written and reviewed by the presenters before the build. Keep questions general (protecting personal data, checking AI output, disclosing AI use, citing sources) rather than quoting any one institution's policy.
