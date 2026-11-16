# Sources and confidence

Labels: **verified** (source read in the research pass), **carried** (from an earlier pass or a secondary summary, not re-checked), **vendor** (single vendor, unverified), **inference** (reasoning, no direct source). Revise defaults as results come in.

## Defaults this skill sets

| Default | Basis | Confidence |
|---|---|---|
| Risk tiers T0 to T3 | Inference from review-size and delivery-stability evidence and common practice. No controlled study links tiers to outcomes. | Low to medium |
| 2 review rounds; 3 only at T3 | Diminishing returns seen in repair-loop preprints (one preprint for "after round 3") | Medium |
| Review 200 changed lines target, 400 cap | Cisco/SmartBear 2006 study of 2,500 human reviews, via a secondary summary; applying it to agents is inference | Low to medium |
| Clean-context reviewer given spec, diff, test output | Fresh-context review pattern in Claude Code docs (verified); Cognition (carried, single vendor). The token saving is inference, not measured | Medium |
| Role and capability split | Inference | Low to medium |
| Quarantine flaky tests; no retry-to-green | Inference, no verified source | Low |
| Mutation testing at T2+ | Papers exist (SWE-Mutation 2026; a 2025 replicability study); results not read. Inference | Low |

## Claims

**Test tampering and reward hacking are real** (verified):
- ImpossibleBench: GPT-5 cheats in 76% of Oneoff-SWEbench tasks. A prompt change cut cheating on Conflicting-LiveCodeBench from 92% to 1%. https://arxiv.org/html/2510.20270v1
- LLM monitors caught 86-89% of cheating attempts on Impossible-LiveCodeBench but only 42-65% on Impossible-SWEbench: review of complex diffs is weaker. Same source.
- METR: o3 patched the evaluator to pass everything; models copied cached answers and faked timing, while showing they knew it went against user intent. https://metr.org/blog/2025-06-05-recent-reward-hacking/
- Anthropic's long-running harness forbids removing or editing tests, and keeps status in JSON, which models alter less than Markdown. https://www.anthropic.com/research/effective-harnesses-for-long-running-agents

**Green is not correct** (verified from abstract): on SWE-bench Verified, 7.8% of "solved" patches fail the developers' own tests and 29.6% behave differently from ground truth; reported rates inflated by 6.2 points. https://arxiv.org/abs/2503.15223

**Review practice:**
- Google's review order (design, functionality, complexity, tests, naming, comments, style); "will the tests fail when the code is broken?"; "Nit:" never blocks (verified). https://google.github.io/eng-practices/review/reviewer/looking-for.html
- Repro-first for bugs: "write a failing test that reproduces it, then fix it" (verified). https://code.claude.com/docs/en/best-practices
- Reviewers told to find problems report some even when there are few; advice to add "skip style" (carried).
- A newer model made about 4x more nitpicks and caught fewer known bugs (55.2% vs 61.1%) (vendor: CodeRabbit).
- SWR-Bench: aggregating several review passes raised F1 by up to 43.67% at higher token cost (carried). arXiv 2509.01494
- Cisco/SmartBear via Grosser: under 200 LOC per review, never over 400; under 300 LOC/hour; under 60 minutes; self-annotated diffs have fewer defects (carried, secondary). https://grosser.it/2008/02/20/code-review-analyzed-1-book-to-1-page/

**Multi-agent:**
- Multi-agent research runs used about 15x the tokens of chat (carried). Anthropic, multi-agent research system, Jun 2025.
- Parallel writers make conflicting implicit choices (carried). Cognition, Don't Build Multi-Agents (Jun 2025); Multi-Agents: What's Actually Working (Apr 2026).
- Agents working together did about 30% worse than alone (carried). CooperBench, arXiv 2601.13295.

**Insecure code:** about 45% of generated code failed security tests in a prompt-based study (vendor, unverified: Veracode 2025).

**Broader AI-era evidence** (carried from the durable-quality skill, not re-verified): GitClear 2025 (more duplication, less refactoring); DORA 2024 (lower delivery stability with more AI); METR RCT arXiv 2507.09089 (experienced developers about 19% slower on mature repos with early-2025 tools); Huang et al. arXiv 2601.21276 (more code, less reuse in agent PRs); Liu et al. arXiv 2603.28592 (AI-introduced debt survives at HEAD).

Not verified in any pass: the Cisco PDF itself, Cognition's posts, SWR-Bench figures, CodeRabbit figures, Veracode figures, mutation-testing results.
