# Operating principles

Read when debugging, sequencing multi-step work, or building commands and loops that may crash, restart, or retry.

## Fix root causes

1. **Reproduce first,** as a failing test. If you cannot reproduce it, you cannot verify the fix.
2. **Instrument, do not guess.** Read the actual error; inspect real values.
3. **Ask "why" until you reach the cause.** A guard that only silences a crash (null check, catch, retry) is a symptom fix.
4. **Fix the pattern.** Search for the same mistake elsewhere.
5. **Fails after a restart? Suspect state before code:** config, caches, lock files, serialized state. If clearing state fixes it, validate that state as the fix.

Check: can you say in one sentence why the bug happened, and does the fix change that cause?

## Sequence verifiable units

- Start from a known-good baseline: current trunk, checks passing.
- Each unit: one change, run its check, then continue. A break found at the unit that caused it is cheap; one found after a batch is buried.
- Each commit builds and makes sense on its own.

Check: if you stopped after any unit, would the tree build, pass, and make sense?

## Make operations idempotent

- Running twice must converge to the same end state. Scan for existing state, clean stale artifacts, adopt live work instead of duplicating it.
- Compare by content, not by timestamps or creation order.
- Detect and reclaim stale locks (dead owner, expired lease).
- External effects (payments, messages, webhooks) use an idempotency key or a check-then-act that survives duplicates.
- Each migration step is safe to re-run.

Check: what happens if this runs twice, or crashed at each possible point last time?

## Encode lessons in structure

When the same correction comes up a second time, turn it into a check instead of more text. Strongest rung that fits: a state that cannot compile, then a lint or CI check, then one canonical helper, then a runtime check, and only then a written rule. Agents copy what nearby code does, so a weak guard becomes the next template.
