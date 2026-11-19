# agent-sdlc

A software lifecycle skill for AI coding agents: spec, writing code, design (UI, brand, and logo), testing, review, anti-slop checks, delegation, integration, release, handoff, and the repo harness that enforces the rules.

The files are written for agents: imperative, short, and checkable. `SKILL.md` is a router (under 80 lines) with a short overview of the flow and risk tiers, a "read by role" table, and a "read by task" table. Every file it names is one link away; no file links to a file the router does not also list. The skill assumes no particular agent runtime, vendor, or named roles.

## Point to it from your project

Skills trigger unreliably from their description alone. Paste these two lines into the project's always-loaded instructions (`AGENTS.md`, `CLAUDE.md`, or equivalent):

```markdown
## Development lifecycle
Before you plan, delegate, write, test, review, or hand off code, or design UI, a brand, or a logo, read the agent-sdlc skill (SKILL.md) and the files it lists for your role.
```

## Layout

```
SKILL.md                 router: flow, tiers, always-rules, role and task tables
SOURCES.md               every rule's basis, label, and confidence; disagreements; gaps
spec/                    index.md (sizing, criteria, sessions), design-note.md
writing-code/            index.md (diffs, names, dead code, commits), comments.md
testing/                 index.md (repro tests, test guarding, evidence, which tests pay)
review/                  index.md (process, rounds, size), checklist.md
roles/                   coordinator, implementer, reviewer, verifier, researcher
delegation/              index.md (one agent or many, one writer), brief.md
integrate-release/       index.md (merging, parallel workspaces, thin release notes)
handoff/                 index.md (definition of done, report)
harness/                 index.md (hooks, CI, sandbox, injection), instruction-files.md, audit.md
principles/              design.md, operations.md
failure-modes/           index.md
anti-slop/               index.md (pre-handoff sweep), copy.md, product.md
design/                  index.md (process, scope, report), floor-checks.md, brand.md, logo.md, logo-deliverables.md, mascot.md, foundations.md, components.md
sources/                 anti-slop.md, design.md, logo.md, foundations.md, components.md, verification.md (evidence split out of SOURCES.md)
```

## Evidence

Each rule traces to a row in `SOURCES.md` with a label (verified, secondhand, vendor, inference) and a confidence. Rules that rest mainly on inference are marked in their file; templates, checklists, and the principles files are engineering defaults, as `SOURCES.md` notes. The risk tiers, the three-round review cap, and the release section are defaults, not findings. Change them when your own results disagree.

The research behind this revision covered roles and orchestration, writing code, testing, review, spec and planning, integration and harness, and skill design. Earlier material came from the `durable-quality` and `principle-*` skills in this repo. The simplicity and surgical-change ideas in `writing-code/` draw on Andrej Karpathy's observations on LLM coding pitfalls, as collected in the `karpathy-guidelines` skill (multica-ai/andrej-karpathy-skills); that repo ships no LICENSE file, so the wording here is our own.

## Extending

- Put key rules first, keep the rule count per file low, write in the imperative, and give the reason for any rule that is not obvious.
- Keep files under about 120 lines. Open each with a "Read when..." line and end with a checkable "Done when" list.
- Add every new file to the router with its exact path. Keep references one level deep.
- Add a `SOURCES.md` row for every non-obvious rule. Label inference as inference. Do not invent numbers.
- No agent names, product names in rules, or personal or employer material.
- Validate: frontmatter parses as YAML (quote values that contain a colon); every relative link resolves.
- Test triggering and file use on the models you run, including small ones, before and after a change.
