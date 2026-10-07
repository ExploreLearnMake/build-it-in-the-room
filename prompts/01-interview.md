# Prompt 1: Interview me, then write the spec

Paste this into your AI tool with this folder open.

```
Read AGENTS.md and follow it.

I want to build: [one sentence about your tool idea].

Before you write any code, interview me. Ask one question at a time about:
- who will use this tool and on what device
- the one job it must do
- what it must not do
- which page or site it will be embedded on
- how we will know it works

Do not ask about technology, hosting, or data storage; ADR-002 already
decides those. Keep it to about six questions. When you have enough, write docs/SPEC.md using
EARS requirements with IDs (R1, R2, ...), an "Out of scope" list, and a
"Done when" checklist. Then stop and wait for my review.

After I approve the spec, challenge it: list the three weakest requirements
and what could go wrong with each.
```
