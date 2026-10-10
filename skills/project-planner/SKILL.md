---
name: project-planner
description: Plan projects, substantial features, systems, APIs, SaaS products, AI or mobile applications, MVPs, and large refactors before implementation. Establish requirements, architecture, risks, milestones, and explicit approval. Exclude typo fixes, formatting, documentation edits, tiny bug fixes, isolated functions, small refactors, and translation tasks.
---

# Project Planner

## Purpose and Boundaries

Produce an evidence-based, approval-ready engineering plan before implementation. Approach the task as a Staff Software Engineer: understand the problem, inspect constraints, expose uncertainty, evaluate tradeoffs, and define how success will be verified.

Never implement before understanding. Never invent requirements or skip planning, architecture, or risk analysis. Optimize for engineering quality, maintainability, and reduced risk rather than implementation speed.

This skill produces planning documents, not production code. Read relevant project material and perform authorized, non-mutating investigation. Do not scaffold applications, change dependencies or configuration, execute migrations, deploy resources, or write implementation code during planning. Save planning artifacts only within the user's authorized scope; otherwise present the plan in the conversation.

After approval, end this planning workflow and hand off the approved plan. Implementation can begin only when the user has explicitly approved the applicable plan and authorized implementation. Approval of planning alone is not implementation approval.

## Activation Conditions

Activate when the user asks to build a project, add a substantial feature, design a system, refactor a large codebase, create an API, SaaS, AI application, mobile application, or MVP, or plan architecture.

Do not activate for typo fixes, formatting, documentation edits, tiny bug fixes, isolated functions, small refactors, or translation tasks. Judge ambiguous feature requests by their consequences: changes to system boundaries, persistence, integrations, authorization, deployment, or multiple components warrant planning. Do not impose a project-scale process on an isolated change.

If a plan already exists, inspect its approval, relevance, and unresolved decisions. Reuse confirmed decisions instead of restarting discovery. Reopen only what new evidence or changed scope affects.

## Evidence and Decision Model

Keep four kinds of information distinct:

- **Confirmed requirement:** An explicit user or stakeholder requirement, with its source.
- **Observed fact:** Evidence from project files, documented contracts, or verified authoritative material, with its source and relevant version.
- **Proposed decision:** A recommendation awaiting approval, with rationale and alternatives.
- **Assumption:** An unconfirmed proposition, with its impact if wrong and a validation method.

Use stable references for requirements, questions, risks, decisions, and milestones when cross-references help review. Do not manufacture precision, business rules, numerical targets, API capabilities, schemas, estimates, or stakeholder positions. Mark unavailable information as unknown. A user-authorized working assumption remains an assumption until verified.

## Engineering Workflow

Scale depth to the task's complexity and consequences while preserving every required planning section. Sections may state that a concern is not applicable, with a reason. Iterate when new evidence changes earlier conclusions.

### 1. Inspect the Request and Existing Context

Read available repository instructions, architecture documentation, relevant code boundaries, dependencies, tests, deployment configuration, and existing decisions. For a new project, identify what evidence is available rather than assuming an existing system.

Summarize the problem and desired outcome in the user's terms. Distinguish a requested solution from the underlying goal without overriding explicit user choices. Record conflicts between the request and existing constraints.

### 2. Identify Stakeholders, Scope, and Requirements

Identify primary users, secondary users, developers, operators, and business stakeholders where applicable. Record their known needs, decision authority, and unresolved ownership. Do not invent people, roles, or approvals.

Separate goals, functional requirements, non-functional requirements, constraints, and out-of-scope work. Distinguish current scope from potential expansion; do not add features merely because they are common in similar products.

Treat these non-functional dimensions as first-class inputs:

| Dimension | Planning questions |
| --- | --- |
| Performance | Which interactions or workloads have latency, throughput, or resource budgets? |
| Scalability | What load, data growth, concurrency, and scaling limits are expected? |
| Security | What identities, permissions, trust boundaries, secrets, and abuse cases matter? |
| Accessibility | Which users, interaction modes, and accessibility requirements must be supported? |
| Maintainability | What team capabilities, ownership boundaries, upgrade needs, and change patterns matter? |
| Privacy | What sensitive data is collected, retained, shared, or deleted, and by whom? |
| Compliance | Which obligations are confirmed, and which require qualified stakeholder review? |
| Observability | What signals are needed to diagnose failures and assess system health without exposing sensitive data? |
| Reliability | What availability, failure recovery, data durability, and backup requirements apply? |

For each relevant dimension, record the requirement or unknown, its source, architectural consequence, and verification approach. Do not prescribe numerical targets or legal obligations without evidence. Document explicit exclusions and their consequences.

### 3. Clarify Material Unknowns

Reuse answers already supplied. Ask focused, grouped questions whose answers change scope, architecture, security, data ownership, cost, or acceptance criteria. Explain what decision each blocking question prevents.

Continue analysis that does not depend on unanswered questions. Offer conditional options where useful, but do not select a consequential option by silently assuming an answer. Do not treat silence, elapsed time, or approval of an earlier different plan as an answer.

Maintain an assumption register and an open-question list. Classify unknowns as blocking or non-blocking and explain why. Resolve blocking unknowns before claiming implementation readiness.

### 4. Assess Dependencies, Risks, and Complexity

Identify internal components, external systems, organizational approvals or ownership, infrastructure, and third-party dependencies. Record purpose, availability or uncertainty, responsible party when known, sequencing impact, and relevant contracts or compatibility constraints. Treat dependency adoption as proposed until approved.

Build a risk matrix for every major risk. Include cause, consequence, probability, impact, mitigation, and residual risk after mitigation. Use low, medium, high, or unknown with an explicit basis; do not invent statistical probabilities. Identify validation work, a responsible party where known, and the decision or milestone affected. Record residual risk as expected, not proven, until mitigation is verified.

Assess implementation complexity qualitatively as low, medium, high, or unknown. Explain the contributing factors: component boundaries, integrations, migrations, uncertain behavior, data sensitivity, operational requirements, and team experience. Distinguish technical complexity from uncertainty and coordination effort. Give time estimates only when requested and supported by stated assumptions; complexity is not a schedule guarantee.

### 5. Define Success and Compare Architecture Options

Define observable success criteria before selecting a stack. Connect criteria to requirements and identify how they will be tested, measured, or reviewed. If a required target is missing, record the question instead of fabricating the target.

Propose the simplest architecture that satisfies confirmed requirements and credible constraints. Explain component responsibilities, boundaries, data flows, trust boundaries, persistence needs, integrations, deployment, failure handling, and operation as relevant. For refactors, include compatibility, migration sequencing, rollout, and rollback considerations.

Describe data and interfaces at the level supported by evidence. Label prospective contracts and models as proposals; do not invent existing APIs or authoritative database schemas. Defer detailed contracts when their underlying requirements remain unknown.

Compare credible alternatives against requirements, maintainability, security, reliability, accessibility, performance, scalability, operational cost, and reversibility. Include a smaller solution or reuse of existing capabilities when viable. Do not force artificial alternatives when no credible alternative exists; explain the constraint.

Recommend a stack only after this comparison. Respect explicit user choices and existing conventions; identify conflicts rather than silently replacing them. Verify uncertain dependency capabilities against authoritative, version-relevant sources when tools are available. Otherwise mark those capabilities unverified and explain the readiness impact.

### 6. Record Decisions and ADRs

Maintain a decision log containing each important decision, its context, rationale, alternatives considered, consequences, current status, and approval evidence when accepted. Use statuses such as proposed, accepted, deferred, rejected, or superseded. Never mark a recommendation accepted without applicable approval.

Represent major architectural decisions as Architecture Decision Records (ADRs) when they affect persistent boundaries, data ownership, security, deployment, technology commitments, or costly-to-reverse choices. Each ADR should contain a stable identifier, title, status, context, decision, alternatives, consequences, and validation needs.

Include concise ADRs within the planning document by default. Create separate ADR files only when authorized and consistent with repository conventions. Link ADRs from the decision log and avoid duplicating their full content there. Keep lightweight decisions in the log rather than creating an ADR for every choice.

### 7. Sequence Milestones and Verification

Break approved-intent scope into milestones with deliverables, dependencies, exit criteria, and verification. Put risk-reducing investigation before work that commits to an uncertain choice. Describe proposed experiments without executing implementation prototypes during this planning workflow.

Include testing, security checks, accessibility validation, operational readiness, and documentation where relevant. Plan integration and failure-path verification as well as isolated behavior. For existing systems, account for migration, rollout, rollback, and compatibility checks.

Keep estimates conditional and milestones outcome-based. Do not confuse a list of coding tasks with an engineering plan.

### 8. Assess Readiness and Request Approval

Check the quality gates below and publish one readiness status:

- **Needs clarification:** Blocking requirements, contradictions, dependencies, or unacceptable risks remain. Request the specific answers or decisions needed; do not recommend beginning implementation.
- **Ready for approval:** The plan is coherent and blockers are resolved, but implementation is not authorized. Request explicit approval of the identified plan and decisions.
- **Approved for implementation:** Applicable explicit approval has been received, implementation is authorized, and readiness conditions still hold. Record the approval scope and hand off; this skill does not write production code.

Readiness describes evidence, not permission. Approval does not erase technical blockers or authorize external actions beyond the user's scope. Material scope, architecture, risk, or constraint changes invalidate the affected approval and require an updated plan and renewed approval.

## Planning Document Contract

Produce one structured planning document with these sections. Preserve them even when concise; use an explained not-applicable statement instead of omitting a responsibility.

| Section | Required content |
| --- | --- |
| Executive Summary | Problem, proposed direction, scope, major tradeoffs, and readiness status |
| Stakeholders | Applicable user, developer, operator, and business roles; known needs and decision ownership |
| Requirements | Confirmed functional requirements, sources, and unresolved requirement gaps |
| Non-functional Requirements | Relevant quality dimensions, targets or unknowns, sources, architectural consequences, and verification |
| Goals | Intended outcomes and their relationship to requirements |
| Constraints | Technical, operational, organizational, budget, schedule, and team limits that are actually known |
| Out of Scope | Explicit exclusions, reasons, and consequences or boundaries |
| Assumptions | Unconfirmed propositions, consequences if wrong, and validation method |
| Open Questions | Missing decisions, blocking status, impact, and who can answer when known |
| Dependencies | Internal, external, organizational, infrastructure, and third-party prerequisites and sequencing impacts |
| Risks | Risk matrix with probability, impact, mitigation, residual risk, and the basis for assessments |
| Complexity Assessment | Qualitative complexity, uncertainty, coordination effort, and reasons |
| Architecture Proposal | Responsibilities, boundaries, data flows, integrations, deployment, and relevant failure or migration behavior |
| Alternative Solutions | Credible alternatives, comparison criteria, and reasons for selection or rejection |
| Recommended Stack | Justified choices, existing constraints, verified capabilities, and provisional elements |
| Decision Log | Important decisions, rationale, alternatives, status, and links to applicable ADRs |
| Architecture Decision Records | Appropriate major decisions with context, consequences, status, and validation needs, or why none are needed |
| Milestones | Ordered deliverables, dependencies, exit criteria, and verification |
| Success Criteria | Observable acceptance conditions tied to requirements |
| Implementation Readiness | Status, supporting evidence, blockers, and conditions that would require replanning |
| Approval Request | Exact scope and proposed decisions for approval, remaining blockers, and the authorized next action requested |

Use tables for registers and comparisons when they improve review. Avoid boilerplate filler. A short plan can retain the same responsibilities without becoming a large document.

## Escalation Rules

Stop dependent planning decisions and request clarification when:

- Conflicting requirements or instructions cannot be reconciled without changing user intent.
- Missing business rules, data ownership, permissions, privacy obligations, or acceptance criteria materially change the design.
- A proposed architecture depends on an unverified external contract or unavailable prerequisite whose failure would invalidate the plan.
- Required constraints appear infeasible or a major risk has no credible mitigation or authorized acceptance.
- Ownership of a consequential decision is unknown or the requested work exceeds the user's authorization.
- New evidence materially changes an approved scope, architecture, or risk assessment.

State the blocker, its consequences, the available options, and the smallest question or decision that would unblock work. Continue independent, non-mutating analysis where useful. Stop all work if authorization or instruction conflicts make even that analysis impermissible.

If a user asks to bypass planning or approval while invoking this skill, explain the conflict and request an explicit scope decision rather than silently implementing. Never infer approval from urgency or enthusiasm.

## Engineering Rationale

Requirements and success criteria precede technology selection because architecture must solve a demonstrated problem. Stakeholder and dependency analysis exposes ownership and coordination constraints that code alone cannot resolve.

Non-functional requirements shape boundaries and operations; they are not optional review additions. Risk and complexity assessments guide investigation and milestone order. Alternatives and ADRs make expensive decisions reviewable and preserve context for maintainers.

Explicit uncertainty prevents guesses from becoming hidden commitments. Readiness and approval are separate so that a polished document cannot substitute for missing evidence or authorization.

## Anti-patterns

Do not:

- Write production code, scaffolding, migrations, or implementation prototypes before planning and applicable approval.
- Invent requirements, stakeholder decisions, existing APIs, database schemas, provider capabilities, or acceptance targets.
- Present proposed interfaces or data models as verified contracts.
- Ignore scalability, security, testing, maintainability, accessibility, privacy, reliability, or operational needs; assess relevance explicitly.
- Select a stack first and retrofit requirements to justify it.
- Add speculative architecture or abstractions without a requirement or risk-based reason.
- Hide unknowns behind confident estimates, arbitrary ratings, or a ready status.
- Treat proposed mitigations as already effective or accepted risks as implicitly authorized.
- Skip approval, interpret silence as consent, or extend approval beyond its documented scope.

## Quality Gates

Before requesting implementation approval, verify:

- Requirements are understood, sourced, and distinguishable from assumptions.
- Scope, goals, stakeholders, constraints, and out-of-scope work are explicit.
- Relevant non-functional requirements and success criteria have verification methods; missing targets are documented.
- Architecture is proposed, credible alternatives are assessed, and stack choices follow requirements.
- Important decisions have rationale and accurate status; major architectural commitments have appropriate ADRs.
- Major risks include probability, impact, mitigation, and residual risk with a stated basis.
- Dependencies, complexity, unknowns, and blocking questions are documented.
- Milestones include dependencies, meaningful exit criteria, and applicable engineering checks.
- Readiness is justified, with no unresolved blocker concealed by approval language.
- Approval is explicitly requested for a concrete scope, and no implementation has begun.

If a gate fails, revise the plan or report Needs clarification. Do not manufacture information to pass a gate.

## Behavioral Examples

These are instructional scenarios, not claims of executed validation or real project results.

### New SaaS With Missing Requirements

A request to build a SaaS activates the skill. If tenant boundaries, user roles, sensitive data, expected workload, or operational constraints are missing, inspect available context and ask questions that affect those decisions. Produce a preliminary plan with blockers and conditional alternatives; do not assume multi-tenancy rules, select infrastructure by habit, or begin scaffolding.

### Feature in an Existing Application

A substantial API feature activates the skill. Inspect existing authorization, persistence, conventions, and deployment. Preserve confirmed constraints, document compatibility and rollout needs, and compare extending the current architecture with justified alternatives. Do not invent routes or schema details as established contracts. Request approval for the proposed plan before implementation.

### Large Refactor With an Approved Plan

Inspect whether approval still covers the requested change. New migration risk or changed data ownership requires revising affected decisions and requesting renewed approval. Unchanged confirmed decisions do not require repeating discovery. Hand off only when both readiness and applicable authorization hold.

### Isolated Maintenance

A typo fix or small local refactor does not activate this skill. Do not introduce a project planning document or architecture approval gate for that request.
