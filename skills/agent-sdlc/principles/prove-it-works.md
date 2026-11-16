# Prove it works

Apply after completing a task, before declaring done. Verify against the real artifact (run the feature, read the actual value, inspect the diff), not a proxy, self-report, or "it compiles."

Unverified work has unknown correctness. Proxies (timestamps, derived state, cached output, an agent's summary) feel cheaper than looking, but acting on a wrong inference costs more.

**Code and features:**
1. Build it. Necessary, not sufficient.
2. Run it and exercise the actual feature path.
3. Follow the data from input to output.
4. For integrations, test the full path end to end.

**Check the real thing:** read the actual value, not a cached copy; check a process directly, not through state it left behind. When a check fails, suspect the check before the system.

**Delegated work:** inspect the artifact (diff, file, running behavior), not the report. Agents report what they meant to do, not always what happened.

**Script the check when you can.** A deterministic script that re-runs the comparison beats a one-time look, and a reviewer can re-run it. Keep its output visible in the handoff; commit it only when the work needs an audit trail (a large port or migration).

**Check:** could someone else re-run your evidence and get the same result?
