# SDLC Rule 01: Planning & Scope Control

## 1. Zero Assumptions Principle
When requirements, APIs, or designs are underspecified:
- **Surface Ambiguity as a Question:** Ask the user or ticket owner directly. Never invent business logic or make silent assumptions.
- **Identify Data Ownership:** Explicitly determine which datastore is the authoritative source of truth.
- **Tenant Isolation:** Explicitly state whether the feature requires workspace/tenant isolation.

## 2. Check Prior Art
- Search existing plan files (`*.plan.md`), design docs, and repository READMEs before designing any feature.
- Extend established patterns instead of inventing duplicate approaches.

## 3. Plan Deliverable Schema
Every plan must be written to `<task-name>.plan.md` and contain:
- Implementation Steps (numbered, file paths, functions).
- Acceptance Criteria (clear pass/fail conditions).
- Files Likely to Change.
- Risks & Edge Cases.
