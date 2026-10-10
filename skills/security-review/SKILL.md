---
name: security-review
description: Review security-relevant designs and changes involving APIs, authentication, authorization, AI systems, web or mobile applications, databases, uploads, integrations, cloud deployment, secrets, user data, infrastructure, payments, or administrative interfaces. Assess threats, evidence, controls, and residual risk proportionately. Exclude pure UI styling, simple documentation edits, formatting, non-security educational questions, and work without security relevance.
---

# Security Review

## Purpose and Boundaries

Identify consequential exposure, reduce attack surfaces, validate assumptions, and recommend proportional controls before, during, and after implementation. Security is an engineering requirement, not a final checklist.

Prefer secure defaults, least privilege, explicit trust boundaries, and independent layers of protection where they reduce credible risk. Validate external inputs according to their use and handle outputs safely in their destination context. Do not add controls merely to make a system appear secure.

Apply the activation conditions in the frontmatter to affected boundaries and behavior. A technology mention alone does not require a full application audit. Reuse existing threat models and decisions when still applicable. Scale review to the change and its consequences without implying that unreviewed areas are safe.

This is a review skill. Inspection and recommendations do not authorize remediation, configuration changes, deployment, exploitation, extraction of sensitive data, or disruptive testing. Perform those activities only within separately established scope and permissions.

## Scope, Authorization, and Evidence

Establish the reviewed components, change or revision, environment, permitted investigation, data-handling constraints, and relevant owners. Identify what is excluded, unavailable, or assumed. Use project instructions and existing authorization rather than request redundant approval for permitted local inspection.

Default to non-mutating review and safe local validation using synthetic data. Before live testing, confirm the authorized targets, accounts, techniques, side effects, and stopping conditions. Tool access is not permission to test every reachable service.

Inspect relevant code, configuration, interfaces, deployment material, tests, and operational evidence. Do not print secrets or copy sensitive records into reports. Cite paths, revisions, sanitized observations, and reproduction conditions as appropriate.

Distinguish confirmed findings, suspected weaknesses, documented assumptions, and unassessed areas under [AI-01](../../ENGINEERING_MANIFESTO.md#ai-01). Verify uncertain dependency advisories, capabilities, and configuration semantics against authoritative, version-relevant sources when available. Never invent vulnerability identifiers, affected versions, exploitability, or performed tests.

## Review Workflow

### 1. Establish Context and Security Requirements

Identify intended behavior, users, operators, deployment exposure, sensitive operations, data categories, and known obligations. Determine consequences of disclosure, unauthorized modification, unavailable service, or loss of integrity.

Clarify consequential gaps in identity, ownership, access rules, data retention, or acceptable risk. Do not infer business authorization rules from existing UI behavior. Apply [ENG-01](../../ENGINEERING_MANIFESTO.md#eng-01) and [DEC-01](../../ENGINEERING_MANIFESTO.md#dec-01).

### 2. Build or Update the Threat Model

Use the structured approach below. Follow data and authority through the affected system rather than review files in isolation. Include legitimate misuse, compromised identities, dependency failures, and adversarial actions where credible.

### 3. Inspect Controls and Defaults

Locate actual enforcement points and compare them with intended policy. Examine normal, negative, and boundary cases. Check configuration and runtime assumptions rather than accept framework defaults, architectural diagrams, or policy documents as evidence of enforcement.

### 4. Assess and Prioritize Findings

Separate risk from confidence. Explain preconditions, exposure, consequences, existing controls, and residual risk. Recommend the least complicated control that addresses the identified path without breaking required behavior.

### 5. Validate Within Authorized Boundaries

Perform proportionate checks, record their limits, and preserve evidence safely. Important fixes require regression validation; proposed tests are not evidence that a fix works.

### 6. Report and Plan Follow-up

Deliver actionable findings, scope limitations, verification evidence, unresolved decisions, and relevant monitoring or incident-readiness needs. Assign remediation or risk acceptance only to known authorized owners. Do not issue a blanket secure declaration.

## Structured Threat Modeling

Record enough detail to connect threats to assets and controls. Reuse an existing model when it represents the reviewed system accurately.

| Element | Required analysis |
| --- | --- |
| Assets | Sensitive data, credentials, money, business invariants, privileged actions, service availability, build artifacts, and other valuable resources; identify owners and consequences of loss. |
| Actors | Legitimate users, administrators, operators, service identities, external parties, and credible adversaries; distinguish authenticated actors from authorized actors. |
| Trust boundaries | Where identity, data, instructions, or authority cross components, tenants, processes, networks, devices, providers, or deployment stages. |
| Threats | Plausible abuse or failure paths with actor capability, entry point, preconditions, affected asset, and consequence. Avoid unsupported attacker capabilities. |
| Security controls | Preventive, detective, and recovery measures; identify enforcement location, dependencies, limitations, validation evidence, and remaining exposure. |

Trace meaningful paths: who supplies input, which component validates it, which identity performs the operation, what data is returned, and where effects persist. Include alternate paths such as background jobs, imports, exports, uploads, support tools, and administrative interfaces where relevant.

Map each major threat to controls or an explicit gap. Multiple controls should address distinct failure paths or contain failure, not repeat the same unverified assumption. Apply [SEC-01](../../ENGINEERING_MANIFESTO.md#sec-01).

## Risk Assessment and Findings

For each material finding, record:

- Identifier, title, status, affected asset, and trust boundary.
- Evidence, source, affected revision or configuration, and safe reproduction conditions.
- Threat or failure path, preconditions, actor capabilities, and plausible consequence.
- Likelihood or probability, impact, exposure, existing controls, and assessment basis.
- Severity and confidence as separate judgments, including unknowns.
- Recommended remediation, credible alternatives, compatibility implications, and verification method.
- Residual risk, accountable owner when known, and remediation or acceptance status.

Use established project ratings where applicable. Otherwise use qualitative judgments with reasons; do not fabricate probabilities or formal scores. A severe potential impact does not prove exploitability. Absence of evidence does not prove absence of exposure.

Use statuses such as suspected, confirmed, remediated awaiting validation, validated within scope, and accepted by an authorized owner. Do not mark a finding fixed because code changed or accepted because a reviewer did not respond.

Escalate residual risk that exceeds established tolerance or lacks an authorized owner under [SEC-02](../../ENGINEERING_MANIFESTO.md#sec-02).

## Control Decisions and Secure Defaults

For consequential choices, explain the threat addressed, enforcement point, alternatives, operational costs, failure behavior, and evidence. Preserve rationale through [DEC-02](../../ENGINEERING_MANIFESTO.md#dec-02).

| Area | Review focus |
| --- | --- |
| Authentication | Identity proof, credential recovery, service identities, abuse resistance, and strength appropriate to sensitive operations. |
| Authorization | Resource, action, tenant, and object-level policy at trusted enforcement points; alternate paths and privilege changes. Client controls are not authoritative enforcement. |
| Sessions | Creation, renewal, expiry, revocation, logout, fixation resistance, credential transport, browser protections, and concurrent-session policy as applicable. |
| Secrets | Full lifecycle, least-privilege access, delivery, storage, exposure paths, and recovery from compromise. |
| Encryption | Threat addressed in transit and at rest, key ownership, lifecycle, deployment configuration, and limits; do not design custom cryptography. |
| Input validation | Syntax, type, size, range, business invariants, canonicalization, and resource limits before dangerous use; validation is not a universal substitute for safe APIs. |
| Output handling | Destination-specific encoding, safe rendering, parameterized operations, file paths, redirects, and generated content; do not assume one escaping method protects every context. |
| Rate limiting | Abuse scenario, identity or resource scope, shared capacity, bypass paths, and behavior under dependency failure; rate limiting does not replace authorization. |
| Logging and auditability | Useful security events, correlation, integrity, access, retention, and response ownership without unnecessary sensitive payloads. |
| Dependencies and deployment | Provenance, integrity, build trust, privileges, artifact promotion, configuration, isolation, and runtime exposure. |

Prefer deny-by-default for access and privileged actions where applicable. Grant only explicit required capabilities; avoid permissive fallback when identity or policy evaluation fails. Define intentionally public behavior rather than treating all data as private or public by accident.

Check initial configuration, missing configuration, new resources, errors, and dependency outages. Safe defaults must remain safe through failure and upgrade. Where fail-closed behavior could itself create serious harm, document the tradeoff, compensating measures, and authorized decision rather than silently allowing access.

Review uploads and integrations for size, type, destination, processing limits, isolation, and access policy. Assess path traversal, injection, untrusted content execution, and server-side requests according to actual use. For payments and privileged operations, examine duplicate effects, integrity, auditability, and recovery rather than authentication alone.

## Secrets Lifecycle

Do not reproduce secret values in reports, examples, tests, or logs. If exposure is discovered, preserve only sanitized evidence and escalate through the authorized response process.

| Stage | Required review |
| --- | --- |
| Creation | Suitable generation, explicit owner and purpose, minimal scope, secure provisioning, and separation by environment or identity where needed. |
| Distribution and use | Controlled storage and delivery, least-privilege access, safe runtime handling, and avoidance of source control, client bundles, logs, or inappropriate persistence. |
| Rotation | Trigger and ownership, dependent consumers, overlap or staged replacement, verification, and recovery if rollout fails; an old exposed credential must not be restored as a convenience rollback. |
| Revocation | Ability to invalidate compromised or unnecessary credentials, propagation delay, dependent access, sessions, cached credentials, and confirmation of effective removal. |
| Expiration | Appropriate lifetime, renewal behavior, alerts, and safe failure when credentials expire; expiration alone does not handle active compromise. |
| Auditability | Evidence of creation, access, policy changes, rotation, and revocation without recording secret material; access control and retention for the audit trail. |

Distinguish passwords, service credentials, signing keys, encryption keys, and session credentials; their recovery and replacement consequences differ. For encryption-key retirement, account for historical data access and recoverability. Removing a secret from a file or repository history does not revoke it.

## Supply Chain and Deployment Security

Inspect actual resolved dependencies and artifacts, including transitive packages, plugins, build tools, installation scripts, and generated deployment outputs where relevant.

- **Provenance:** Identify intended source, maintainer or publisher, acquisition path, update policy, and trust basis. Popularity and familiar names are not sufficient evidence.
- **Integrity:** Check available integrity verification, trusted signatures or attestations, pinned resolution, and controlled artifact promotion. A checksum from an untrusted source does not establish authenticity.
- **Dependency confusion:** Examine private/public source precedence, namespaces, package resolution, and registry configuration. Confirm that private identifiers cannot unexpectedly resolve to public packages.
- **SBOM:** Use a software bill of materials when inventory, deployment traceability, response, or obligations justify it. Tie it to the actual release artifact and keep it current; an SBOM is an inventory, not a safety guarantee.
- **Build trust:** Review contributor and automation permissions, installation-time execution, release credentials, protected changes, and isolation of untrusted build inputs.
- **Exposure:** Verify runtime identity, unnecessary capabilities, network access, debug features, default accounts, and secrets in shipped artifacts.

Assess advisories against exact versions and usage where evidence permits. Automated findings require interpretation; reachability uncertainty must not be misrepresented as either confirmed exploitation or complete safety. Plan updates, removal, containment, and ownership according to risk.

## AI Security

Treat model outputs, user content, retrieved documents, memory, tool descriptions, and tool results according to their actual trust level. Model-generated instructions do not acquire execution authority merely by appearing in a valid format.

| Risk | Required assessment |
| --- | --- |
| Direct prompt injection | User attempts to override intended behavior; assess isolation, access scope, action controls, and adversarial validation. |
| Indirect prompt injection | Hostile instructions in retrieved content, tools, files, or memory; trace how they can influence privileged actions or disclosure. |
| Tool abuse and agent misuse | Argument manipulation, overprivilege, arbitrary destinations, repeated side effects, uncontrolled delegation, and execution budgets. |
| Hallucination | Unsupported claims or invented arguments reaching consequential decisions; require evidence, validation, abstention, or appropriate review. |
| Sensitive data leakage | Prompts, outputs, providers, telemetry, caches, and tool egress; assess minimization, retention, permissions, and isolation. |
| RAG data exposure | Ingestion rights, retrieval authorization, tenant boundaries, derived indexes, stale permissions, citations, and deletion propagation. |
| Model output validation | Syntax and semantic constraints, safe rendering, destination-specific handling, and trusted-side policy enforcement. |
| Human approval | Exact action and scope presented, authorized reviewer, approval binding, changed arguments, expiry, denial, and enforcement outside the model. |
| Model trust boundaries | Separation of probabilistic behavior from identity, policy, sensitive data access, and irreversible operations. |

Prompts and delimiters can improve clarity but do not eliminate injection. Citations do not establish correctness. Human review is a control with limitations, not a guarantee. Do not rely on self-reported model confidence as a safety gate.

Evaluate hostile content and outputs using safe fixtures and bounded permissions. Avoid live exfiltration or destructive actions to demonstrate a flaw. For tools, distinguish rejected calls, successful invocation, and actual effects; reconcile uncertain effects before retries.

## Validation and Security Regression

Choose validation from the threat model and consequences under [VAL-01](../../ENGINEERING_MANIFESTO.md#val-01). Combine appropriate code inspection, configuration checks, local tests, dependency analysis, and authorized runtime checks. State what each method establishes and leaves untested.

Exercise allowed and denied paths. Relevant cases include unauthenticated access, insufficient privilege, cross-user and cross-tenant access, expired or revoked credentials, malformed or oversized input, unsafe output contexts, and failures in security dependencies.

Important security fixes require durable regression coverage at the enforcement boundary. Reproduce the original security invariant violation safely, verify that the fix blocks it, and confirm legitimate behavior still works. Cover related paths or variants when they share the faulty assumption.

Prefer tests of the violated invariant over tests that match one payload or implementation detail. Use synthetic credentials and data; do not preserve real leaked secrets or sensitive records in fixtures. When feasible, establish that a regression case fails against the vulnerable baseline in an isolated authorized environment without modifying the user's working state.

If automation is not practical, document a repeatable manual or configuration validation procedure, execution evidence, owner, and revisit trigger. Do not equate a proposed procedure with performed validation. Retain important regression cases through refactors and dependency changes.

Scanner output is evidence to investigate, not a complete security assessment. A passing test suite or lack of findings is not proof of safety under [VAL-02](../../ENGINEERING_MANIFESTO.md#val-02).

## Monitoring and Incident Readiness

Identify useful signals for suspicious access, privilege changes, secret misuse, validation failures, abnormal tool activity, dependency exposure, and integrity violations where relevant. Define thresholds or investigation criteria from actual operational needs, not invented targets.

Ensure alerts have owners and feasible response actions. Assess telemetry permissions, retention, redaction, integrity, availability, and sensitive-data exposure. Audit trails should support investigation without becoming a secondary source of secrets.

Review containment, credential revocation, access suspension, rollback or repair, evidence preservation, recovery validation, and appropriate communication routes. Do not invent incident contacts or notify others without authorization. Disclosure and notification obligations must be confirmed by accountable owners.

## Reporting, Escalation, and Quality Gates

Report reviewed scope and revision, evidence sources, findings prioritized by justified risk, suggested controls, validation performed, limitations, and required decisions. Use local file references and sanitized detail sufficient for remediation. Preserve rationale under [DOC-02](../../ENGINEERING_MANIFESTO.md#doc-02).

Stop dependent investigation and request clarification when authorization is unclear, safe validation would require live effects, sensitive evidence cannot be handled within scope, or consequential policy is missing. Explain the blocker, options, and minimum decision needed. Continue independent permitted analysis where useful.

If a live secret, active compromise, or serious exposure is observed, avoid amplifying it and promptly report through authorized channels. Do not independently rotate credentials, disable accounts, or change production configuration unless authorized.

Before completing the review, verify that relevant areas are assessed or explicitly marked unassessed or inapplicable:

- Authentication fits the known identity and risk requirements.
- Authorization is enforced at trusted boundaries, including alternate and cross-resource paths.
- Secrets have protected storage, delivery, lifecycle, and response mechanisms.
- External inputs are validated and outputs handled safely for their destination.
- Secure defaults and security-dependency failures behave as intended.
- Dependencies and artifacts have an explicit trust basis, integrity checks where available, and understood supply-chain exposure.
- Logging, auditability, monitoring, and incident ownership are appropriate.
- AI trust boundaries and action controls are reviewed where applicable.
- Assumptions, residual risk, finding confidence, and limitations are documented.
- Important fixes have meaningful regression validation or a disclosed validation gap.

An unassessed area is a limitation, not a passed gate. Distinguish review complete, remediation proposed, remediation awaiting validation, and validated within scope. Risk acceptance requires an authorized owner and does not establish that a vulnerability is fixed.

## Anti-patterns

Do not rely on obscurity, hardcode secrets, grant excessive privileges, trust external input or AI output blindly, or disable controls for convenience.

Do not accept framework defaults without verifying their application, ignore dependency exposure, or substitute a scanner report for threat analysis. Avoid blanket encryption, authentication, or logging recommendations without explaining the threat and consequences.

Do not exaggerate exploitability, prescribe controls unrelated to credible risk, imply universal security from limited review, or hide uncertainty behind severity labels. Do not treat approval, absence of reported incidents, or a successful happy-path test as proof of control effectiveness.

## Coordination With Existing Skills

[project-planner](../project-planner/SKILL.md) owns substantial scope, architecture planning, milestones, and approval. Supply security requirements, threats, controls, and validation criteria without taking over its decision ownership.

[mentor-mode](../mentor-mode/SKILL.md) explains findings and tradeoffs at the user's preferred depth; explanation is not verification.

[ai-engineer](../ai-engineer/SKILL.md) owns AI architecture, evaluation, implementation, and operation. Review its trust boundaries, retrieval access, tool controls, and residual risk without creating a competing architecture.

[frontend-master](../frontend-master/SKILL.md) owns interface behavior. Review browser exposure, session interactions, output handling, and approval presentation while distinguishing UI controls from authoritative enforcement.

These references do not require every skill for every review. Preserve scope, authorization, and truthful reporting through [AI-02](../../ENGINEERING_MANIFESTO.md#ai-02), [PRO-01](../../ENGINEERING_MANIFESTO.md#pro-01), and [PRO-02](../../ENGINEERING_MANIFESTO.md#pro-02).

## Behavioral Examples

These are instructional scenarios, not executed validation results.

### Resource Authorization

An endpoint authenticates callers but the resource ownership check is unclear. Trace authoritative enforcement and alternate paths, distinguish suspicion from confirmed cross-user access, and validate using permitted synthetic accounts. Recommend invariant-based regression cases for both allowed and denied access.

### Exposed Credential

A credential appears in a tracked file. Report sanitized evidence, assess scope and lifecycle, and request authorized revocation or rotation. Removing the file is not a complete remedy and deleting history does not invalidate the credential.

### Package Resolution

A private dependency can resolve through a public source. Review actual source precedence and build identity before claiming dependency confusion is exploitable. Recommend controlled resolution and release-artifact verification with a regression check of the intended source.

### Retrieval-Enabled Agent

Retrieved content can influence a tool request. Trace document access, instruction handling, tool authorization, and egress boundaries. Use a safe adversarial fixture to validate rejection or containment; do not demonstrate leakage using real secrets or unauthorized destinations.
