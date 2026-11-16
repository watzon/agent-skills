# Make operations idempotent

Apply when designing commands, lifecycle steps, or processing loops that run amid crashes, restarts, and retries. Converge to the same end state regardless of partial prior runs.

Crashes, restarts, and retries are normal. If leftover state changes the next run's result, every restart becomes a debugging session.

- **Convergent startup:** scan for existing state, clean stale artifacts, adopt live sessions instead of duplicating them.
- **Compare by content,** not by creation order or timestamps.
- **Self-healing locks:** detect stale locks (dead owner process, expired lease) and reclaim them.
- **Idempotent scheduling:** failed work respawns cleanly; inputs are regenerated each cycle.
- **External effects** (payments, messages, webhooks): use an idempotency key or a check-then-act that survives duplicates.
- **Migrations:** each step safe to re-run ([07-release](../07-release/index.md)).

**Check:**
1. What happens if this runs twice in a row?
2. What happens if the last run crashed at each possible point?
3. Does re-running converge to the same end state?

If any answer is "it depends on what was left behind", add a reconciliation step.
