# Fix root causes

Apply when debugging. Trace each symptom to its root cause and fix it there; reproduce first, ask why until you reach it, resist nil-check guards that silence crashes.

Symptom fixes pile up, make the system harder to reason about, and leave the real bug in place.

1. **Reproduce first.** If you cannot reproduce it, you cannot verify the fix. Capture the repro as a failing test.
2. **Instrument, don't guess.** Read the actual error, add logging, inspect real values.
3. **Ask "why" until you hit the cause.** A guard that only silences a crash (a nil check, a try/catch, a retry) is a symptom fix.
4. **Fix the pattern, not the instance.** Search for the same mistake elsewhere and fix every instance.
5. **A workaround that needs a paragraph of comment means the code is wrong.** Fix the code.

**Fails after restart? Suspect state before code.** Code is the same between runs; state is not. Check config files, caches, lock files, and serialized state first. If clearing state fixes it, add validation of that state as the fix.

**Check:** can you say in one sentence why the bug happened, and does your fix change that cause rather than its effect?
