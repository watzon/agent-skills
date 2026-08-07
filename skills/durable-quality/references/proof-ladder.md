# Proof ladder

## Law

Behavior changes need a quick, sure, repeatable proof. Coverage percentage alone is insufficient. Prefer tests that fail when meaning flips.

## Fail-without-change rule

For a behavior fix or feature:

1. Observe or write a test that fails on current (pre-change) behavior
2. Implement
3. See the test pass
4. Keep the test as regression

TypeScript and many compiler projects treat this as table stakes.

## Tiers

| Tier | Blast radius | Minimum proof | Extra |
|---|---|---|---|
| T0 | Docs, copy, comments | Format/lint | None |
| T1 | Pure functions, local UI without auth | Unit tests + types | Snapshot only if stable and reviewed |
| T2 | API/service boundaries | Contract or integration tests | Schema/openapi checks |
| T3 | Parsers, codecs, state machines, money math | Property or fuzz + units | Golden vectors |
| T4 | Authz, payments, migrations, deletion, crypto wrappers | T3 + human owner review | Mutation sampling; threat notes |
| T5 | Multi-tenant isolation, security boundaries, kernel-equivalent | T4 + dual review when possible | Anomaly tests where relevant |

Assign paths in the repo to tiers (see bootstrap playbook). Default new code to T1/T2; never leave auth/payments unassigned.

## Test honesty signals

Healthy:

- Asserts lock observable behavior
- Edge cases and error paths present
- Tests fail when production assertion is inverted
- Fixtures minimal and readable

Unhealthy (agent PR red flags):

- Tests edited only after failures, with weaker asserts
- Broad `except` / catch swallowing
- Excessive mocking that proves nothing about the system
- Snapshots updated in bulk without explanation
- Coverage floor lowered in the same PR

## Mutation testing mindset

Martin and SQLite both push toward semantic stability:

- Flip branch sense, remove call, change comparator
- A trustworthy suite kills the mutant
- Surviving mutants mean untested meaning

Practical use:

- Run mutation on T3–T5 packages on a schedule or pre-release
- Gate on score only where suite is mature enough not to thrash
- Use surviving mutants as a backlog of missing tests

Tools (examples): PIT (JVM), Stryker (JS/TS/NET), mutmut/cosmic-ray (Python), cargo-mutants (Rust).

## Anomaly testing (when relevant)

Steal SQLite ideas at the right scale:

- timeouts and cancellation
- disk full / permission errors
- duplicate webhooks / at-least-once delivery
- clock skew
- process kill mid-write (for durable stores)

## Property and fuzz

Use when input space is large:

- parsers and serializers
- permission matrix generators
- codecs
- distributed/retry logic with modeled network faults (where tooling exists)

## Proof in the PR

Require authors (human or agent harness) to paste:

- commands run
- exit codes
- relevant tail of output
- what was **not** run and why

Willison's bar: deliver code you have proven to work. Manual proof still matters when automation cannot see the bug class (especially UI and ops).

## Negative verification of the harness

After adding a gate, prove it fails closed:

- temporarily break a dependency rule → CI red
- remove an assertion → mutation or test red
- add `|| true` to a required check → anti-gaming rule red

If the gate cannot be shown to fail, it is decoration.
