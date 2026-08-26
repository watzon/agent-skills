---
name: artifact
version: 0.1.0
description: >
  Publish an artifact as a live here.now page. Use when the user asks for an
  artifact, or when a report, explainer, dashboard, mockup, interactive
  example, or visual walkthrough would land better as a URL than as a chat
  reply. Load here-now to host it. Not for video, not for hosting files the
  user already has, and not for a throwaway prototype that must live in the
  repo.
license: MIT
compatibility: claude-code opencode cursor codex
---

# Artifact

An **artifact** is a self-contained page published with here.now. Chat is for talk. The artifact is the thing itself.

When a longer document, a visual, or something operable would serve better than a chat reply, build the page and publish it. Do not ask permission first unless the form is genuinely ambiguous.

## Stay in chat when

- The answer is a short fact, a command, or a yes or no.
- The user asked for code in the repo.
- The deliverable is video. That is `hyperframes`.
- The user already has files and only wants them hosted. That is `here-now` alone.
- The user wants a throwaway prototype next to production code. That is `prototype`.

If the choice is close, publish.

## Steps

**Done when** the publish directory has `index.html` at its root, no `SLOT` markers or placeholder copy remain, every control that looks live works, and the live `siteUrl` is printed on its own line.

1. Load `here-now` (`skill://here-now` or `~/.agents/skills/here-now/SKILL.md`). That skill owns hosting, credentials, slugs, claim URLs, and how you print the live link.
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
5. Publish with `here-now`:

   ```bash
   ~/.agents/skills/here-now/scripts/publish.sh {dir} --client opencode
   ```

   On revision, pass `--slug` from the prior run. Use `--spa` when unknown paths should serve `index.html`.

Then one or two lines: what the page shows, and what is still fake or temporary. If the publish was anonymous, say it expires in 24 hours and share the claim URL byte-for-byte, the way `here-now` requires.

Feedback edits the same files and republishes the same slug. When the user wants it built for real, turn the page plus their reactions into a short must / nice / cut list and wait for them to accept it.

Shared records (a form, poll, checklist, or anything multiple viewers write) need here.now Site Data. Read https://here.now/docs after loading `here-now` before you invent a store.
