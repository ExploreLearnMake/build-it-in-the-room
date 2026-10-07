# AGENTS.md

Instructions for any AI agent or assistant working in this repository. Read this file before doing anything else.

## The rule

All projects start with a specification document. Requirements are written in EARS (Easy Approach to Requirements Syntax). All code includes documentation, such as JSDoc for JavaScript. Projects keep their documentation in Markdown.

## Order of work

1. **Read first.** Read `docs/SPEC.md`, `docs/TAD.md`, `docs/TASKS.md`, and every file in `docs/ADRs/` before proposing or writing code.
2. **No spec, no code.** If `docs/SPEC.md` still contains template placeholders, do not write code. Interview the user using `prompts/01-interview.md`, then write the spec.
3. **One question at a time.** When interviewing, ask a single question, wait for the answer, then ask the next.
4. **Stop for review.** After writing or changing `docs/SPEC.md`, `docs/TAD.md`, or `docs/TASKS.md`, stop and ask the user to review before continuing.
5. **Build only what the spec requires.** Anything listed under "Out of scope" stays out. If you think something is missing, ask; don't add it.
6. **Work the task list in order.** Check off each task in `docs/TASKS.md` when it passes its check.
7. **Test against the spec.** When the build is done, list every requirement in `docs/SPEC.md` with pass or fail.

## Decisions already made

Do not reopen these unless the user explicitly asks to change one. If they do, write a new ADR that replaces the old one.

- **ADR-001, accessibility:** WCAG 2.2 AA target, WCAG 2.1 AA minimum. Not a later step. See `docs/ADRs/ADR-001-digital-accessibility.md`.
- **ADR-002, single-file embed:** every tool is one self-contained `builds/<tool-name>/index.html` with no dependencies, no build step, no server, and no data collection, embeddable in an iframe on almost any website. See `docs/ADRs/ADR-002-single-file-embed.md` and `skills/embed.md`.
- **No personal data:** do not collect, store, or transmit names, emails, IDs, grades, or other personal information.

Because ADR-002 answers the platform questions, do not ask the user about frameworks, hosting, databases, or deployment during the interview. Spend the questions on what the tool must do.

## Writing requirements in EARS

| Pattern | Template |
|---|---|
| Ubiquitous | The `<system>` shall `<response>`. |
| Event-driven | When `<trigger>`, the `<system>` shall `<response>`. |
| State-driven | While `<state>`, the `<system>` shall `<response>`. |
| Unwanted behavior | If `<condition>`, then the `<system>` shall `<response>`. |
| Optional feature | Where `<feature is included>`, the `<system>` shall `<response>`. |

Keep each requirement to one testable behavior. Give each one an ID (R1, R2, and so on) so tasks and tests can point to it.

## Code conventions

- Document every function with JSDoc (purpose, parameters, return value).
- Use semantic HTML elements before ARIA. Every control is reachable and usable by keyboard.
- Keep code readable over clever. The people maintaining this may not be developers.

## Where things go

- Finished tools: `builds/<tool-name>/index.html`
- Prompts used during the project: `prompts/`
- Platform-specific guidance: `skills/`
- New decisions worth recording: a new file in `docs/ADRs/` (copy the format of ADR-001)
