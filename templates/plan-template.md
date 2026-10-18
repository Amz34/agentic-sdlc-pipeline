# Implementation Plan: [TICKET-ID] - [Task Title]

## 1. Context & Objectives
- **Ticket / Source:** Linear / Jira / Issue `[TICKET-ID]`
- **Scope & System Impact:** (Webapp UI / API / Database / Cache / Background Worker)
- **Datastore Authority:** (PostgreSQL / DynamoDB / Redis / SQLite)

## 2. Architectural Guardrails & Prior Art
- **Existing Patterns:** (Document components, services, or hooks being extended)
- **Constraint Checklist:**
  - [ ] Zero unapproved external dependencies
  - [ ] Native test runners only (`node:test` or `pytest`)
  - [ ] Tenant data isolation strictly preserved
  - [ ] Error states return explicit types without unhandled rejections

## 3. Step-by-Step Implementation Steps
1. [ ] **Step 1: Component / Service Interface**
   - Files to create or modify: `src/...`
   - Purpose: Define typed interfaces and schemas.
2. [ ] **Step 2: Business Logic Implementation**
   - Files to modify: `src/...`
   - Purpose: Implement surgical changes adhering to existing codebase patterns.
3. [ ] **Step 3: Verification & Wiring**
   - Files to modify: `src/...`
   - Purpose: Connect into main execution path or router.

## 4. Acceptance Criteria & 4-Quadrant Test Matrix
- [ ] **Quadrant 1 (Happy Path):** Valid inputs produce expected outputs and correct UI/data state.
- [ ] **Quadrant 2 (Failure Path):** Missing/malformed inputs trigger clean error handling without crashes.
- [ ] **Quadrant 3 (Edge Case 1 - Boundary/Empty):** Zero items, null records, or maximum length handled without regression.
- [ ] **Quadrant 4 (Edge Case 2 - Idempotency/Race):** Repeated invocations or rapid retries do not corrupt state.

## 5. Risk Assessment & Rollback Strategy
- **Potential Failure Modes:** (e.g., latency spikes, missing props in legacy callers)
- **Mitigation:** Fallback defaults, feature flags, defensive null-checks.
- **Rollback Runbook:** Steps to immediately revert in staging or production.
