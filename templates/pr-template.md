# Pull Request: [[TICKET-ID]] [Feature / Bug Fix Title]

## Summary of Changes
- High-level overview of what this pull request modifies and why.
- Links to relevant architectural design decisions and implementation plan (`*.plan.md`).

## Linked Issue
- Fixes #[TICKET-ID] (Linear / GitHub Issues)

## 4-Quadrant Test Evidence
```text
Native Test Runner Execution:
✔ Quadrant 1 (Happy Path): Passed
✔ Quadrant 2 (Failure Path): Handled expected errors cleanly
✔ Quadrant 3 (Edge Case 1 - Boundary / Empty): Passed
✔ Quadrant 4 (Edge Case 2 - Idempotency / Concurrency): Passed

Result: 4 passed, 0 failed, 0 skipped
```

## Architectural & Security Verification
- [ ] No unapproved third-party dependencies added
- [ ] Tenant boundaries and access controls verified
- [ ] Input schemas validated before mutation
- [ ] No hardcoded secrets, tokens, or environment overrides

## Rollback Runbook
In case of regression or deployment anomaly:
1. Revert merge commit via `git revert -m 1 <commit-sha>`.
2. Redeploy prior known good build to Staging.
3. Validate rollback status in monitoring dashboard.

## Staging Human-in-the-Loop Signoff
- [ ] Verified live on Staging environment
- [ ] Telemetry / error tracker clean (PostHog / Sentry / Datadog)
- [ ] Human engineer signoff approved for Production release
