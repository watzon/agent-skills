# Agent skills

Personal skills for [Claude Code](https://docs.anthropic.com/en/docs/claude-code).

## Skills

| Skill | Description |
|---|---|
| [agent-sdlc](./skills/agent-sdlc/) | Lifecycle for AI coding agents: a router that sends each role or task to a few short, sourced files (spec, writing code, testing, review, delegation, harness) |
| [artifact](./skills/artifact/) | Publish a report, explainer, dashboard, table, or mockup as a live here.now page |
| [durable-quality](./skills/durable-quality/) | Standing quality baseline for AI-assisted coding: intent, proof, structure, ownership, and risk-scaled review |

The `principle-*` skills are situational playbooks (root-cause fixes, idempotent operations, type-system discipline, and more). They are read on demand and never self-trigger.

`artifact` routes the form, then loads `here-now` to host the page. Form rules live in `references/`. HTML shells live in `templates/`.

`durable-quality` includes references, checklists, playbooks, and examples. Load it before writing code to prevent vibe rot and keep quality high.

## Install

Clone the repository, then symlink each skill so this repo stays the source of truth:

```bash
git clone https://github.com/watzon/agent-skills ~/Projects/personal/agent-skills
ln -s ~/Projects/personal/agent-skills/skills/agent-sdlc ~/.agents/skills/agent-sdlc
ln -s ~/Projects/personal/agent-skills/skills/artifact ~/.agents/skills/artifact
ln -s ~/Projects/personal/agent-skills/skills/durable-quality ~/.agents/skills/durable-quality
```

For `agent-sdlc`, also paste the two-line pointer from [its README](./skills/agent-sdlc/README.md#point-to-it-from-your-project) into each project's `AGENTS.md` or `CLAUDE.md`, so agents find it.

`artifact` also needs the `here-now` skill:

```bash
npx skills add heredotnow/skill --skill here-now -g
```


## Contributing

Add each skill under `skills/<skill-name>/` with a required `SKILL.md`. Put detailed material in `references/`, reusable templates in `examples/`, and deterministic utilities in `scripts/`.

## License

MIT © Chris Watson
