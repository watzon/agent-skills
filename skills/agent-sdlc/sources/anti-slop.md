# Sources: anti-slop

Evidence behind [anti-slop/](../anti-slop/index.md). Labels and confidence as in [SOURCES.md](../SOURCES.md). Research pass: 2026-11-16. Most of this evidence is practitioner guidance and incident reports, not measurement.

## Sweep (anti-slop/index.md)

| Rule | Basis | Label | Conf. |
|---|---|---|---|
| Sweep the diff, not the repo | Avoids flagging old code; no source | inference | 0.6 |
| Prose tells count only in clusters | Pattern catalog's false-positive rule [5]; signs are not proof [4] | verified | 0.6 |
| Never frame a finding as AI authorship | [4]; em dash is not a detector [8] | verified / secondhand | 0.9 |
| Mechanical vs judgment split | Research pass's classification of each rule | inference | 0.7 |

## Copy (anti-slop/copy.md)

| Rule | Basis | Label | Conf. |
|---|---|---|---|
| Say a fact once | GOV.UK: start with less, drop words [1] | verified | 0.85 |
| Label plus value over prose | [1]; NN/g UI copy [2] | verified | 0.8 |
| Fix the interface instead of explaining it | "If you find yourself having to explain how the user interface works... fix the interface" [1] | verified | 0.75 |
| Labels 4 words or fewer, no articles, name the result | Command labels 2 to 4 words, remove articles, describe the resulting state [2] | verified | 0.85 |
| No "please", "thank you", routine "sorry" | [1] | verified | 0.75 |
| Keep full content for errors and destructive confirmations | Practitioner account, n=1 [3]; [1] warns against unclear fragments | secondhand | 0.8 |
| Lead with the answer; length follows decisions; one next step | [3]; vendor prompting guide: models run long by default, prompt for concision explicitly [6] | secondhand / vendor | 0.6 |
| Dashes as house preference | Rates vary 0 to 9.1 per 1,000 words across 12 models (single-author preprint) [7]; a peer-reviewed counterexample, via a review [8]; editors removed 23% of 254 em dashes in post-editing (n=81) [9] | secondhand | 0.9 that it is a preference; 0.3 that it signals quality |
| Watch-list words as a review aid | Population-level excess vocabulary in abstracts [10], says nothing about one document | secondhand | 0.6 |
| Length rules alone fail | LLM judges prefer longer answers [11]; length in preference training (abstracts only) | verified abstract / secondhand | 0.7 judges; 0.5 training link |

The worked example in copy.md is a real billing page reviewed during research, described without product names. It had no dashes; its problem was one fact stated four times plus two explanatory sentences.

## Product (anti-slop/product.md)

| Rule | Basis | Label | Conf. |
|---|---|---|---|
| Compat existence test (consumer, persisted data, deployed user) | A maintainer rule banning compat because "this project has no external consumers" [12]; a PR that removed six shims and added a greenfield-first rule [13]; the three-question test itself is inference | verified + inference | 0.75 |
| Keep cheap-now items (version fields, logs, timestamps, raw data) | YAGNI exceptions essay [14] | verified, practitioner | 0.6 |
| No UI for unbuilt phases; real waitlist excepted | Practitioner catalogs that disagree [15] [16] | secondhand | 0.6 |
| Delete unused code; no "removed" comments or `_unused` renames | Third-party extraction of an agent system prompt [17] | secondhand | 0.7 |
| Inline settled flags, delete flag, config, tests | Vendor report on agent cleanup of dead flag branches [18]; automated stale-flag removal [19] | vendor / secondhand | 0.7 |
| Every config key has a reader | Mechanically checkable; no source | inference | 0.7 |
| No mock data in product code | Incident reports: an agent "faked data" [20]; a user report of mock data despite a rule [21] | secondhand / verified anecdote | 0.6 |
| No invented numbers, on screen or in reports | Self-reported post-mortem: 94% of claimed results fabricated [22]; [20] | vendor / secondhand | 0.6 |
| Agents add removable code | 2.6% of 12,343 added methods deleted before merge; 9.9% in PRs with revisions (Python only) [23]; repeated logic over reuse [24] | verified | 0.7 |
| Sweep tool names (knip, vulture, staticcheck, cargo-machete, jscpd) | Recalled during research, not checked | inference | 0.8 that they exist |

## Where people disagree

- **Compat.** No compat at all [12] [13] vs design for changes you can already see [14] [25]. Resolved by the existence test, not by the word "greenfield".
- **Visible unbuilt features.** No "coming soon" without a backing build [15] vs a real waitlist is fine [16]. The rule takes the stricter side plus the waitlist exception.
- **Em dashes.** A model-specific habit [7] vs not a detector [8]; the cause (markdown habits in training) is a hypothesis. Banning the glyph moves the tell to "--", colons, or semicolons; rules target repetition and padding instead.
- **Deletion rate.** Quote 2.6% and 9.9% with their denominators, never one alone [23].
- **Brevity.** Cut words [1] vs over-cutting yields fragments [3]. Errors and destructive confirmations are the stated exception.

## Gaps

- No controlled study of verbosity or repetition in UI copy; copy rules 1 to 7 rest on guides.
- One major platform's style guide not checked; two platform guides loaded as snippets only.
- No study of placeholder UI, impossible-case guards, or product-stage declarations in agent output.
- Dead-flag removal by agents: one vendor case, no replication.
- Mock data and fake metrics: incident reports only, no rate.

## References

[1] https://www.gov.uk/service-manual/design/writing-for-user-interfaces · [2] https://www.nngroup.com/articles/ui-copy/ · [3] https://danhopwood.com/posts/be-concise-is-the-wrong-instruction · [4] https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing · [5] https://github.com/soodoku/on-writing/blob/master/skills/on-writing/references/ai-patterns.md · [6] https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices · [7] https://arxiv.org/abs/2603.27006 · [8] https://www.gunvir.ca/papers/why-llms-seem-to-overuse-em-dashes.html · [9] https://arxiv.org/abs/2604.24444 (Baumler et al., ACL 2026; n=81 checked in the abstract, the dash figure not checked) · [10] https://www.science.org/doi/10.1126/sciadv.adt3813 · [11] https://arxiv.org/abs/2310.10076 · [12] https://github.com/prisma/prisma-next/blob/main/.agents/rules/no-backward-compatibility.mdc · [13] https://github.com/protoLabsAI/protoMaker/pull/886 · [14] https://lukeplant.me.uk/blog/posts/yagni-exceptions/ · [15] https://auditbuffet.com/patterns/ab-000274 · [16] https://alrighthq.com/checklist/technical/basics/no-lorem-ipsum/ · [17] https://github.com/Piebald-AI/claude-code-system-prompts/blob/main/system-prompts/system-prompt-doing-tasks-no-compatibility-hacks.md · [18] https://www.uber.com/us/en/blog/ai-code-cleanup/ · [19] https://dl.acm.org/doi/10.1145/3377813.3381350 · [20] https://www.theregister.com/software/2025/07/21/vibe-coding-service-replit-deleted-production-database/719783 · [21] https://github.com/anthropics/claude-code/issues/6984 · [22] https://getgodmode.dev/blog/one-shot-beta-the-verification-run.html · [23] https://arxiv.org/abs/2602.17091 · [24] https://arxiv.org/abs/2601.21276 · [25] https://simonwillison.net/guides/agentic-engineering-patterns/code-is-cheap/
