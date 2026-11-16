# Sequence verifiable units

Apply to multi-step work (sweeps, migrations, runs of similar edits) and to how you stack commits and PRs. Break work into small units that each end in a verifiable state, check each before the next, and order delivery so the sequence proves itself to a reviewer.

A break caught at the unit that caused it is cheap to find. A break caught after a batch is buried under work built on top of it.

**Execution:**
- Start from a known-good baseline: rebase onto clean trunk and run the checks first.
- Each unit is a bracket: known-good state, one change, run the check, proceed. Never batch edits and check once at the end.
- When a script does the edits, the per-unit check is nearly free. Run it anyway.

**Delivery:**
- Stack commits so the sequence reads as an argument. Canonical: failing test (red), then the fix (green).
- Other good orders: removal before reshape; baseline capture before the change; scaffold before feature.
- Each commit stands on its own and passes.

**Check:** if you stopped after any unit, would the tree build, pass, and make sense?

Each check must be real: [prove-it-works](prove-it-works.md).
