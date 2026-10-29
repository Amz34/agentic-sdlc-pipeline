# Agentic SDLC Pipeline

![Agentic SDLC Pipeline CI/CD Architecture](assets/sdlc-pipeline-benefits.jpg)

> **A production-tested 5-Stage SDLC Pipeline for autonomous AI coding agents (Claude Code, Cursor, Antigravity, Copilot).**  
> Turn tickets into tested, verified, and rollback-ready pull requests with zero hallucinated architecture.

[![CI](https://github.com/Amz34/agentic-sdlc-pipeline/actions/workflows/ci.yml/badge.svg)](https://github.com/Amz34/agentic-sdlc-pipeline/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Architecture: 5-Stage SDLC](https://img.shields.io/badge/Architecture-5--Stage%20AI%20SDLC-emerald.svg)](rules/00-lifecycle.md)
[![Zero-Dependency CLI](https://img.shields.io/badge/CLI-Python%20Stdlib-blue.svg)](bin/sdlc-pipeline)

---

## The Reality: The "Genius Intern with Amnesia"

Modern LLMs reason at an elite engineering level, but they possess zero working memory of your repo conventions, zero self-restraint against installing unapproved packages, and a bad habit of inventing mock abstractions rather than running real tests.

Treating an AI coding agent like an autonomous engineer leads to regressions. Treating it like a **Genius Intern with Amnesia** under a strict pipeline leads to 10x engineering velocity.

The **Leverage Loop** enforces this workflow across every task:

$$\text{Context} \longrightarrow \text{Constrain} \longrightarrow \text{Generate} \longrightarrow \text{Verify}$$

1. **Context ("Brief the intern"):** Feed ticket requirements, existing architecture patterns, and schema contracts.
2. **Constrain ("Hand over the guardrails"):** Ban unapproved npm/pip packages, enforce native test runners, and lock datastore boundaries.
3. **Generate ("Let it work in isolation"):** Agent operates inside constrained plan or implementation modes.
4. **Verify ("Check the work"):** Run automated test suites across all 4 quadrants before human signoff.

---

## The 5-Stage AI SDLC Pipeline

```
┌─────────────────┐     ┌───────────────────────┐     ┌──────────────────┐
│ 1. PLANNING     │ ──> │ 2. IMPLEMENTATION     │ ──> │ 3. TESTING        │
│ *.plan.md       │     │ Surgical Code Edits   │     │ 4 Quadrants      │
│ No code allowed │     │ Zero Dep Bloat        │     │ Native Runners   │
└─────────────────┘     └───────────────────────┘     └──────────────────┘
                                                                │
                                                                ▼
┌─────────────────┐     ┌───────────────────────┐     ┌──────────────────┐
│ PRODUCTION      │ <── │ 5. RELEASE            │ <── │ 4. DEBUGGING     │
│ Human Signoff   │     │ PR Draft & Rollback   │     │ Git Conflicts    │
│ Production Red  │     │ Staging Gate          │     │ Regressions      │
└─────────────────┘     └───────────────────────┘     └──────────────────┘
```

### 1. Planning (`sdlc-planner`)
- **Spec:** [`agents/sdlc-planner.md`](agents/sdlc-planner.md) | **Rule:** [`rules/01-planning.md`](rules/01-planning.md)
- **Constraint:** AI is strictly forbidden from writing code in this phase.
- **Workflow:** Inspect prior art, classify system boundaries (UI vs API vs Datastore), and surface ambiguities as explicit questions before authoring an approved `*.plan.md`.
- **Copy-Paste Prompt:**
  ```text
  Read Linear ticket <TICKET_ID>. Break it into a numbered implementation plan 
  with acceptance criteria, the files likely to change, and the risks. 
  Ask me anything ambiguous before you assume. Do not write code yet.
  ```

### 2. Implementation (`sdlc-implementer`)
- **Spec:** [`agents/sdlc-implementer.md`](agents/sdlc-implementer.md) | **Rule:** [`rules/03-implementation.md`](rules/03-implementation.md)
- **Constraint:** Surgical modifications only. Zero unapproved third-party dependencies.
- **Workflow:** Implement approved steps from the plan. Adhere to existing directory patterns, datastore authority, and error handling conventions.

### 3. Testing (`sdlc-tester`)
- **Spec:** [`agents/sdlc-tester.md`](agents/sdlc-tester.md) | **Rule:** [`rules/04-testing.md`](rules/04-testing.md)
- **Constraint:** Native test runners only (`node:test` via `tsx --test` or `pytest`). No complex mock packages.
- **Mandatory 4-Quadrant Test Suite:**
  1. **Happy Path:** Valid inputs produce expected outcomes.
  2. **Failure Path:** Malformed or missing inputs fail gracefully with explicit errors.
  3. **Edge Case 1:** Empty collections, null objects, or boundary values.
  4. **Edge Case 2:** Idempotency, duplicate triggers, and concurrent execution.
- **Copy-Paste Prompt:**
  ```text
  Write tests for the change in <TICKET_ID> using our test framework. 
  Cover the happy path, the failure path, and two edge cases I would forget. 
  Run them and report what passes and what fails.
  ```

### 4. Debugging (`sdlc-debugger`)
- **Spec:** [`agents/sdlc-debugger.md`](agents/sdlc-debugger.md)
- **Constraint:** Autonomous reconciliation of git rebase conflicts without dropping changes.
- **Workflow:** Parses conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`), reconciles conflicting intent, and re-executes the test suite to isolate regressions.

### 5. Release & Deployment (`sdlc-releaser`)
- **Spec:** [`agents/sdlc-releaser.md`](agents/sdlc-releaser.md) | **Rule:** [`rules/06-release.md`](rules/06-release.md)
- **The Production Red Line:** Never provide AI agents with direct production write access or deployment keys.
- **Workflow:** Generates comprehensive PR descriptions, embeds test evidence, produces actionable rollback runbooks, and gates deployment behind Staging verification and human engineer signoff.
- **Copy-Paste Prompt:**
  ```text
  Draft the PR: summary, risk, rollback steps, and test evidence. 
  Then generate the migration and a rollback for it. 
  Flag anything that needs a human before it goes to production.
  ```

---

## Quickstart CLI

The pipeline includes a zero-dependency Python CLI (`bin/sdlc-pipeline`) to manage and audit repositories:

### 1. Initialize SDLC Architecture into Any Repo
Scaffolds all agent specs and lifecycle rules into `.claude/` and `.cursor/`:
```bash
sdlc-pipeline init /path/to/your/project
```

### 2. Audit Repository Readiness
Verify whether a codebase has the necessary agents, rules, and context files:
```bash
sdlc-pipeline status /path/to/your/project
```

### 3. Generate a Structured Plan Template
```bash
sdlc-pipeline plan --ticket GRO-1135 "Fix analytics widget display"
```

### 4. Draft a Rollback-Ready PR Description
```bash
sdlc-pipeline release --ticket GRO-1135 "Mount AI Insights widget"
```

---

## Repository Structure

```
agentic-sdlc-pipeline/
├── agents/               # Autonomous agent system prompts
│   ├── sdlc-planner.md
│   ├── sdlc-implementer.md
│   ├── sdlc-tester.md
│   ├── sdlc-debugger.md
│   ├── sdlc-reviewer.md
│   └── sdlc-releaser.md
├── rules/                # Operational rules enforced across lifecycle
│   ├── 00-lifecycle.md
│   ├── 01-planning.md
│   ├── 03-implementation.md
│   ├── 04-testing.md
│   ├── 05-review.md
│   └── 06-release.md
├── bin/
│   └── sdlc-pipeline     # Executable CLI orchestrator
├── templates/            # Structured plans, PRs, and runbooks
│   ├── plan-template.md
│   ├── pr-template.md
│   └── rollback-runbook-template.md
├── examples/             # Real-world battle-tested case studies
│   └── GRO-1135-case-study/
├── SKILL.md              # Skill definition for AI agent platforms
├── LICENSE               # MIT License
└── README.md
```

---

## Live Case Study: Linear GRO-1135

Tested in production on `getowl.ai`:
- **Problem:** AI Insights widget failed to render on customer dashboards due to an unannounced component export rename.
- **Pipeline Execution:**
  1. `sdlc-planner` inspected Linear issue, audited git diff, and drafted acceptance criteria.
  2. `sdlc-implementer` made surgical import modifications with null safety.
  3. `sdlc-tester` ran 4-quadrant test suite covering empty state and tab toggles.
  4. `sdlc-debugger` cleared rebase markers autonomously.
  5. `sdlc-releaser` drafted staging verification checklist and rollback steps.
- **Result:** Bug resolved and shipped to staging with complete test evidence in under 12 minutes.

---

## Contributing

Pull requests are welcome. Please ensure any changes conform to the 5 SDLC stages and include 4-quadrant test evidence.

## License

[MIT](LICENSE) © 2026 [Aamir Zameer (Amz34)](https://github.com/Amz34)

---

Part of [my always-on agent stack](https://github.com/Amz34) · [Awesome Agent Infrastructure](https://github.com/Amz34/awesome-agent-infrastructure) (135 live-checked building blocks).
