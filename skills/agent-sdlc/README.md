# agent-sdlc

A software lifecycle skill for AI coding agents. It covers spec, design, implementation, testing, review, integration, release, and handoff, plus roles, delegation, engineering principles, failure modes, and repo audits.

The content is written for agents: imperative, short, and checkable. `SKILL.md` is a small router (under 80 lines). An agent loads it, picks its risk tier, and reads only the directory for its current step. It assumes no particular agent runtime, vendor, or named roles.

## Layout

```
SKILL.md          router, always-rules, risk tiers T0-T3
SOURCES.md        evidence behind the defaults, with confidence labels
01-spec/ ... 08-handoff/   one directory per stage; index.md = steps, artifact, done-when
05-review/code-health.md   second-pass review for T2+
roles/            coordinator, implementer, reviewer, verifier, researcher; mapping when no roles exist
delegation/       one agent vs many, splitting, brief template
principles/       one file per principle, each opening with its "Apply when..." trigger
failure-modes/    signals, checks, and guards for common agent failures
audit/            repo scorecard, CI/ownership harness, writing AGENTS.md
```

Why this cut: stages answer "what do I do now", roles answer "what is my job", and principles answer "how do I think about this". Each is read on its own trigger. The agent-PR gate lives in `05-review` (a reviewer needs it during review), and `audit/` links to it instead of copying it.

## Sources

Merged and condensed from:
- `durable-quality` and its references (this repo): standing rules, proof ladder, review checklists, audit scorecard, harness and agent-rules playbooks. The T0-T5 proof ladder was folded into T0-T3: old T3 (parsers, state machines) went to T2, and old T4-T5 went to T3.
- The 12 `principle-*` skills (this repo): one file each, tightened, with links to missing skills removed and overlap resolved by linking.
- The hub skills `agent-sdlc` (draft) and `multi-agent-orchestration`: tiers, stages, review rules, round caps, failure modes, handoff format, delegation rules, brief shape.
- A research report on agent SDLC practice: sourced claims and confidence labels, kept in `SOURCES.md`.
- `principles/behavior.md` paraphrases the four ideas (think before coding, simplicity, surgical changes, goal-driven execution) from the `karpathy-guidelines` skill by forrestchang/multica-ai (https://github.com/multica-ai/andrej-karpathy-skills), which draws on Andrej Karpathy's observations on LLM coding pitfalls. That repo declares MIT in its README and skill frontmatter but ships no LICENSE file with a copyright notice, so the text here is our own wording, not a copy.

## Confidence

The tiers, round cap, and review-size limits are defaults, not findings. Their basis and confidence are in `SOURCES.md`. Claims labeled inference are reasoning, not evidence. Change the numbers when your own results disagree.

## Extending

- New stage or topic: add a directory with `index.md` that opens with a one-line "Read when..." trigger and ends with a checkable "Done when" list. Add one row to the router table.
- New principle: add `principles/<name>.md` opening with "Apply when...", then a row in `principles/index.md`.
- Keep files under about 120 lines. Link to an existing file instead of repeating its point.
- No agent names, product names, or employer material in the skill files.
- Validate: `SKILL.md` frontmatter must parse as YAML (quote values containing a colon), and every router link must resolve.
