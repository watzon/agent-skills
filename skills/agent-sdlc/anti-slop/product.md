# Product leftovers

Read when adding or reviewing compatibility code, flags, settings, placeholder UI, or anything that shows data. Code-level rules (no speculative abstraction, no guards for impossible states) are in [writing-code/index.md](../writing-code/index.md); they are not repeated here.

## Rules

1. **Compatibility needs a consumer.** Before adding a shim, fallback, deprecation path, alias, re-export, or migration, answer three questions:
   - Is there an external consumer: a published API, a plugin, a client not shipped with this code?
   - Is there persisted data from an older version: rows, files, cached config?
   - Is there a deployed user on the old behavior?

   If all three are no, add no compatibility code; change every caller instead. If any is yes, keep compatibility at that boundary only and give the reason in the commit or PR text. Project instructions that declare the stage (unreleased or in production) settle the question.
2. **Unbuilt phases leave no trace in the product.** No code, nav entry, tab, disabled button, or "coming soon" text for work not built yet. The roadmap lives in issues or docs. Exception: the product owner asked for a waitlist, and it really captures sign-ups.
3. **Keep what is cheap now and costly later,** even in a new project: a version field on formats and protocols whose other end you do not control, logs, creation timestamps, and raw data you may need. These are not compatibility code.
4. **Delete, do not mark.** Remove unused variables, exports, and re-exports. No "removed" or "deprecated" comments, no renaming to `_unused`. If you are sure it is unused, delete it.
5. **Inline settled flags.** When a flag is fully on or fully off, delete the flag, its dead branch, its config, and its tests in the same change.
6. **Every config key has a reader.** A setting no code reads is deleted.
7. **No mock data in product code.** Non-test code holds no sample rows, fake names, or seeded records. Fixtures live in test paths. A demo, if requested, is labeled and removed before handoff.
8. **No invented numbers.** Every number on screen comes from a query or an input. If the query does not exist, the number does not ship. The same holds for reports: never state a test count, score, or metric you did not get from a command.

Rules 2, 6, 7, and 8 rest on practitioner catalogs and incident reports, not studies.

## Sweep

Run on the diff ([index.md](index.md)). The tool names are examples recalled during research and **not verified**; use the project's own tools first.

| Check | How | Rules |
|---|---|---|
| Compat markers | grep added lines for `deprecat`, `legacy`, `backward`, `compat`, `shim`, `migrat`, `polyfill`, `removed`, `_unused` | 1, 4 |
| Unused code | a dead-code tool, for example knip (JS/TS), vulture (Python), staticcheck U1000 (Go), cargo-machete (Rust dependencies) | 4, 6 |
| UI leftovers | grep user-visible strings for `coming soon`, `TODO`, `WIP`, `placeholder`, `lorem`, `example.com`, `not implemented`; disabled controls with no handler; tabs or routes that render nothing | 2 |
| Literal data | arrays of names, emails, amounts, or IDs outside test and fixture paths; hard-coded numbers in metric or dashboard components | 7, 8 |
| Flags | flags whose value is constant, or whose other branch is unreachable | 5 |
| Settings | config keys with no reader | 6 |
| Abstractions | new functions, classes, or exports with zero or one caller | [writing-code](../writing-code/index.md) 2 |
| Duplicates | a copy-paste detector, for example jscpd | [writing-code](../writing-code/index.md) 3 |

## Done when

- [ ] Every compatibility path in the diff names its consumer, data, or user, or is gone.
- [ ] No UI for unbuilt work, unless it is a requested, working waitlist.
- [ ] No unused code, "removed" comment, settled flag, or reader-less config key is added.
- [ ] Product code holds no sample data; every shown number traces to a query or input.
- [ ] Sweep commands and output are in the handoff.
