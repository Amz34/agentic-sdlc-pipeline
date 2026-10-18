---
name: sdlc-pipeline
description: 5-Stage AI SDLC Pipeline Orchestrator (Planning -> Coding -> Testing -> Debugging -> Deployment). Use when developing, refactoring, fixing bugs, testing, or releasing production code in any repository. Enforces the Leverage Loop, native test runners, and production red lines.
---

# SDLC Pipeline Skill

This skill operationalizes the Outskill Masterclass 5-Stage AI SDLC Pipeline across all development work.

## Core Philosophy: The Leverage Loop
$$\text{Context} \longrightarrow \text{Constrain} \longrightarrow \text{Generate} \longrightarrow \text{Verify}$$

1. **Context ("Brief the intern"):** Supply tickets, repository architecture, and existing pattern documentation.
2. **Constrain ("Hand over the rules"):** Enforce guardrails, forbidden libraries, and datastore boundaries.
3. **Generate ("Let it cook"):** Run the agent in isolated plan or build mode.
4. **Verify ("Check the plate"):** Force execution of unit tests, build checks, and UI validation before merging.

---

## The 5 SDLC Stages & Prompts

### Stage 1: Planning
- **Spec:** `.claude/agents/sdlc-planner.md` & `.claude/rules/01-planning.md`
- **Rule:** Never author code before an approved implementation plan (`*.plan.md`). Surface ambiguity as questions rather than making assumptions.
- **Steal-able Prompt:**
  ```text
  Read Linear ticket <TICKET_ID>. Break it into a numbered implementation plan 
  with acceptance criteria, the files likely to change, and the risks. 
  Ask me anything ambiguous before you assume. Do not write code yet.
  ```

### Stage 2: Coding (Implementation)
- **Spec:** `.claude/agents/sdlc-implementer.md` & `.claude/rules/03-implementation.md`
- **Rule:** Surgical modification only. Zero unapproved packages. Strict input validation.

### Stage 3: Testing
- **Spec:** `.claude/agents/sdlc-tester.md` & `.claude/rules/04-testing.md`
- **Rule:** Native test runners only (`node:test` via `tsx --test` or `pytest`). Strictly 4 test quadrants:
  1. Happy Path
  2. Failure Path
  3. Edge Case 1 (boundaries/empty state)
  4. Edge Case 2 (idempotency/concurrency)
- **Steal-able Prompt:**
  ```text
  Write tests for the change in <TICKET_ID> using our test framework. 
  Cover the happy path, the failure path, and two edge cases I would forget. 
  Run them and report what passes and what fails.
  ```

### Stage 4: Debugging
- **Spec:** `.claude/agents/sdlc-debugger.md`
- **Rule:** Parse git rebase/merge conflict blocks autonomously (`<<<<<<<`, `=======`, `>>>>>>>`). Retain changes cleanly without syntax or semantic degradation.

### Stage 5: Deployment & Release
- **Spec:** `.claude/agents/sdlc-releaser.md` & `.claude/rules/06-release.md`
- **Rule:** The Production Red Line: Never give AI direct production credentials. Staging first, human approval always required before prod.
- **Steal-able Prompt:**
  ```text
  Draft the PR: summary, risk, rollback steps, and test evidence. 
  Then generate the migration and a rollback for it. 
  Flag anything that needs a human before it goes to production.
  ```

---

## Quick CLI Usage
```bash
# Audit repository for SDLC readiness:
sdlc-pipeline status [path]

# Scaffold agents & rules into any repo:
sdlc-pipeline init [path]

# Generate a new implementation plan:
sdlc-pipeline plan --ticket GRO-1135 "Fix analytics widget display"

# Draft a production PR with rollback steps:
sdlc-pipeline release --ticket GRO-1135 "Mount AI Insights widget"
```
