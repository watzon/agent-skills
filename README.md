# Claude Code skills

Personal skills for [Claude Code](https://docs.anthropic.com/en/docs/claude-code).

## Skills

| Skill | Description |
|---|---|
| [artifact](./skills/artifact/) | Publish a report, explainer, dashboard, table, or mockup as a live here.now page |
| [durable-quality](./skills/durable-quality/) | Standing quality baseline for AI-assisted coding: intent, proof, structure, ownership, and risk-scaled review |

`artifact` routes the form, then loads `here-now` to host the page. Form rules live in `references/`. HTML shells live in `templates/`.

`durable-quality` includes references, checklists, playbooks, and examples. Load it before writing code to prevent vibe rot and keep quality high.

## Install

Clone the repository, then copy the skill into the shared skills directory:

```bash
git clone https://github.com/watzon/claude-code
cp -R claude-code/skills/artifact ~/.agents/skills/
cp -R claude-code/skills/durable-quality ~/.agents/skills/
```

`artifact` also needs the `here-now` skill:

```bash
npx skills add heredotnow/skill --skill here-now -g
```


## Contributing

Add each skill under `skills/<skill-name>/` with a required `SKILL.md`. Put detailed material in `references/`, reusable templates in `examples/`, and deterministic utilities in `scripts/`.

## License

MIT © Chris Watson
