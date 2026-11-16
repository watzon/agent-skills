# 07 Release

Read when a change reaches users or production: T2+ with user-visible effect, and every T3 change.

## Steps

1. **Changelog.** One line per user-visible change, in the project's format. Note breaking changes and deprecations explicitly.
2. **Rollback note.** How to undo: revert commit, flag off, down-migration, or restore step. If there is no rollback, say so and get human approval first.
3. **Migrations (expand, then contract).** Add the new shape, ship code that reads both, backfill, switch writes, then remove the old shape in a later release. Every step must be safe to re-run ([make-operations-idempotent](../principles/make-operations-idempotent.md)).
4. **Stage the rollout at T3.** Flag, canary, or a small cohort first. Define the signal that means stop (error rate, failed checks) before starting.
5. **Version** per the project's scheme. Tag only if you have authority.
6. **Verify after release.** Exercise the real path in the target environment, or say exactly what you could not check.

Never deploy, tag, or publish without the authority the environment grants. Prepare the release and hand off if you lack it.

## Artifact

```
Changelog: ...
Rollback: <exact steps>
Rollout: <stages and stop signal>  (T3)
Post-release check: <command or observation and result>
```

## Done when

- [ ] Changelog entry exists for each user-visible change.
- [ ] Rollback steps are written, or human approval for no rollback is recorded.
- [ ] Migrations follow expand then contract and are re-runnable.
- [ ] T3: staged rollout with a stop signal defined.
- [ ] Post-release check done, or the gap is reported.
