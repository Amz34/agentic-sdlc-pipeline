# Rollback Runbook: [[TICKET-ID]] [Feature / Release Title]

## Trigger Conditions
Execute this rollback if ANY of the following occur within 15 minutes of deployment:
- Error rates exceed 0.05% baseline.
- P99 latency increases by >25% on key endpoints.
- Critical regression reported in core user flow.

## Fast Reversion Steps
1. **Application Layer:**
   ```bash
   # Revert commit
   git revert -m 1 <MERGE_COMMIT_SHA> -n
   git commit -m "revert: rollback [TICKET-ID] due to incident"
   git push origin main
   ```
2. **Feature Flag Disabling (if gated):**
   - Toggle flag `ff_feature_slug` to `OFF` via admin console.
3. **Database Layer (if migration applied):**
   - Run down-migration:
   ```bash
   npm run db:migrate:down # or alembic downgrade -1
   ```

## Verification & Recovery Confirmation
- [ ] Staging/Production health check endpoint returns 200 OK.
- [ ] Error tracker alerts resolve to nominal baseline.
- [ ] Affected customers or test accounts re-verified.
