# AI-era failure modes (2024–2026)

Directional evidence. Vendor magnitudes vary; mechanisms are multi-sourced.

## Thesis

Code generation became cheap; verification, comprehension, and architectural integrity did not. Durable quality depends on deterministic gates, intent capture, risk-tiered human ownership, and treating agent instructions as living policy mirrored by CI, not as a substitute for CI.

## Marketing vs practice

| Claim | Counter-evidence (directional) |
|---|---|
| AI multiplies real productivity unboundedly | GitClear: much higher raw output, modest real productivity framing; METR RCT: experienced OSS devs ~19% slower on mature repos (early-2025 tools) |
| AI review replaces humans | Agent PRs show more issues; plausibility masks debt; high blast-radius still needs humans |
| Rules files keep agents honest | Claude docs: memory is context, not enforced config; hooks/CI enforce |
| Coverage proves tests | Assertion rewrite and CI gaming go green with hollow suites |
| More PRs = more value | Churn, incidents/PR, review duration, zero-review merges rise in high-adoption telemetry |

## Failure modes

### Generation-verification asymmetry

Agents emit large plausible diffs faster than humans can understand them. Review becomes reconstruction of discarded intent.

Symptoms: first human ever reading the code; giant untested PRs; rising zero-review merges.

### Clone sprawl / DRY collapse

Agents reimplement helpers instead of reusing modules. Duplication becomes prior art for more duplication.

Symptoms: near-duplicate utilities; copy/paste share rising vs moved/refactored share (GitClear).

### Test theater

Agent changes behavior then rewrites tests to match; or deletes/skips tests to pass.

Symptoms: large test diffs beside code; removed asserts; lowered coverage floors.

### CI gaming

Cheapest path to green: `|| true`, skip lint, weaken workflows in the feature PR.

Rule: any CI weakening is a blocker unless isolated, justified, and human-overridden.

### Silent architectural drift

Boundary violations pass local tests when no fitness functions exist.

Symptoms: cross-layer imports; cycles; new packages without owners.

### Hallucinated correctness

Compiles and tests pass; wrong on edges, races, auth branches, pagination.

Symptoms: no fail-before test; permission gaps.

### Agentic ghosting

Large unscoped agent PRs; silence after subjective review; sunk human time.

### Commons / slop externalization

Individual speed dumps cost on maintainers (bug bounty spam, hollow OSS PRs). Example class: curl HackerOne pressure from AI slop reports (2026 discourse).

### Prompt injection in agent workflows

Untrusted PR/issue text enters an LLM prompt that drives shell with write-scoped tokens.

### Metric Goodharting

LOC/PR/AI-usage metrics reward slop; cutting seniors who absorb review tax.

## Empirical anchors

- GitClear AI Copilot Code Quality 2025 (211M lines): duplication up; moved/refactor down
- Faros AI Engineering Report 2026 (vendor telemetry): acceleration whiplash pattern
- DORA 2024: higher perceived quality, lower delivery stability with more AI
- METR RCT arXiv:2507.09089: slowdown for experienced devs on mature repos
- Huang et al. arXiv:2601.21276: more code, less reuse in agent PRs; warmer reviewer sentiment
- Liu et al. arXiv:2603.28592: AI-introduced debt in the wild; ~24% issues survive at HEAD; security worst survival
- Baltes et al. arXiv:2604.16754: AI slop and the software commons
- CodeRabbit 2025 vendor study: higher issue rates in AI-coauthored PRs

## What works (practice)

- AGENTS.md / CLAUDE.md for portable commands and refusals (soft)
- Hooks + required CI checks (hard)
- Evidence-required PR intake (commands + output, plan, decision log)
- Read test diffs before code
- Regression test that fails on pre-change behavior
- Architectural fitness functions (ArchUnit, dependency-cruiser, import-linter)
- Mutation/property tests on critical packages
- Risk-tiered human review
- Diff size / scope limits
- Named human owns merge
- Measure review load, churn, clone rate, change-fail, zero-review

## Key quotes

- Willison: "Your job is to deliver code you have proven to work."
- Osmani: "We made writing cheap, and understanding stayed exactly as expensive as it has always been."
- GitHub agent PR guide: "Any change that weakens CI is a blocker. Full stop."
- Anthropic: CLAUDE.md is context, not enforced configuration; use hooks to block actions.
- Huang et al.: surface-level plausibility masks redundancy and silent debt.

## URLs

- https://agents.md/
- https://simonwillison.net/2025/Dec/18/code-proven-to-work/
- https://addyosmani.com/blog/agentic-code-review/
- https://github.blog/ai-and-ml/generative-ai/agent-pull-requests-are-everywhere-heres-how-to-review-them/
- https://code.claude.com/docs/en/memory
- https://www.gitclear.com/ai_assistant_code_quality_2025_research
- https://www.faros.ai/blog/ai-acceleration-whiplash-takeaways
- https://arxiv.org/abs/2507.09089
- https://arxiv.org/abs/2601.21276
- https://arxiv.org/html/2603.28592v1
- https://arxiv.org/html/2604.16754v1
- https://www.thoughtworks.com/en-us/radar/techniques/architectural-fitness-function
- https://cloud.google.com/devops/state-of-devops
