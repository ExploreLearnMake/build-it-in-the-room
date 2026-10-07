# Skill: Building and embedding a single-file tool

**When to use this skill:** every build, unless a newer ADR replaces ADR-002.

## What to know

- The deliverable is `builds/<tool-name>/index.html`: one file with inline `<style>` and `<script>`. Use a short, lowercase, hyphenated folder name.
- Start the file with `<!doctype html>`, `<html lang="en">`, a meaningful `<title>`, and `<meta name="viewport" content="width=device-width, initial-scale=1">`.
- Use system fonts (`font-family: system-ui, sans-serif`). No web fonts, CDNs, or external images.
- Inside an iframe the page cannot assume its own height will grow. Keep the main view within about 600 px tall, or let it scroll inside the frame.
- Do not use `alert()`, `confirm()`, pop-up windows, or `window.top`. Show messages in the page.
- Announce feedback with a polite live region (`aria-live="polite"`).
- Document every function with JSDoc.

## Embed code to give the user

```html
<iframe
  src="https://<username>.github.io/<repo>/builds/<tool-name>/"
  title="<Short description of the tool>"
  width="100%" height="600" loading="lazy"
  style="border:0; max-width:800px;">
</iframe>
```

LMS editors (Canvas, CourseArc, and others) often accept iframes, but rules vary by institution. If a platform blocks iframes, link to the tool instead.

## Checklist before calling it done

- [ ] One file, opens and works with no internet connection.
- [ ] No requests to other domains (check the browser's Network tab).
- [ ] Works at 320 px wide and inside an iframe.
- [ ] Meets the ADR-001 checks.
- [ ] Embed code above filled in with the real URL and title.
