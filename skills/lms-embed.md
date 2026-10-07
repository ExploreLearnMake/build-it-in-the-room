# Skill: Embedding a tool in an LMS page

**When to use this skill:** the TAD says the tool will be embedded in an LMS page (for example, Canvas or CourseArc).

## What to know

- Most LMS rich-content editors remove `<script>` tags pasted into a page. A working interactive usually has to be hosted somewhere else and embedded with an `<iframe>`, or added through a tool your LMS administrators have approved.
- The tool must work inside a frame: no pop-up windows, no reliance on the top-level page, and a layout that fits a narrow column.
- Give every `<iframe>` a meaningful `title` attribute so screen reader users know what it contains.
- Hosting options and what is allowed vary by institution. Confirm with your LMS administrator or IT before publishing anything student-facing.

## Checklist

- [ ] The tool is one self-contained HTML file, or the TAD names the approved host.
- [ ] It works at 320 px wide and inside an iframe.
- [ ] The embed code includes a descriptive `title`.
- [ ] No student data leaves the page unless the TAD says where it goes and IT approved it.
