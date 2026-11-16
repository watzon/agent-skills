---
name: artifact
version: 0.1.0
description: "Create self-contained interactive pages for reports, explainers, dashboards, and mockups. Use here.now for publishing when that host is selected."
license: MIT
compatibility: claude-code opencode cursor codex
---

# Artifact

This skill builds self-contained pages and provides a here.now publishing workflow.

Use a page when it serves the requested deliverable. Preserve the user's chosen format and host. A request for an artifact does not by itself authorize publishing. Prepare and verify the local result first, then publish when authorized.

## Stay in chat when

- The answer is a short fact, a command, or a yes or no.
- The user asked for code in the repo.
- The deliverable is video. That is `hyperframes`.
- The user already has files and only wants them hosted. That is `here-now` alone.
- The user wants a throwaway prototype next to production code. That is `prototype`.

When the format is uncertain, use the request and existing context to choose a useful local deliverable.

## Steps

**Done when** the publish directory has `index.html` at its root, no `SLOT` markers or placeholder copy remain, every control that looks live works, and the requested output is available. For authorized publishing, verify and return the live `siteUrl`.

1. For authorized here.now publishing, load `here-now` (`skill://here-now` or `~/.agents/skills/here-now/SKILL.md`). That skill owns hosting, credentials, slugs, claim URLs, and how you print the live link.
2. Name the form in one line. Read only that form's reference, then copy its template:

   | Form | When | Read |
   | --- | --- | --- |
   | report | Prose read top to bottom: analysis, memo, plan, spec | `references/report.md` then `templates/report.html` |
   | explainer | Teach a mechanism, walk through a process | `references/explainer.md` then `templates/explainer.html` |
   | dashboard | Glance at numbers: KPIs, a chart, a breakdown | `references/dashboard.md` then `templates/dashboard.html` |
   | table | Browse, sort, or filter rows | `references/table.md` then `templates/table.html` |
   | mockup | One working interaction to react to | `references/mockup.md` then `templates/mockup.html` |

   A plan or memo is a utilitarian report. A landing page, game, or tool they will keep is an editorial mockup.
3. Read `references/design.md` before writing HTML. Read `references/diagrams.md` before drawing a figure. Apply `unslop` to every string the page shows. For an editorial mockup, also load `anti-slop-design`.
4. Write to a stable path so revisions update the same Site:
   - In a project: `./.artifacts/<short-name>/index.html`
   - Otherwise: `~/.herenow/artifacts/<short-name>/index.html`
5. When publishing is authorized, publish with `here-now`:

   ```bash
   ~/.agents/skills/here-now/scripts/publish.sh {dir} --client opencode
   ```

   On revision, pass `--slug` from the prior run. Use `--spa` when unknown paths should serve `index.html`.

Then one or two lines: what the page shows, and what is still fake or temporary. If the publish was anonymous, say it expires in 24 hours and share the claim URL byte-for-byte, the way `here-now` requires.

For authorized revisions to the published page, edit the same files and republish the same slug. When the user wants it built for real, turn the page plus their reactions into a short must / nice / cut list and wait for them to accept it.

Shared records (a form, poll, checklist, or anything multiple viewers write) need here.now Site Data. Read https://here.now/docs after loading `here-now` before you invent a store.
