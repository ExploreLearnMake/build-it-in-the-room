# Build It in the Room

**A starter kit for building small interactive tools with AI, the way developers do it.**

From the session *Build It in the Room: What Developers Know About AI That Everyone Else Needs To* at the 2026 National Summit on Artificial Intelligence, Chandler-Gilbert Community College, October 15, 2026. Presented by Jason Reiche and Gordon Inman, Rio Salado College.

---

## The short version

AI can build quizzes, calculators, checklists, and practice scenarios for you. Most people ask for one, get something close, and spend an hour fixing it.

Developers work differently. Before anyone builds anything, they write down what it has to do. Then the AI builds from that page instead of guessing.

This kit gives you that page, already set up. You describe your idea, the AI asks you questions, and you end up with a short document that says exactly what to build. Then the AI builds it.

You don't need to know how to code.

## What you need

- A small idea. One screen, one kind of person using it, one job. "A five-question quiz on our lab safety rules" is the right size. "A course" is not.
- An AI tool that can work with files in a folder. Claude (Cowork or Code), VS Code with GitHub Copilot, Cursor, AWS Kiro, Google Antigravity, and ChatGPT Codex all work.
- About 30 minutes.

## Try it

1. **Get a copy.** On GitHub, click **Use this template** (or **Fork**). You can also click **Code > Download ZIP**.
2. **Open the folder in your AI tool.**
3. **Start the interview.** Copy the prompt from `prompts/01-interview.md` into your AI tool, and add one sentence about your idea.
4. **Answer the questions.** The AI asks one at a time. When it's done, it writes `docs/SPEC.md`.
5. **Read the spec.** This is the most important step. If something is wrong or missing, say so now. Fixing a sentence is much faster than fixing a finished tool.
6. **Let it plan and build.** Use prompts 02, 03, and 04 in order. The AI works through a checklist and tells you how to check each piece.
7. **Test it against the spec.** Every line in the spec should work. If one doesn't, fix the spec or the checklist and build again.

## What we already decided for you

Big decisions slow a project down, so we made a few ahead of time. They're written up in `docs/ADRs/` so the AI follows them without being told.

- **You're building a small embed.** One file that works on its own and can be placed on almost any website, course page, or intranet. No servers, no accounts, no installs. ([ADR-002](docs/ADRs/ADR-002-single-file-embed.md))
- **It has to be accessible.** Everyone, including people using a keyboard or a screen reader, can use what you build. ([ADR-001](docs/ADRs/ADR-001-digital-accessibility.md))
- **It doesn't collect personal information.** No names, emails, IDs, or grades.

If your project needs something different, that's fine. Change the decision on purpose, write down why, and tell the AI.

## What's in the folder

| Where | What it is |
|---|---|
| `README.md` | This page. |
| `AGENTS.md` | Instructions every AI tool reads first. You rarely need to touch it. |
| `CLAUDE.md` | A few extra notes for Claude. |
| `docs/SPEC.md` | What your tool must do. The AI fills this in with you. |
| `docs/TAD.md` | How it works and where it will live. |
| `docs/TASKS.md` | The build checklist. |
| `docs/ADRs/` | Decisions already made, and why. |
| `prompts/` | The four prompts, in the order you use them. |
| `skills/` | Know-how the AI uses, such as how to embed on a website. |
| `examples/` | A finished spec you can compare yours to. |
| `builds/` | Where finished tools go, one folder each. |

## Before you use it at work

Talk to your IT or web team before putting a tool in front of students, customers, or the public. They'll know where it can live and what's approved. The TAD has a section for exactly that conversation.

---

## Going deeper: why this works

*The rest of this page is for people who want to know what's going on underneath.*

### Spec-driven development

Asking an AI to "make a quiz" leaves it to guess hundreds of small things: how many questions, what happens on a wrong answer, whether there's a score, what it looks like on a phone. Every guess is a chance to be wrong. Spec-driven development (SDD) answers those questions in writing first, so the AI isn't guessing.

The workflow in this kit has four steps:

1. **Specify.** The AI interviews you and writes `SPEC.md`: what the tool must do.
2. **Plan.** The AI writes `TAD.md`: how the tool will do it.
3. **Tasks.** The AI breaks the plan into small, ordered steps in `TASKS.md`.
4. **Implement.** The AI builds one task at a time, and you check each one.

Because the decisions live in files instead of a chat, you can close the tool, come back next week, or switch to a different AI, and nothing is lost.

### EARS: how requirements are written

Every requirement in the spec follows one of five sentence patterns from EARS (Easy Approach to Requirements Syntax, developed by Alistair Mavin and colleagues at Rolls-Royce). The patterns make each requirement specific and testable.

| Pattern | Shape | Example |
|---|---|---|
| Ubiquitous | The *system* shall *response*. | The quiz shall show one question at a time. |
| Event-driven | When *trigger*, the *system* shall *response*. | When the learner submits an answer, the quiz shall show feedback. |
| State-driven | While *state*, the *system* shall *response*. | While a question is unanswered, the quiz shall keep Next disabled. |
| Unwanted behavior | If *condition*, then the *system* shall *response*. | If no answer is selected, then the quiz shall disable Submit. |
| Optional feature | Where *feature*, the *system* shall *response*. | Where audio is enabled, the quiz shall read questions aloud. |

More: https://alistairmavin.com/ears/

### TAD: the technical architecture document

The TAD answers "how does it do it, and where does it live?" It lists the components, which requirements each one covers, what data the tool stores (ideally none), and what is out of scope. Anything in the plan that doesn't trace back to a requirement gets cut. That rule is what keeps AI from adding features nobody asked for.

### ADRs: architectural decision records

An ADR records one decision, the context behind it, and its consequences. Its job is to stop the same question from being reopened every time someone (or some AI) touches the project. When you change a decision, add a new ADR that replaces the old one rather than editing history.

### AGENTS.md and CLAUDE.md

`AGENTS.md` is an emerging convention: a plain Markdown file at the root of a project that AI coding tools read for instructions. `CLAUDE.md` serves the same purpose for Claude specifically. Ours tell the AI to read the docs first, interview before building, stop for review, build only what the spec says, and follow the ADRs.

---

## Technical reference

### The embed contract (ADR-002)

Each tool is a single `index.html` in its own folder under `builds/`:

```
builds/
  lab-safety-quiz/
    index.html      <- HTML, CSS, and JavaScript in one file
```

- No external scripts, stylesheets, fonts, or images loaded from other sites. Images are inline SVG or data URIs.
- No build step, frameworks, or package installs. Opening the file in a browser runs it.
- No network requests, cookies, `localStorage`, or analytics unless the TAD says otherwise.
- Responsive from 320 px wide, and works inside an `<iframe>` (no pop-ups, no reliance on the parent page).
- Every function documented with JSDoc.

### Hosting and embedding

The simplest host is GitHub Pages from your copy of this repo:

1. In your repo, go to **Settings > Pages**, choose **Deploy from a branch**, branch `main`, folder `/ (root)`, and save.
2. Your tool will be at `https://<your-username>.github.io/<repo-name>/builds/<tool-folder>/`.
3. Embed it on another page with:

```html
<iframe
  src="https://<your-username>.github.io/<repo-name>/builds/<tool-folder>/"
  title="<Describe the tool, e.g., Lab safety self-check>"
  width="100%" height="600" loading="lazy"
  style="border:0; max-width:800px;">
</iframe>
```

The `title` attribute is required for accessibility. Many LMS editors (Canvas, CourseArc, and others) accept iframe embeds, but rules vary by institution, so confirm with your administrator. Any static host your IT team approves works the same way.

### Accessibility (ADR-001)

Target **WCAG 2.2 Level AA**, with WCAG 2.1 AA as the legal floor under the ADA Title II rule. Each build is checked three ways: a keyboard-only pass, an automated scan (WAVE, axe, or your institution's tool), and a screen reader spot check where possible. Automated tools catch only part of the problems, so the manual passes are not optional.

### Using a different AI tool

Any tool that reads files in your project works. If your tool doesn't read `AGENTS.md` automatically, start each session with: "Read AGENTS.md and follow it."

### Credits

Session materials by Jason Reiche and Gordon Inman, Rio Salado College (Maricopa Community Colleges).
