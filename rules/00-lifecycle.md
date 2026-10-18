# SDLC Rule 00: Lifecycle & Sizing

## 1. The Five Lifecycle Phases
All engineering changes in the repository map to the 5 SDLC stages:
1. **Planning:** Scope definition, prior art review, ambiguity resolution, acceptance criteria.
2. **Implementation:** Surgical code editing adhering strictly to house style.
3. **Testing:** 4-quadrant test authoring and execution via native runners.
4. **Debugging:** Conflict reconciliation, error diagnosis, regression isolation.
5. **Release:** PR compilation, rollback runbook authoring, staging review gate.

## 2. Sizing Matrix
Before starting work, the planning phase must size the task:
- **Small (Single file / typo / minor UI tweak):**
  - Requires: Minimal Planning + Direct Implementation + Fast Test Run.
  - Skips: Full architecture review and migration planning.
- **Medium (Component addition / endpoint expansion / bug fix):**
  - Requires: Standard Plan (`*.plan.md`) + Implementation + 4-Quadrant Unit Tests + Staging PR.
- **Large (Datastore alteration / architectural change / hot path modification):**
  - Requires: Deep Architecture Spec + Security Review + Full Test Suite + Migration & Rollback Runbook + Mandatory Multi-party Review.
