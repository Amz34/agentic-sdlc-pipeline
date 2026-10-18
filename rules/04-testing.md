# SDLC Rule 04: Testing & Verification Standards

## 1. Native Test Runners
- For Node/TypeScript: Use native `node:test` (`describe`/`it`/`beforeEach`/`afterEach`) executed via `tsx --test` with `node:assert/strict`. No Jest/Vitest/mocking libraries unless explicitly pre-configured.
- For Python: Use `pytest` or `unittest`.

## 2. Mandatory 4-Quadrant Test Coverage
Every test suite must cover:
1. **Happy Path:** Expected successful execution with valid data.
2. **Failure Path:** Error handling, validation rejection, and missing params.
3. **Edge Case 1:** Boundary conditions, zero values, empty collections, or loading state stability.
4. **Edge Case 2:** Concurrency, race conditions, expired tokens, or duplicate payloads.

## 3. Concrete Test Evidence
- Code changes cannot be merged or released without executing the test command and reporting passing output (`X passed, 0 failed`).
- Tests must be registered in the test runner script (e.g. `package.json` test script or test runner configuration).
