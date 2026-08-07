# Code health review checklist

Senior principle: approve when the change improves overall code health; reject when it degrades code health (except true emergencies).

## Before reading the hunk

1. Read the PR intent / decision log
2. Skim test diffs first (especially agent PRs)
3. Note blast-radius paths touched (auth, money, migrations, workflows, CI)
4. Confirm CI required checks and whether workflows changed

## Design

- Does this belong in this codebase / package?
- Does it integrate with existing patterns, or invent a parallel one?
- Is now the right time for this functionality?
- Speculative generality present? Prefer solving the known problem.

## Functionality

- Does it do what the author intends?
- Is that intent good for users and future callers?
- Edge cases, concurrency, idempotency, permissions considered?
- For UI or ops-visible behavior, is there demo/evidence beyond unit green?

## Complexity

- Could this be simpler at line, function, and module level?
- Would another engineer modify this safely in six months?
- Nested control flow a smell (kernel-style: deep nesting means redesign)?

## Tests

- Appropriate unit / integration / e2e for the change?
- Tests correct, focused, and maintainable?
- Would tests fail if the behavior regressed?
- Fail-without-change evidence for behavior work?
- Avoid accepting complexity in tests "because they are not prod"

## Structure and reuse

- Duplicates an existing helper?
- Breaks layer/dependency rules?
- Introduces a cycle or new undeclared package?
- Public API surface changed without docs/changelog?

## Naming, comments, docs

- Names reveal intent?
- Comments explain why, not narrate what?
- User-facing docs / README / API notes updated when behavior changed?

## Style and consistency

- Matches project formatter and style guide?
- No mixed reformat + feature?
- Consistency with neighbors unless style guide says otherwise?

## Every line and context

- Understand every human-written line assigned
- Read surrounding file context, not only the hunk
- System-level: does code health rise or fall?

## Agent-specific addenda

- Run `checklists/agent-pr-gate.md` first
- Watch for CI gaming and assertion rewriting
- Prefer small follow-ups over landing a mudball

## Outcomes

- Approve / approve-with-nits / request changes / reject
- Label nits clearly so they do not block health-positive work
- Call out good craft when seen (mentoring signal)
