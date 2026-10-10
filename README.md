# Agent Engineering Skills

Reusable Agent Skills that encode software engineering decision-making.

**Status:** Repository foundation. No skills, templates, or examples are implemented yet.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
<!-- Add CI, release, and compatibility badges only when backed by working systems. -->

## Vision

AI coding agents should reason about requirements, architecture, risk, verification, and maintenance as part of development. This project aims to make that engineering practice explicit, reusable, and reviewable.

## Mission

Create the engineering standard for AI coding agents.

This is an ambition, not a claim of established authority. Progress depends on useful workflows, validation evidence, contributor review, and sustained maintenance.

## Core Engineering Principles

- **Plan before implementation.** Clarify requirements, constraints, risks, and acceptance criteria.
- **Architecture before code.** Understand boundaries, dependencies, and tradeoffs before choosing an implementation.
- **Readability over cleverness.** Prefer instructions and code another engineer can understand.
- **Simplicity over unnecessary abstraction.** Add abstractions when they solve a demonstrated problem.
- **Security by default.** Protect secrets, validate inputs, apply least privilege, and respect authorization.
- **Testing is part of implementation.** Verify meaningful behavior and relevant failure paths.
- **Documentation is part of development.** Keep explanations, interfaces, and operational guidance aligned with behavior.
- **Accessibility is a requirement, not an enhancement.** Include accessible content and interaction in design and validation.
- **Consider performance from the beginning.** Establish relevant budgets and measure before optimizing.
- **Reduce engineering mistakes.** Speed is useful when results remain correct and maintainable.

## Repository Philosophy

This repository is not a prompt collection. Skills should encode the decisions behind engineering work: what context to inspect, which tradeoffs to evaluate, when to act, and what evidence demonstrates completion.

Workflows should adapt to the project rather than prescribe one stack or architecture. They should surface uncertainty, explain rationale, and preserve human ownership of consequential decisions.

Long-term maintainability takes priority over short-term completeness. A smaller collection of validated, distinct skills is preferable to broad coverage that is difficult to review or maintain. Consistent structure should make behavior understandable without forcing every skill into an identical workflow.

## What Agent Skills Are

Agent Skills package reusable instructions and, where needed, supporting resources for a bounded class of tasks. Each future skill will define its purpose, activation conditions, workflow, engineering rationale, examples, anti-patterns, and quality checklist.

A skill does not replace user authorization, repository instructions, tool constraints, or human review.

## How Skills Work

When activation conditions match a task, an agent inspects context, follows the applicable decision process, performs authorized work, verifies outcomes, and reports material decisions and limitations.

Target tools include OpenAI Codex, Claude Code, Gemini CLI, GitHub Copilot, and future Agent Skills compatible tools. Support will be documented after validation against specific tool versions and workflows.

Discovery, packaging, installation, and invocation details will be defined with the first validated skills. The foundation provides no installable skills or execution mechanism.

## Repository Layout

```text
agent-engineering-skills/
├── README.md
├── LICENSE
├── CHANGELOG.md
├── CONTRIBUTING.md
├── .gitignore
├── docs/
├── examples/
├── templates/
│   └── skill-template/
└── skills/
```

| Location | Responsibility |
| --- | --- |
| `README.md` | Scope, principles, architecture, and roadmap |
| `LICENSE` | MIT license |
| `CHANGELOG.md` | Notable changes and release history |
| `CONTRIBUTING.md` | Authoring, validation, and review standards |
| `.gitignore` | Local artifact and credential exclusions |
| `docs/` | Future design, compatibility, and maintenance documentation |
| `examples/` | Future verified applications of working skills |
| `templates/skill-template/` | Reserved location for the future authoring template |
| `skills/` | Future independently reusable skills |

### Scaling the Catalog

Each future skill will have one directory directly under `skills/`, named with a globally unique, stable, lowercase hyphenated identifier. Categories will organize discovery through a future catalog rather than determine paths. A skill can belong to several categories without being duplicated or moved.

Initial category topics include Architecture, AI Engineering, Backend, Frontend, DevOps, Security, Code Review, Documentation, Databases, Testing, Performance, and Accessibility. Categories can expand without changing the repository architecture.

The layout is intended to accommodate 100+ skills. At that scale, discovery needs a catalog, quality needs repeatable validation, and maintenance needs ownership and deprecation practices. Stable identifiers, bounded scope, and explicit dependencies reduce future reorganization. Detailed metadata and tooling will be designed when actual needs emerge.

All directories are intentionally empty, including `templates/skill-template/`. Git does not track empty directories; they will appear in Git checkouts once substantive content is added. No placeholder files are included.

## Skill Lifecycle

1. **Propose:** Define the problem, users, activation conditions, and boundaries.
2. **Design:** Specify decisions, rationale, risks, and acceptance criteria.
3. **Develop:** Write instructions and necessary supporting resources.
4. **Validate:** Exercise realistic tasks and failure cases; record agent versions and environments.
5. **Review:** Assess correctness, security, usability, compatibility, and maintenance cost.
6. **Release and maintain:** Publish reviewed changes, record behavior changes, and address feedback.
7. **Deprecate:** Document replacements and migration guidance before removal.

No skills have been released. This describes the intended maintenance process.

## Skill Execution Pipeline

The pipeline describes engineering responsibilities during a task:

```text
User Request
     ↓
Planning
     ↓
Architecture
     ↓
Implementation
     ↓
Validation
     ↓
Security Review
     ↓
Code Review
     ↓
Documentation
```

This is a conceptual workflow, not a strict implementation requirement or an implemented orchestrator. Individual skills may participate in one or several stages. Task scope determines which stages are relevant, and review may return work to earlier stages.

Security, testing, accessibility, performance, and documentation also inform planning and implementation. Their placement in the diagram does not defer these concerns until the end. The execution pipeline describes task work; the skill lifecycle describes how skills themselves are maintained.

## Roadmap

Phases describe an intended sequence without delivery dates or compatibility guarantees. None of this work is implemented.

| Phase | Planned work | Focus |
| --- | --- | --- |
| 1 | `project-planner`, `mentor-mode` | Planning and explaining engineering decisions |
| 2 | `ai-engineer`, `frontend-master` | AI systems and accessible frontend engineering |
| 3 | `code-review`, `security-review` | Correctness, maintainability, and security assessment |
| 4 | MCP, LangGraph, RAG, FastAPI, Docker, Testing, DevOps, Architecture Review | Specialized engineering workflows |

Phase 4 entries are topic areas. Final skill names and boundaries will be determined during design.

## Future Vision

Build independently usable skills with documented compatibility, realistic evaluation tasks, and clear maintenance responsibilities. Extend coverage when a distinct engineering need and a credible validation approach exist.

Future catalog and validation tooling should support discovery and consistency without unnecessary coupling between skills.

## Examples

Verified examples will be added alongside working skills. No sample outputs or simulated demonstrations are included in the foundation.

## Contribution Guide

Read [CONTRIBUTING.md](CONTRIBUTING.md). Proposals should explain the engineering problem, scope, rationale, expected outcomes, and validation approach. Discuss substantial additions before implementation.

Foundation documentation improvements are welcome. Skill and template implementation will begin in later sessions.

## FAQ

### Can I install or run a skill now?

No. Installation and invocation instructions will accompany validated skills.

### How does this differ from a prompt collection?

Skills define repeatable decision processes, scope boundaries, and verification criteria rather than simply requesting an output.

### Which agents are supported?

Codex, Claude Code, Gemini CLI, and GitHub Copilot are targets. Compatibility has not yet been validated.

### Must every task follow the entire pipeline?

No. Apply responsibilities appropriate to the task and revisit decisions when new evidence requires it.

### Can categories change as the project grows?

Yes. Categories organize discovery and do not determine skill paths. New categories do not require restructuring the repository.

### Why is the template directory empty?

The template will be designed after the foundation, once authoring requirements are reviewed.

### What license applies?

The project uses the [MIT license](LICENSE).

## Non Goals

- Collecting generic prompts without an engineering workflow.
- Maximizing skill count at the expense of quality or maintenance.
- Replacing engineering judgment, authorization, or human review.
- Enforcing one framework or architecture across unrelated projects.
- Claiming universal agent compatibility without validation.
- Guaranteeing production readiness through instructions alone.
- Building an orchestration framework during the foundation phase.
