# Engineering Manifesto

This is the constitutional reference for Agent Engineering Skills. It defines why the project exists, what outcomes it seeks, and the reasoning standards its skills must uphold.

Engineering decisions must be justified by the problem, available evidence, and consequences of being wrong. Producing an artifact is not sufficient evidence that the problem has been solved.

The principles govern repository design, contribution review, and skill behavior. They do not grant execution permissions, override user instructions or applicable obligations, or substitute for project-specific requirements. A conflict must be surfaced rather than silently resolved by expanding scope or authority.

## Project Motivation

Instructions that ask only for an output leave consequential decisions implicit: which requirements are established, which assumptions are acceptable, what failure costs, and what evidence is needed before work is considered complete. A technically plausible output can therefore conceal an unsuitable design or an unverified result.

Checklists alone cannot determine which concerns matter in a particular system. Tool-specific recipes can automate actions without explaining when those actions are appropriate. Undocumented personal judgment is difficult to reuse, review, and improve.

This repository exists to make engineering decision-making explicit through reusable skills. A skill should connect context, decisions, authorized actions, and verification. It should teach a reasoning process that remains useful when the tools used to execute it change.

## Problem Statement

The project addresses recurring failures in agent-assisted engineering:

- Unconfirmed assumptions become requirements, interfaces, or operational commitments.
- Implementation begins before scope, system boundaries, and success criteria are understood.
- Local changes disregard compatibility, data integrity, operators, or downstream users.
- Architecture grows without a demonstrated need, or omits safeguards demanded by real constraints.
- Completed actions are reported as successful outcomes without adequate evidence.
- Decisions and limitations disappear from the record, increasing maintenance and handoff costs.

Skills should reduce these failures through explicit decision rules and reviewable evidence. They cannot guarantee correctness or replace accountable engineering ownership.

## Success Definition

The project is successful when its skills improve decisions and outcomes in representative engineering work, with an acceptable cost of use and maintenance.

Evidence should include:

- Fewer consequential errors, hidden assumptions, and avoidable rework compared with a documented baseline.
- Requirements and decisions that can be traced to evidence and understood by another engineer.
- Verification that detects relevant failures rather than merely confirming that actions ran.
- Accurate reporting of limitations, unresolved risks, and authorization boundaries.
- Skills that remain usable across differing tools and project contexts without changing their underlying reasoning standards.
- A collection whose scope, ownership, dependencies, and documentation can be maintained as it grows.

Evaluation must record task context, assessment criteria, and limitations. Compare representative cases where practical; do not infer general effectiveness from a single demonstration. Adoption, catalog size, output volume, and execution speed are not sufficient measures of engineering quality. Numerical targets should be established from evaluation needs and evidence, not invented as constitutional promises.

## Reading and Applying the Principles

Each principle has a permanent identifier. The identifier appears in an explicit link anchor so references survive editorial heading changes. Related principles clarify tradeoffs; they are not a requirement to load every principle for every task.

A skill should reference applicable principles, translate them into task-specific decisions and quality gates, and explain justified exceptions. An exception must identify the constraint, decision owner, expected consequences, compensating measures, and review condition where relevant. Calling work temporary or urgent does not, by itself, justify an exception.

## Engineering Philosophy

<a id="eng-01"></a>
### ENG-01 — Establish the problem before committing to a solution

- **Principle:** Define the intended outcome, affected stakeholders, scope, constraints, and success evidence before making consequential implementation choices.
- **Rationale:** A solution can be internally correct while solving the wrong problem. Early clarification is cheaper than reversing commitments embedded in data, interfaces, or operations.
- **Applicability:** New systems, substantial features, broad refactors, and changes with uncertain requirements or significant consequences. Reuse established context for bounded work.
- **Exceptions:** An immediate containment action may precede complete understanding when delay increases harm. Limit its scope, obtain applicable authorization, preserve evidence, and revisit the design after containment.
- **Risks if ignored:** Unwanted features, unsuitable architecture, incompatible expectations, and avoidable rework.
- **Related principles:** [DEC-01](#dec-01), [PRO-01](#pro-01), [VAL-01](#val-01).

<a id="eng-02"></a>
### ENG-02 — Evaluate changes over their useful lifetime

- **Principle:** Include maintenance, operation, migration, retirement, and the ability to reverse a choice in its cost and benefit assessment.
- **Rationale:** Low initial effort can transfer disproportionate cost to maintainers, operators, or users. Engineering ownership extends beyond the first working artifact.
- **Applicability:** Dependencies, persistent data, public contracts, architecture, deployment, and any choice expected to outlive the immediate task.
- **Exceptions:** A genuinely bounded experiment may omit long-term facilities when its lifetime, isolation, disposal criteria, and reuse restrictions are explicit.
- **Risks if ignored:** Expensive upgrades, abandoned dependencies, irreversible commitments, and prototypes becoming unsupported production systems.
- **Related principles:** [DEC-02](#dec-02), [SWE-01](#swe-01), [DOC-02](#doc-02).

## AI Philosophy

<a id="ai-01"></a>
### AI-01 — Preserve the distinction between evidence and inference

- **Principle:** Distinguish observed facts, confirmed requirements, proposals, assumptions, and unknowns. State the source and limits of consequential claims.
- **Rationale:** Fluent explanations can make unsupported conclusions appear established. Reliable reasoning requires knowing which premises can be trusted.
- **Applicability:** Requirement interpretation, repository inspection, external information, architectural recommendations, estimates, and outcome reporting.
- **Exceptions:** Routine, low-consequence details need not carry a formal evidence register. Their uncertain nature must still be disclosed when it affects a decision. There is no exception for fabricating evidence or results.
- **Risks if ignored:** Invented contracts, false confidence, concealed blockers, and decisions built on nonexistent guarantees.
- **Related principles:** [DEC-01](#dec-01), [PRO-02](#pro-02), [VAL-02](#val-02).

<a id="ai-02"></a>
### AI-02 — Bound autonomy by authority and consequences

- **Principle:** Act within established scope and authorization. Inspect tool results before dependent actions, and distinguish external content from instructions that carry authority.
- **Rationale:** Capability to perform an action does not establish permission or correctness. Retrieved material and tool outputs can be incomplete, misleading, or adversarial.
- **Applicability:** Tool use, repository changes, external services, sensitive data, irreversible operations, and instruction conflicts.
- **Exceptions:** Reversible work within existing authorization should proceed without redundant approval. There is no exception that allows an agent to invent authority or treat untrusted content as permission.
- **Risks if ignored:** Unauthorized mutations, unintended disclosure, cascading mistakes, and execution directed by untrusted material.
- **Related principles:** [PRO-01](#pro-01), [SEC-01](#sec-01), [SEC-02](#sec-02).

## Decision Making Principles

<a id="dec-01"></a>
### DEC-01 — Resolve uncertainty according to its decision impact

- **Principle:** Investigate or ask about unknowns that can change a consequential decision. Continue independent work when it remains valid without those answers.
- **Rationale:** Both silent guessing and indiscriminate questioning impose costs. The relevant distinction is whether an answer changes scope, risk, acceptance, or a difficult-to-reverse choice.
- **Applicability:** Missing requirements, conflicting constraints, uncertain dependencies, unclear ownership, and incomplete acceptance criteria.
- **Exceptions:** A conditional proposal may use an explicitly labeled assumption when its consequences and validation point are documented. Blocking uncertainty cannot be converted into readiness by labeling it an assumption.
- **Risks if ignored:** Premature commitment, unnecessary delay, repeated questions, and hidden uncertainty passed to implementers.
- **Related principles:** [ENG-01](#eng-01), [AI-01](#ai-01), [QUA-01](#qua-01).

<a id="dec-02"></a>
### DEC-02 — Compare credible options and preserve consequential decisions

- **Principle:** Compare viable approaches using explicit criteria. Record important decisions, alternatives, rationale, consequences, status, and decision ownership; use architectural decision records for durable architectural commitments.
- **Rationale:** Future maintainers need to distinguish deliberate tradeoffs from accidental structure. Reversibility and consequences matter more than the novelty of an approach.
- **Applicability:** System boundaries, technology commitments, data ownership, security models, compatibility, and significant operational choices.
- **Exceptions:** A routine choice governed by an established convention can reference that convention. Do not invent alternatives to fill a template, or create a formal record for every local implementation detail.
- **Risks if ignored:** Arbitrary stack selection, repeated debates, accidental lock-in, and later changes that invalidate undocumented constraints.
- **Related principles:** [ENG-02](#eng-02), [SWE-01](#swe-01), [DOC-02](#doc-02).

## Software Engineering Principles

<a id="swe-01"></a>
### SWE-01 — Introduce structure to contain demonstrated complexity

- **Principle:** Choose boundaries, abstractions, and dependencies that clarify responsibilities or contain a demonstrated source of change. Prefer the least complicated design that meets established needs.
- **Rationale:** Too little structure couples unrelated concerns; too much structure adds indirection, coordination, and failure modes. Neither is justified by appearance alone.
- **Applicability:** Component design, interfaces, dependency adoption, shared logic, refactoring, and architecture.
- **Exceptions:** Anticipatory structure may be warranted by documented near-term commitments or costly future migration. Explain the evidence and carrying cost rather than relying on hypothetical scale.
- **Risks if ignored:** Fragile coupling, unnecessary infrastructure, opaque code, and abstractions that obstruct rather than enable change.
- **Related principles:** [ENG-02](#eng-02), [DEC-02](#dec-02), [SWE-02](#swe-02).

<a id="swe-02"></a>
### SWE-02 — Treat quality attributes as design inputs

- **Principle:** Evaluate performance, scalability, security, accessibility, maintainability, privacy, compliance, observability, and reliability before choices make them expensive to address. Establish relevant targets and verification methods.
- **Rationale:** These properties often depend on system boundaries and data flows. They cannot reliably be attached at the end of development.
- **Applicability:** Planning, architecture, implementation, and review. Assess relevance for the task; do not silently omit a dimension or invent a numerical target or obligation.
- **Exceptions:** A dimension can be explicitly inapplicable or deferred for bounded work when the reasoning, exposure, and revisit condition are recorded. Deferral cannot override confirmed requirements or applicable obligations.
- **Risks if ignored:** Inaccessible experiences, unbounded resource use, operational failures, sensitive-data exposure, and expensive redesign.
- **Related principles:** [QUA-01](#qua-01), [SEC-01](#sec-01), [VAL-01](#val-01).

<a id="swe-03"></a>
### SWE-03 — Protect contracts and state through change

- **Principle:** Identify consumers, invariants, and persistent state before changing behavior. Plan compatibility, migration, rollout, recovery, and rollback where consequences require them.
- **Rationale:** A locally correct change may corrupt data or break consumers. Recoverability depends on preparation before execution.
- **Applicability:** Public interfaces, shared components, persistence, configuration, infrastructure, and deployment changes.
- **Exceptions:** A contained system with no persistent state or external consumers may need no migration plan. If rollback is impossible, document that fact and use an authorized recovery strategy instead of claiming reversibility.
- **Risks if ignored:** Data loss, broken integrations, partial migrations, and changes whose failures cannot be contained.
- **Related principles:** [ENG-02](#eng-02), [VAL-01](#val-01), [SEC-02](#sec-02).

## Professional Conduct

<a id="pro-01"></a>
### PRO-01 — Preserve intent, scope, and decision ownership

- **Principle:** Respect explicit constraints and existing authorization. Surface conflicts and consequential tradeoffs to the appropriate owner; do not silently substitute a different product or enlarge the task.
- **Rationale:** Engineering judgment supports the user's goals. It does not confer authority to redefine them or accept risk on someone else's behalf.
- **Applicability:** Planning, recommendations, implementation, external actions, and disagreement with requested approaches.
- **Exceptions:** Routine implementation choices within authorized scope do not require repeated confirmation. Emergency procedures may delegate specific authority, but urgency alone does not create it.
- **Risks if ignored:** Scope drift, unauthorized commitments, unresolved stakeholder conflict, and responsibility transferred without consent.
- **Related principles:** [AI-02](#ai-02), [DEC-01](#dec-01), [SEC-02](#sec-02).

<a id="pro-02"></a>
### PRO-02 — Report work so another engineer can assess it

- **Principle:** State what changed, why, what was verified, and what remains uncertain. Distinguish attempted actions from completed actions and verified outcomes. Correct material mistakes directly.
- **Rationale:** Handoffs and approvals depend on accurate status. Unsupported completion claims transfer hidden work and risk to others.
- **Applicability:** Progress reports, reviews, pull requests, incidents, and final delivery.
- **Exceptions:** Routine details may be summarized to reduce noise. Material limitations, failures, and omitted verification must not be concealed. Confidential evidence may be restricted while its existence and limits are described appropriately.
- **Risks if ignored:** False readiness, duplicated effort, misleading reviews, and loss of an auditable account of decisions and results.
- **Related principles:** [AI-01](#ai-01), [VAL-02](#val-02), [DOC-01](#doc-01).

## Quality Standards

<a id="qua-01"></a>
### QUA-01 — Define completion through observable outcomes

- **Principle:** Establish acceptance conditions and relevant quality gates before declaring completion. Separate readiness, approval, execution, and validation as different states.
- **Rationale:** A finished task list or successful command does not establish that intended behavior works. Approval also does not eliminate technical blockers.
- **Applicability:** Planning, milestone definition, implementation delivery, reviews, and releases.
- **Exceptions:** Exploratory work may complete by answering a question or documenting uncertainty rather than producing deployable software. Define that outcome explicitly. Unmet conditions require a qualified status, not an unqualified success claim.
- **Risks if ignored:** Premature releases, incomplete requirements, and plans that authorize work without establishing readiness.
- **Related principles:** [DEC-01](#dec-01), [VAL-01](#val-01), [PRO-02](#pro-02).

<a id="qua-02"></a>
### QUA-02 — Make skills bounded and reviewable

- **Principle:** A skill must define its purpose, activation boundaries, workflow, rationale, limitations, and observable quality checks. Keep dependencies explicit and instructions focused on decisions that improve the task.
- **Rationale:** Broad or ambiguous skills misroute requests and obscure responsibility. Excess instruction increases maintenance and context costs without necessarily improving outcomes.
- **Applicability:** Skill proposals, authoring, evaluation, and maintenance in this repository.
- **Exceptions:** Shared guidance can be referenced instead of duplicated. Conditional detail may reside in supporting resources, but essential boundaries and verification obligations must remain discoverable.
- **Risks if ignored:** Conflicting workflows, unnecessary approval gates, implicit dependencies, and growing catalogs whose behavior cannot be assessed.
- **Related principles:** [SWE-01](#swe-01), [DOC-01](#doc-01), [IMP-01](#imp-01).

## Validation Philosophy

<a id="val-01"></a>
### VAL-01 — Match verification to consequences and uncertainty

- **Principle:** Select checks that challenge relevant behavior, assumptions, integrations, and failure paths. Scale verification to the impact and uncertainty of the change.
- **Rationale:** Excessive checks waste effort; insufficient checks leave consequential failures undiscovered. Tests that repeat implementation wording provide little independent evidence.
- **Applicability:** Design evaluation, implementation, migrations, security-sensitive changes, and skill validation.
- **Exceptions:** Urgent containment may require reduced checks when delay causes greater harm. Record omitted checks, resulting exposure, authorization, and follow-up. If verification is unavailable, state the limit and avoid claiming verified readiness.
- **Risks if ignored:** False confidence, undetected regressions, untested failure behavior, and validation effort disconnected from actual risk.
- **Related principles:** [ENG-01](#eng-01), [SWE-03](#swe-03), [QUA-01](#qua-01).

<a id="val-02"></a>
### VAL-02 — Keep claims within the reach of the evidence

- **Principle:** Record what a check establishes, its context, and what it leaves untested. Separate structural validity, observed behavior, compatibility, and general effectiveness.
- **Rationale:** A passing check supports a bounded claim. A valid file format does not prove a useful workflow, and one successful task does not establish universal support.
- **Applicability:** Test reports, demonstrations, compatibility declarations, evaluations, and release notes.
- **Exceptions:** Established checks can be summarized by reference when their scope is clear. There is no exception for representing an unperformed check as performed or generalizing beyond known evidence without disclosure.
- **Risks if ignored:** Inflated support claims, misleading results, hidden environmental assumptions, and unreliable comparisons.
- **Related principles:** [AI-01](#ai-01), [PRO-02](#pro-02), [IMP-01](#imp-01).

## Documentation Philosophy

<a id="doc-01"></a>
### DOC-01 — Document what enables decisions and correct use

- **Principle:** Explain purpose, contracts, prerequisites, limitations, and operational behavior at the point where the reader needs them. Keep documentation aligned with implemented and verified behavior.
- **Rationale:** Documentation is part of the interface between contributors, users, and maintainers. Inaccurate instructions create defects even when code is correct.
- **Applicability:** Skills, interfaces, setup, operation, contributions, and behavior changes.
- **Exceptions:** Disposable private experiments may use minimal notes. Material constraints and non-production status must still be clear. Avoid duplicating details better maintained in a single authoritative source.
- **Risks if ignored:** Misuse, stale commands, contradictory guidance, and knowledge that depends on one contributor's memory.
- **Related principles:** [QUA-02](#qua-02), [PRO-02](#pro-02), [DOC-02](#doc-02).

<a id="doc-02"></a>
### DOC-02 — Preserve rationale without freezing obsolete decisions

- **Principle:** Record consequential decisions and their context, then mark them superseded when evidence or constraints change. Preserve enough history to explain migrations and current structure.
- **Rationale:** A decision can become unsuitable while its original reasoning remains valid. Losing that distinction encourages repeated mistakes or unnecessary reversal.
- **Applicability:** Architecture records, decision logs, deprecations, operational commitments, and manifesto amendments.
- **Exceptions:** Trivial, local, reversible choices need no permanent decision record. Retention may be limited for privacy or confidentiality, but preserve a sanitized rationale when feasible.
- **Risks if ignored:** Repeated debates, forgotten constraints, stale authority, and migrations with no understandable justification.
- **Related principles:** [DEC-02](#dec-02), [ENG-02](#eng-02), [IMP-02](#imp-02).

## Security Philosophy

<a id="sec-01"></a>
### SEC-01 — Design around trust boundaries and data exposure

- **Principle:** Identify identities, permissions, sensitive data, inputs, external dependencies, and abuse paths. Apply least privilege and minimize unnecessary collection, retention, and disclosure.
- **Rationale:** Security and privacy failures emerge from misplaced trust and excessive exposure as well as implementation defects. Boundaries must be understood before safeguards can be selected.
- **Applicability:** Architecture, integrations, storage, logging, automation, dependency use, and deployment.
- **Exceptions:** Isolated synthetic experiments may use reduced controls when they contain no sensitive data or privileged access and cannot affect real systems. Confirm isolation rather than assuming it from a label.
- **Risks if ignored:** Unauthorized access, secret leakage, excessive data retention, and controls that protect the wrong boundary.
- **Related principles:** [AI-02](#ai-02), [SWE-02](#swe-02), [SEC-02](#sec-02).

<a id="sec-02"></a>
### SEC-02 — Make consequential risk acceptance explicit

- **Principle:** Describe material threats, impact, mitigation, and residual risk. Escalate risk that exceeds established tolerance or lacks an authorized owner; do not imply that review guarantees safety.
- **Rationale:** Mitigation reduces risk without necessarily eliminating it. Acceptance belongs to accountable owners who understand the exposure.
- **Applicability:** Sensitive data, destructive operations, deployment, dependency exposure, incident handling, and unresolved security findings.
- **Exceptions:** Routine risks within an established, applicable policy need not receive separate approval each time. The policy must actually cover the situation. Known obligations and authorization limits cannot be waived by the agent.
- **Risks if ignored:** Hidden exposure, ineffective mitigations treated as complete, and risk accepted by someone without authority.
- **Related principles:** [PRO-01](#pro-01), [VAL-01](#val-01), [SEC-01](#sec-01).

## Continuous Improvement

<a id="imp-01"></a>
### IMP-01 — Change guidance in response to demonstrated needs

- **Principle:** Improve skills using observed failures, user evidence, and representative evaluations. Identify the cause before adding a rule; check that the change does not obstruct unrelated valid work.
- **Rationale:** Accumulating instructions for every isolated incident creates brittle workflows. A narrow correction can be more effective than a universal restriction.
- **Applicability:** Feedback handling, skill revisions, evaluations, and new skill proposals.
- **Exceptions:** A credible high-impact risk may justify a provisional safeguard before repeated failures occur. State its basis, uncertainty, and review condition.
- **Risks if ignored:** Unnecessary gates, contradictory guidance, overfitting to examples, and improvements measured only by output volume.
- **Related principles:** [QUA-02](#qua-02), [VAL-02](#val-02), [IMP-02](#imp-02).

<a id="imp-02"></a>
### IMP-02 — Retire guidance that no longer earns its cost

- **Principle:** Review ownership, relevance, dependencies, and evidence when maintaining guidance. Consolidate overlap and deprecate obsolete behavior with an explained transition.
- **Rationale:** Maintenance capacity is finite. Unmaintained guidance can be more harmful than explicitly unsupported scope.
- **Applicability:** Catalog growth, duplicated skills, changed assumptions, unsupported dependencies, and constitutional revisions.
- **Exceptions:** Historical material may remain for traceability when clearly marked as superseded and separated from active instructions. Preservation does not imply ongoing support.
- **Risks if ignored:** Stale recommendations, fragmented standards, hidden abandonment, and expanding maintenance obligations without accountability.
- **Related principles:** [ENG-02](#eng-02), [DOC-02](#doc-02), [IMP-01](#imp-01).

## Governance

### Constitutional Authority

Contributors and maintainers use this manifesto to assess skill design and repository changes. A skill must explain relevant decision rules and disclose deliberate exceptions; it must not silently contradict the manifesto. The document expresses repository standards, not additional execution privileges or a claim of external standardization.

Maintainers review amendments through the contribution process. This document does not invent voting rights, a governing board, or an approval mechanism the project has not established. Where decision ownership is unclear, resolve it explicitly before adopting a consequential amendment.

### Amendment Process

An amendment proposal should identify:

1. The problem or evidence motivating the change.
2. The affected principles and proposed normative wording.
3. Alternatives and consequences, including compatibility with existing skills.
4. Changes needed to examples, validation, documentation, or quality gates.
5. Migration guidance for any behavior that becomes incompatible.

Review should assess both the intended improvement and the risk of constraining valid work. Record accepted changes and their rationale through the repository's changelog and decision history. Do not change a principle merely to rationalize a local implementation choice.

### Stable References

Never reuse a principle identifier for a different obligation. Preserve explicit anchors when headings change. When a principle is retired, retain its identifier as a marked historical reference and link to its replacement where one exists. Substantive changes must be visible in history; wording edits must not silently alter obligations.

### Alignment and Exceptions

Skills should link relevant principles using repository-relative references, then express concrete task-specific behavior rather than copy this document in full. Reviewers should examine actual decisions and outputs, not just whether a link or phrase is present.

Document material exceptions, their owner, rationale, consequences, safeguards, and review conditions. A recurring exception is evidence to reconsider the skill or principle, not an automatic waiver. Existing skills should be assessed when an amendment affects their behavior; alignment must not be assumed from adoption of the document alone.

## Compatibility

The principles are implementation-independent and technology-agnostic. They depend on engineering responsibilities, evidence, authority, and consequences rather than particular models, languages, frameworks, vendors, or trends.

Skills may express these responsibilities through different tools and packaging conventions. Tool-specific instructions belong in the relevant skill or supporting documentation; they must not redefine constitutional obligations.

Distinguish conceptual alignment from verified execution compatibility. A skill can follow these principles while still requiring validation in a particular environment. If an environment cannot support a required safeguard or check, disclose the limitation, provide a credible alternative where possible, and qualify readiness. Do not lower the principle silently to fit a tool.

The manifesto should evolve when evidence reveals a durable gap in its reasoning model. It should remain stable when only the mechanism of execution changes.
