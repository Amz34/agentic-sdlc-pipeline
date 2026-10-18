# SDLC Rule 03: Implementation & House Standards

## 1. Surgical Modification
- Modify only lines and files required by the plan.
- Do not reformat untouched code or introduce sweeping cosmetic refactors.
- Preserve all existing comments and docstrings.

## 2. Dependency Discipline
- Strictly zero unapproved third-party npm or pip dependencies.
- Reuse existing internal libraries, UI primitives, and utilities.

## 3. Strict Input Validation
- All API routes and function entry points must validate inputs against rigid schemas (Zod/Pydantic) before processing.
- Reject unvalidated parameters immediately.

## 4. Error Handling
- Never silence errors with empty catch blocks.
- Log failures with actionable context (request IDs, entity IDs, timestamps).
