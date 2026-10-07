# CLAUDE.md

Read `AGENTS.md` first. Everything there applies to you.

## Claude-specific notes

- When interviewing the user, use interactive questions if your interface supports them. Offer two to four likely answers plus a free-text option.
- When asked to plan, you may draft the technical design as a visual canvas or artifact for the room to see, but the source of truth is `docs/TAD.md`. Update the file.
- Prefer editing the documents in `docs/` over keeping decisions in the chat. If the user tells you something that changes a requirement, update `docs/SPEC.md` and say what changed.
- Before building, restate in one or two sentences what you are about to build and which requirements it covers.
