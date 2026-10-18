# SDLC Rule 06: Release & Production Guardrails

## 1. The Production Red Line
- Under no circumstances should an automated agent deploy directly to production infrastructure or run unreviewed production database migrations.
- Production access requires:
  1. Passing automated CI/CD test gates.
  2. Successful deployment and validation on Staging.
  3. Mandatory human engineering approval.

## 2. Pull Request Requirements
Every PR created in the SDLC pipeline must provide:
- **Summary:** Problem statement and implemented solution.
- **Test Evidence:** Verifiable output from the native test runner.
- **Risk Assessment:** Performance, security, data migration, and backward compatibility risks.
- **Rollback Runbook:** Step-by-step instructions to revert code and rollback schema/data migrations.
- **Staging Verification Checklist:** Explicit manual items to verify on staging.
