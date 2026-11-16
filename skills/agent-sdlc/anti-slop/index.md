# Anti-slop sweep

Read before you hand off any change, and when you review one. Slop is the unchosen default left in the work: repeated copy, leftover compatibility code, placeholder UI, invented numbers, generic design. The rules are in [copy.md](copy.md), [product.md](product.md), and, for UI, [design/floor-checks.md](../design/floor-checks.md).

## How to run it

1. Run the sweep on the diff, not the whole repo, so old code is not flagged. Report older slop; do not fix it in this change.
2. Run the mechanical checks first. Show each command and its output in the handoff.
3. Then do the judgment checks by reading the changed screens, strings, and code.
4. A single hit on a prose tell proves nothing. Rewrite when several signals cluster in one paragraph or view.
5. Never call a finding "written by AI". Name the problem: repeated, padded, unused, invented.

## Mechanical checks

Added lines only, in tracked changes and in new untracked files (ignored files are skipped); set `BASE` to the commit the change branched from and run from the repo root. A starting point; adapt the patterns to the project. Every hit needs a fix or a one-line reason.

```sh
sweep() {
  { git diff -U0 "$BASE" -- .
    git -c core.quotePath=false ls-files --others --exclude-standard | while IFS= read -r f; do git diff -U0 --no-index /dev/null "$f"; done
  } | perl -CSD -ne 'BEGIN { $p = shift } print if /^\+(?!\+\+)/ && /$p/i' "$1"
}
sweep 'deprecat|legacy|backward|compat|shim|migrat|polyfill|removed|_unused'    # compat markers
sweep 'coming soon|todo|wip|placeholder|lorem|example\.com|not implemented'   # unbuilt-feature leftovers in UI strings
sweep '\bplease\b|thank you|\bsorry\b'                                     # courtesy words in UI text
sweep 'let me know|i hope this helps|want me to'                                  # chat closers in docs and reports
sweep '[\x{2013}\x{2014}]'                                                  # dashes in copy and docs
```

Compat markers serve [product.md](product.md) rules 1 and 4; leftovers serve rule 2; courtesy words, closers, and dashes serve [copy.md](copy.md) rules 5, 7, and 8.

Checks that need a tool or a search rather than a grep:

| Check | How | Rule |
|---|---|---|
| Disabled controls, empty tabs or routes | controls with no handler; routes that render nothing | [product.md](product.md) 2 |
| Unused code | the project's dead-code or unused-export tool | [product.md](product.md) 4 |
| Config keys with no reader | search for each added key outside its definition | [product.md](product.md) 6 |
| Literal sample data outside tests | arrays of names, emails, amounts, or IDs outside test and fixture paths | [product.md](product.md) 7 |
| New exports with zero or one caller | search for each new exported name | [writing-code/index.md](../writing-code/index.md) 2 |
| UI floor (UI changes only) | automated contrast check; screenshots at desktop and phone width | [design/floor-checks.md](../design/floor-checks.md) |

## Judgment checks

Read each changed view and module once, asking:

- **Copy.** Is any fact stated twice on one view? Is prose doing a label's job? Does a sentence explain state the interface should make obvious? Are errors and destructive confirmations still complete? ([copy.md](copy.md))
- **Compat.** Does each shim, fallback, or migration pass the existence test? ([product.md](product.md))
- **Unbuilt work.** Is there a tab, nav entry, disabled control, or "coming soon" for something not built? ([product.md](product.md))
- **Numbers.** Does every number on screen come from a real query or input? ([product.md](product.md))
- **Design.** Can each color, typeface, and layout choice be traced to the subject or the design system in one sentence? ([design/index.md](../design/index.md))

## Done when

- [ ] Every mechanical check ran on the diff, with command and output in the handoff.
- [ ] Every hit is fixed or has a one-line reason.
- [ ] Every judgment question was answered for each changed view and module.
- [ ] No finding is framed as AI authorship.
