# Sources

Evidence behind each rule. Labels are the research pass's: **verified** (source read), **secondhand** (via a summary, snippet, or quote), **vendor** (a company's claim about its own product or practice), **inference** (reasoning, no direct source). Confidence (0 to 1) is the research pass's judgment of how well the rule is supported. Most evidence is from 2025 to 2026, small, and often preprints. Change a default when your own results disagree.

Anti-slop and design evidence is split out: [sources/anti-slop.md](sources/anti-slop.md), [sources/design.md](sources/design.md), [sources/foundations.md](sources/foundations.md), and [sources/components.md](sources/components.md).

## Router and tiers

| Rule | Basis | Label | Conf. |
|---|---|---|---|
| Tiers T0 to T3 and their review/human columns | Built on Anthropic's internal tiers (low risk: no human once checks pass; medium: one person; high: two; auth, billing, CI files always need a person; agent approval never counts) [1] | vendor + inference | 0.5 |
| Router with exact paths, role table, short "Use when" description | [21] [22] [23]; agents rarely search for the right file [24] | verified | 0.85 |
| Pointer from AGENTS.md / CLAUDE.md | One study: indirect requests fired a skill in 15% of runs; a session-start reminder raised it to 62% [25] | verified, single study | 0.6 |

## Writing code and comments (writing-code/)

| Rule | Basis | Label | Conf. |
|---|---|---|---|
| Never write history in comments; current state only | Agents followed a stale instruction file in 90.1% of choices [2]; followed stale guidance and never repaired it [3]; zero-comment, no-history rule in a production AGENTS.md [4] | verified | 0.9 |
| Fix or delete a comment your change makes false | 63.2% of AI-authored PRs changed code without updating docs [5] (documentation files, not inline comments); [3] | verified | 0.85 |
| Default to zero comments; keep a non-obvious "why" | Removal neutral or slightly better for strong models [6] [7]; comments from correct solutions raised pass@1 17.2%, unrelated ones cut it 20.8% [8]; [4] | verified | 0.7 |
| Don't strip a real "why" | A stripped branch needed lint directives restored [7]; an agent replaced a fencepost reason with a restatement (anecdote) [7] | verified / anecdote | 0.6 |
| History goes in commits and PR text | [4] (PR body) | verified | 0.85 |
| Small diffs, no parallel abstraction, cleanup in its own change | [4]; cleaner code used 7 to 8% fewer tokens, same pass rate [9] (vendor interest); Willison dissents on cleanup [10] | verified + vendor | 0.65 |
| Reuse before writing | Agent PRs add redundancy ("More Code, Less Reuse", arXiv 2601.21276) [11] | secondhand | 0.6 |
| Greppable names over comments; readable, not golfed | Ronacher on terse code leaking into codebases [12]; distraction was the top failure cause in [6] | secondhand + inference | 0.55 |
| Two failed attempts, then stop | No source | inference | 0.4 |

## Testing (testing/)

| Rule | Basis | Label | Conf. |
|---|---|---|---|
| Repro test per bug, seen failing | "Write a failing test that reproduces it, then fix it" [13]; red/green: confirm the test fails first [14] | verified | 0.85 |
| Do not edit existing tests; enforce it | GPT-5 passed spec-contradicting tests in 76% of one-off SWE-bench tasks; a prompt change cut one variant from 92% to 1% [15]; harness forbids editing tests [16]; "never modify existing tests" (OpenAI, quoted) [17] | verified / secondhand | 0.8 |
| Evidence is command and output | [13] | verified, vendor doc | 0.8 |
| Must-run checks in hooks/CI; no "always run tests" | [13]; generic run-tests instructions reported to backfire (TDAD study, not read) [17] | verified / secondhand | 0.75 |
| No TDD by default in the loop | No quality gain, 2.96x to 8.5x tokens, agents faked the red step; small n, greenfield [18] | verified | 0.5 |
| Mutation testing as periodic sensor | Thoughtworks Radar: Adopt; coverage easy to inflate [19]; reliable only in regression-style settings [20] | verified | 0.6 |
| Integration over mock-heavy units; contract, property tests | Tautological tests [18]; "green mocked tests do not prove the UX" [26]; the rest | verified / inference | 0.5 to 0.6 |
| Green is not correct | 7.8% of "solved" SWE-bench patches fail developer tests; 29.6% diverge from ground truth (arXiv 2503.15223) | verified (abstract) | 0.8 |
| Quarantine flaky tests | No source | inference | 0.4 |
| Scoped tests while working; configured integration gate before merge | Research suggests targeted tests in later rounds and full CI at integration, as its own inference | inference | 0.5 |

## Review (review/)

| Rule | Basis | Label | Conf. |
|---|---|---|---|
| Checks and output before review | [1]; [26]; give the agent something to run [13] | verified, vendor | 0.85 |
| Fresh-context reviewer with spec, diff, test output | [13]; [1]; clean-context reviewer [27] | verified, vendor | 0.8 |
| Blocking vs nit; nits never block | Important / Nit / Pre-existing tags [28]; Google "Nit:" [29] | verified | 0.8 |
| Stop at no blockers; cap 3; re-review new diff; escalate | Review did not converge (one PR ran 50+ rounds); capped at three [1] | vendor | 0.6 |
| Escalate on a repeat finding or a second dispute | Earlier research pass | inference | 0.5 |
| Size: about 100 lines fine, 1,000 too large; count files | Google eng-practices [30] | verified | 0.5 |
| Cross-model review optional | Benefit was one-directional in one preprint [31]; same-model judges fine if they match human labels [32] | verified, one study | 0.45 |
| Findings cite file:line and evidence | [1]; [11] | verified, vendor | 0.7 |

## Spec (spec/)

| Rule | Basis | Label | Conf. |
|---|---|---|---|
| Size the spec to the change | A small bug became 4 user stories and 16 criteria [33]; one rebuild: 33 min agent time and 3.5 h review vs about 8 min and 15 min (one author, no control) [34]; Radar: Assess [35] | verified | 0.8 |
| Checkable criteria, test-first | Feature list where only `passes` changes [16]; [14] | verified | 0.85 |
| Gather, then build in a fresh session | Interview until it adds up to a spec, then a fresh session [13] | verified, vendor doc | 0.7 |
| One verifiable unit per session | [16]; one task per loop [36] | verified | 0.8 |
| No prose specs kept in sync by default | One team dropped repo-resident specs [37]; that report is vendor-written, by the team's own firm; context files add cost without raising success [38] | vendor + verified, one study | 0.55 |
| Design note: data first, short, alternatives optional | Data-first is carried from the design principles; length and alternatives rules have no source | inference | 0.4 |
| Ask only on costly-to-reverse decisions | No source counts questions | inference | 0.4 |

## Roles and delegation (roles/, delegation/)

| Rule | Basis | Label | Conf. |
|---|---|---|---|
| Single agent by default | 180 configurations: +81% on parallel work, −39 to −70% on sequential planning; independent agents amplified errors up to 17.2x [39]; ~15x chat tokens for multi-agent [40] | verified (blog) | 0.8 |
| One writer; parallel reads and reviews | [27]; disjoint claims can work [41] | verified | 0.8 |
| Brief: objective, output format, tools/sources, boundary, decisions | [40]; implicit decisions cause conflicts [42] | verified | 0.85 |
| Coordinator does not write code (default) | No source states it; from context-isolation arguments [40] [27] | inference | 0.55 |
| Results as file path + summary | [40]; [43] | verified | 0.75 |
| Merge in dependency order | No source found | inference | low |

## Harness and release (harness/, integrate-release/)

| Rule | Basis | Label | Conf. |
|---|---|---|---|
| Must-rules in hooks, CI, protection | [13] | verified | 0.9 |
| Server-side gates; sandbox by default | Radar: sandboxing Adopt, pipeline responsibility Assess [44] | verified | 0.85 |
| Lethal trifecta | [45]; Fowler/Sietsma [46] | verified | 0.85 |
| No reliable prompt-level defense | Schneier, as quoted in [46] | secondhand | 0.6 |
| Completion gate with an escape hatch | Stop-hook proof file pattern [47] | secondhand | 0.75 |
| Fast tools; per-edit hooks disputed | [48] | verified (2025) | 0.6 |
| Short pointer-style instruction files; re-check after model change | [13]; [38]; Codex 32 KiB budget [49]; re-audit advice [12] (secondhand) | verified / secondhand | 0.6 to 0.7 |
| Worktree traps | One team's report [50] | verified, small sample | 0.6 |
| Auto-merge only at low risk | Autonomous merge [26] vs risk-tiered oversight [44] [46] | verified; tiering inference | 0.65 |
| Release, flags, rollback, observability | No sources read | inference | 0.4 |

## Where people disagree

- **Comments:** content matters [8] vs removal neutral or better [6] [7]. Reconciled view: the content helps; wrong content hurts most. Effects vary by model.
- **Cleanup in the same change:** yes, it is cheap [10]; no, keep diffs minimal [4].
- **Test-first in the loop:** strong yes [14]; no measured gain at 3x+ cost [18]. One team dropped many slow tests [12] (secondhand).
- **Round cap:** three [1]; loop until all reviewers agree, no cap (tstack `council`) [26].
- **Merge without a human:** low risk can auto-merge [1]; every agent PR needs a person (GitHub) [11]; solo projects may defer.
- **Multi-agent:** fragile [42] vs +90.2% on a research eval [40]; parallel writers fail [27] vs work with locks [41].
- **Specs as source of truth:** yes (Spec Kit, Tessl) vs "code is the law" [33].
- **Hooks:** the only deterministic layer [13] vs costly and bypassed in permissive modes [48].

## Gaps the research flagged

Merge order; release, flags, rollback, and observability for agent code; flaky-test and test-maintenance cost; independent review-tool comparisons that score false positives; router-style skills specifically; how many clarifying questions to ask; long-horizon effects of agent-written comments. Not read: the TDAD paper, the full Google scaling paper, OpenAI harness-engineering post, the ASE 2026 stale-comments paper.

## References

[1] Anthropic, Solving code review at Anthropic, https://claude.dev/blog/solving-code-review-at-anthropic/ · [2] https://arxiv.org/abs/2610.30571 · [3] https://arxiv.org/abs/2611.09802 · [4] assistant-ui PR #4174, https://github.com/assistant-ui/assistant-ui/pull/4174 · [5] https://arxiv.org/abs/2610.27381 · [6] https://antimemetics.institute/comment-ablation · [7] https://epeicher.github.io/wairehouse/openstation/experiments/comments-ab.html · [8] https://aclanthology.org/2026.findings-emnlp.916/ · [9] https://arxiv.org/abs/2605.20049 · [10] https://simonwillison.net/guides/agentic-engineering-patterns/better-code/ · [11] https://github.blog/ai-and-ml/generative-ai/agent-pull-requests-are-everywhere-heres-how-to-review-them/ · [12] https://zeronoise.ai/posts/models-are-skipping-the-edit-tool-ronacher-and-huntley-on-code-mode-stale-agentsmd-files-and-harness-design-7dkfd10szww4nmcx · [13] https://code.claude.com/docs/en/best-practices · [14] https://simonwillison.net/guides/agentic-engineering-patterns/red-green-tdd/ · [15] https://arxiv.org/abs/2510.20270 · [16] https://www.anthropic.com/research/effective-harnesses-for-long-running-agents · [17] https://codex.danielvaughan.com/2026/06/05/why-always-run-tests-agents-md-makes-things-worse/ · [18] https://www.martinfowler.com/articles/exploring-gen-ai/tdd-in-the-agent-loop.html · [19] https://www.thoughtworks.com/radar/techniques/mutation-testing · [20] https://arxiv.org/abs/2607.22880 · [21] https://agentskills.io/specification · [22] https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices · [23] https://github.com/obra/superpowers/blob/main/skills/writing-skills/SKILL.md · [24] https://arxiv.org/abs/2604.04323 · [25] https://towardsdatascience.com/a-session-start-hook-raised-claude-code-skill-firing-from-15-to-62/ · [26] https://github.com/t3dotgg/tstack · [27] https://cognition.com/blog/multi-agents-working · [28] https://code.claude.com/docs/en/code-review · [29] https://google.github.io/eng-practices/review/reviewer/looking-for.html · [30] https://google.github.io/eng-practices/review/developer/small-cls.html · [31] https://arxiv.org/abs/2607.21656 · [32] https://hamel.dev/blog/posts/evals-faq/can-i-use-the-same-model-for-both-the-main-task-and-evaluation.html · [33] https://www.martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html · [34] https://blog.scottlogic.com/2025/11/26/putting-spec-kit-through-its-paces-radical-idea-or-reinvented-waterfall.html · [35] https://www.thoughtworks.com/radar/techniques/spec-driven-development · [36] https://ghuntley.com/loop/ · [37] https://talkthinkdo.com/ai-velocity-report/moving-away-from-openspec/ · [38] https://arxiv.org/abs/2602.11988 · [39] https://research.google/blog/towards-a-science-of-scaling-agent-systems-when-and-why-agent-systems-work/ · [40] https://www.anthropic.com/research/multi-agent-research-system · [41] https://www.anthropic.com/research/building-c-compiler · [42] https://cognition.com/blog/dont-build-multi-agents · [43] https://lucumr.pocoo.org/2025/11/21/agents-are-hard/ · [44] https://www.thoughtworks.com/en-us/radar/techniques/agent-sandboxing · [45] https://simonwillison.net/2025/jun/16/the-lethal-trifecta/ · [46] https://martinfowler.com/articles/agentic-ai-security.html · [47] https://marcindudek.dev/blog/claude-code-quality-gates-stop-hook/ · [48] https://lucumr.pocoo.org/2025/7/30/things-that-didnt-work/ · [49] https://learn.chatgpt.com/docs/agent-configuration/agents-md · [50] https://slowbench.com/blog/agents/four-traps-merging-parallel-agent-worktrees

Design and operating principles ([principles/](principles/design.md)) are engineering judgment carried from earlier skills in this repo, not agent research.
