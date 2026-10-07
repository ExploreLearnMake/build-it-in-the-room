# ADR-002: Build a single-file embed that works on almost any website

- **Status:** Accepted
- **Date:** 2026-10-07
- **Applies to:** every tool built from this repository unless a newer ADR replaces this one

## Context

The goal is to go from idea to working tool in a short session, often live in front of a room. Every open technical question (which framework, which server, where data goes, how to deploy) costs time and adds risk. Most of the tools people want to build (quizzes, calculators, checklists, branching scenarios, flashcards) need none of that.

People also want to put their tool where their audience already is: a course page, a department website, an intranet, a newsletter landing page. Those platforms differ, but nearly all of them can show a web page inside an `<iframe>`, or link to one.

## Decision

Every tool is a **single, self-contained HTML file** that can be embedded on almost any website.

- **One file.** HTML, CSS, and JavaScript live in `builds/<tool-name>/index.html`. No other files are required to run it.
- **No dependencies.** No frameworks, libraries, CDNs, web fonts, or external images. Use system fonts and inline SVG or data URIs.
- **No build step.** Opening the file in a browser runs it.
- **No server and no data.** No network requests, cookies, `localStorage`, analytics, or accounts. Nothing typed into the tool leaves the page.
- **Embed-friendly.** Works inside an `<iframe>` with no pop-ups and no dependence on the parent page. Responsive from 320 px wide. Content fits a reasonable fixed height (default 600 px) or scrolls inside the frame.
- **Hosted as a static file.** Default host is GitHub Pages from the same repository. Any static host approved by your IT team works the same way.
- **Accessible.** Meets ADR-001.

## Consequences

**Positive:**

- The TAD's platform questions are already answered, so planning takes minutes.
- The tool works on nearly any site that accepts an iframe or a link, and offline when opened as a file.
- No personal data means far fewer privacy and security reviews.
- Easy to review: one file, readable top to bottom.

**Negative:**

- No saved progress, user accounts, shared results, or gradebook integration. Tools that need those need a new ADR and a conversation with IT.
- Content changes mean editing the file and republishing it.
- Some platforms block iframes from outside domains. In that case, link to the tool instead of embedding it, or ask IT about an approved host.

## Requirements (EARS)

| ID | Requirement |
|---|---|
| E1 | Each tool shall consist of a single `index.html` file in its own folder under `builds/`. |
| E2 | The tool shall run by opening the file in a current browser, without a server or build step. |
| E3 | The tool shall not load any resource from another domain. |
| E4 | The tool shall not store or transmit user input. |
| E5 | While displayed inside an iframe 320 px or wider, the tool shall remain fully usable. |
