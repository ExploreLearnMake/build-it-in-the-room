# CLAUDE.md

Read `AGENTS.md` first. Everything there applies to you.

## Claude-specific notes

- When interviewing the user, use interactive questions if your interface supports them. Offer two to four likely answers plus a free-text option.
- The end product is always the single file `builds/<tool-name>/index.html` (ADR-002). You may also show it as a code artifact so people can preview and copy it, but the file in `builds/` is the deliverable. Keep the plan in `docs/TAD.md`, not in a separate canvas or chat.
- Prefer editing the documents in `docs/` over keeping decisions in the chat. If the user tells you something that changes a requirement, update `docs/SPEC.md` and say what changed.
- Before building, restate in one or two sentences what you are about to build and which requirements it covers.
