---
name: frontend-master
description: Design, implement, review, and maintain accessible, responsive, performant, resilient user interfaces using frontend frameworks, HTML/CSS, styling utilities, component libraries, or design systems. Apply to frontend architecture, client-side state, and UI implementation. Exclude backend APIs, database design, AI architecture, infrastructure, and pure algorithm questions.
---

# Frontend Master

## Purpose and Boundaries

Design for users before developers and maintainability before cleverness. Treat accessibility as a requirement, performance as a user-facing property, and consistency as a foundation for understandable interaction. Prefer clarity over visual complexity.

Approach the interface as a system of tasks, information, interactions, state, rendering, and failure behavior. Visual appearance is one part of quality, not proof of correctness or usability.

Activate for React, Next.js, Vue, Angular, Svelte, HTML/CSS, Tailwind, component libraries, design systems, responsive interfaces, accessibility, frontend architecture, client-side state, and UI implementation. Technology mentions alone do not justify expanding the task. Exclude unrelated backend, database, AI architecture, infrastructure, and algorithm work.

Preserve the user's scope, project instructions, established design language, and execution permissions. Do not introduce a framework, library, design system, or repository-wide rewrite without a demonstrated need and applicable authorization. Scale investigation to the change; a bounded component fix does not require redesigning the application.

## Evidence and Engineering Decisions

Inspect the existing application before recommending replacements. Distinguish requirements, observed behavior, proposals, assumptions, and unknowns under [AI-01](../../ENGINEERING_MANIFESTO.md#ai-01). Verify uncertain, version-sensitive framework or platform capabilities using authoritative documentation when available; otherwise disclose the uncertainty.

For consequential choices, record the requirement addressed, alternatives, rationale, costs, limitations, evidence, and revisit conditions. Reuse existing decision records. Apply [DEC-02](../../ENGINEERING_MANIFESTO.md#dec-02) to these questions:

| Decision | Required reasoning |
| --- | --- |
| Component structure | Which responsibilities, state boundaries, accessibility contracts, or reuse needs justify the decomposition? |
| State management | Who owns each value, who needs it, how long does it live, and why is local state or an existing mechanism insufficient? |
| Client-side rendering | Which interactions or deployment constraints require browser execution, and what are the loading, accessibility, and resource costs? |
| Server or static rendering | Which content, discovery, initial-delivery, or data-access needs justify it, and what are the freshness, caching, and hydration consequences? |
| Routing | Which navigable states need stable URLs, deep links, history behavior, authorization, and recovery? |
| Design pattern | Which user task or interaction problem does the pattern solve, and what usability or accessibility costs does it introduce? |
| Styling | How does the approach fit existing conventions, token ownership, theming, responsive behavior, and maintenance needs? |
| Optimization | What measured bottleneck or established budget justifies added complexity, and how will improvement be verified? |

Do not invent alternatives or measurements. Preserve explicit choices unless a conflict is surfaced and resolved.

## Engineering Workflow

### 1. Understand Requirements and User Goals

Inspect repository instructions, relevant screens, components, tokens, routing, state, tests, and build configuration. Identify primary tasks, users, content, input methods, supported environments, constraints, and acceptance criteria.

Clarify consequential gaps, such as user permissions, required form behavior, content priority, supported browsers, or recovery expectations. Do not infer business rules or API contracts from a visual mockup. Continue independent authorized analysis while blocked decisions await answers.

Follow [ENG-01](../../ENGINEERING_MANIFESTO.md#eng-01) and [DEC-01](../../ENGINEERING_MANIFESTO.md#dec-01). For substantial work, contribute frontend findings to the approved project plan rather than start implementation prematurely.

### 2. Design Information and Interaction

Define content hierarchy, navigation, task sequence, meaningful URLs, primary actions, feedback, and recovery. Use existing interaction conventions unless requirements justify a change. Consider destructive-action confirmation, interruption, undo, and preservation of user work.

Describe accessibility, responsive behavior, and the UX state model before component selection. A mockup of the success state alone is incomplete interaction design.

### 3. Establish Architecture and Design Contracts

Choose composition, state ownership, data flow, rendering boundaries, routing, caching, and styling based on requirements. Reuse the design system where suitable. Identify dependencies, compatibility risks, and performance budgets that are actually established.

Document component contracts and the ownership of asynchronous state, focus, errors, and recovery. Include relevant quality attributes through [SWE-02](../../ENGINEERING_MANIFESTO.md#swe-02), with structure justified under [SWE-01](../../ENGINEERING_MANIFESTO.md#swe-01).

### 4. Implement Within Approved Scope

Use semantic elements and accessible behavior first. Implement complete relevant states and transitions, responsive layout, form validation, cancellation, and failure recovery alongside the primary path.

Keep interfaces and state understandable. Do not expand scope through incidental cleanup, dependency replacement, or speculative abstraction. Preserve contracts and rollout compatibility under [SWE-03](../../ENGINEERING_MANIFESTO.md#swe-03).

### 5. Verify and Review

Exercise relevant user tasks, state transitions, keyboard behavior, focus, responsive layouts, failure cases, and supported environments. Measure performance where the change affects it. Use automated checks and manual examination for their distinct purposes.

Review composition, state ownership, token use, dependencies, and documentation. Report observed outcomes, omitted checks, and remaining limitations under [PRO-02](../../ENGINEERING_MANIFESTO.md#pro-02) and [VAL-02](../../ENGINEERING_MANIFESTO.md#val-02). A screenshot or passing automated accessibility scan alone does not establish production quality.

## UX State Model

For each data-driven view and consequential interaction, identify applicable states, entry conditions, transitions, permitted actions, feedback, and recovery. Record why a state is not applicable instead of silently omitting it.

| State | Required behavior |
| --- | --- |
| Idle | Explain what is available and what begins the interaction; do not imply that unrequested data is empty. |
| Loading | Indicate pending work without misleading progress; preserve useful content and user input, and control repeated actions. |
| Success | Confirm the actual outcome and expose the next useful action; distinguish completed mutations from merely accepted requests. |
| Empty | Distinguish no records, no search matches, and filtered results; explain an appropriate next step. |
| Error | Explain the failure at a useful level, preserve recoverable work, and offer a safe retry, correction, or escalation. |
| Unauthorized | Distinguish missing authentication from insufficient permission where safe; avoid exposing protected content and provide an appropriate route forward. |
| Offline | Explain connectivity and freshness limits, preserve permitted local work, and distinguish local changes from synchronized results. |

States may compose: cached content can remain visible while refresh fails, and a pending mutation can coexist with usable data. Avoid contradictory boolean flags; use explicit transitions where complexity warrants them.

Handle stale responses, races, unmounts, cancellation, and interrupted navigation. Prevent old results from overwriting newer intent. Define whether cancellation only stops display or also stops server work; do not claim reversal without evidence.

## Accessibility and Responsive Strategy

Use semantic HTML for structure and controls. Choose links for navigation and buttons for actions; provide accessible names, meaningful headings, landmarks, and labels. Use ARIA only when needed and ensure it matches actual behavior.

Verify keyboard reachability, visible focus, logical order, focus restoration, and escape from interactive regions. Custom composite widgets must follow appropriate interaction conventions. Do not remove focus cues or rely on pointer input alone.

Associate instructions and errors with form fields. Announce relevant status changes without overwhelming assistive technology. Manage focus for dialogs and route changes according to context; do not move focus unexpectedly during streaming or background refresh.

Check contrast, non-color cues, readable typography, zoom and reflow, touch targets, reduced-motion preferences, and content alternatives where relevant. Identify the applicable accessibility requirements rather than inventing a conformance claim.

Design responsive behavior around content and tasks, not a list of devices. Account for narrow and wide layouts, long or localized text, differing input methods, orientation, and browser text scaling. Avoid clipping essential actions, disabling zoom, or making hover the only path to information.

Verify relevant breakpoints and intermediate widths. Preserve reading and focus order when layout changes. Treat mobile performance and interaction as primary constraints where supported, not an afterthought.

## Component Architecture and Design Tokens

Compose components around coherent responsibilities and stable contracts. Keep domain orchestration separate from reusable presentation where it improves clarity. Extract shared components when reuse or behavioral consistency is demonstrated, not merely because markup looks similar.

Avoid deep prop drilling when it creates fragile coupling; do not replace clear local data flow with global state by habit. Prefer the least broad ownership mechanism that serves the consumers. Specify behavior for controlled and uncontrolled inputs when relevant.

Treat design tokens as maintained engineering contracts:

- Define spacing, typography, color, motion, elevation, radius, and other relevant primitives and semantic roles.
- Reuse established tokens; distinguish raw values from intent such as emphasis, danger, surface, or interaction state.
- Account for themes, contrast, reduced motion, responsive typography, and applicable user preferences.
- Avoid scattered one-off values that create visual and behavioral drift. Justify exceptions such as a content-specific measurement.
- Document ownership and propagate token changes through relevant components and states; a token change can have accessibility and layout consequences.

Reuse component libraries only after checking their fit, accessibility behavior, customization cost, dependency burden, and actual version capabilities. Library adoption is not proof of accessible composition.

## State Ownership, Routing, Rendering, and Caching

Distinguish local interaction state, shared application state, URL state, remote data, and durable user data. Assign each value an owner and lifetime. Derive values when possible rather than maintain synchronized copies.

Use URLs for relevant navigable or shareable state, without exposing sensitive information. Preserve history, deep linking, expected back behavior, and appropriate authorization checks. Frontend route guards improve experience but are not authoritative security controls.

Choose client, server, static, or mixed rendering from delivery and interaction needs. Specify server/client boundaries, browser-only capabilities, and data exposure. Never send secrets to the client because a module appears server-adjacent.

For hydration, ensure compatible initial markup and state; account for time, locale, randomness, browser storage, and asynchronous data. Diagnose mismatches rather than suppress warnings as the default fix. Verify that users can interact reliably during initial delivery and enhancement.

For each cache, define owner, key, scope, freshness, invalidation, mutation behavior, and access isolation. Prevent cross-user data reuse and stale data after identity changes. Distinguish refreshing existing data from first load. Do not cache sensitive content without a justified policy.

## Forms and Mutations

Use clear labels, instructions, appropriate input types, and intentional validation timing. Preserve entered data through recoverable failures. Distinguish formatting checks from business validation and authorization: client-side checks aid users but do not replace trusted-side enforcement.

Show field errors in context and an error summary when useful. Explain how to correct the problem without exposing sensitive internals. Avoid validation that disrupts typing or relies only on color. Keep error associations and focus behavior accessible.

Define pending states, repeat-submission handling, cancellation, and completion feedback. Do not disable unrelated actions unnecessarily or make pending work invisible.

Use optimistic updates only when the operation is sufficiently reversible and its outcome predictable. Record the pending mutation, reconcile authoritative results, and specify rollback or compensating behavior. Protect later user changes from being overwritten by rollback of an earlier operation.

Retry only when safe. A timeout may leave the mutation completed remotely; reconcile uncertain effects or use an established idempotency contract rather than resubmit blindly. Do not invent such a contract. Include authorization failures, conflicting edits, stale data, and validation errors in recovery design.

## Performance and Resilience

Establish relevant budgets and measure user-facing behavior under representative devices, networks, data volumes, and interaction sequences. Distinguish initial delivery, responsiveness, layout stability, and ongoing work. Do not present development-mode measurements as production guarantees.

Investigate unnecessary renders, costly computations, network waterfalls, excessive assets, and long tasks before optimizing. Memoization, virtualization, and caching introduce tradeoffs and need a demonstrated benefit.

Use code splitting and lazy loading at meaningful boundaries. Avoid deferring critical content or creating additional loading waterfalls; preserve predictable layout and accessible fallback states. Examine bundle composition and dependency cost rather than optimizing only source-file size.

Prefer progressive enhancement for core tasks when feasible. Define what still works without optional scripting or browser capabilities and what cannot. An application requiring scripting must still expose coherent loading and failure behavior.

Plan offline features only when user needs justify them. Define local persistence, privacy, freshness labels, retry queues, conflict handling, and synchronization status. Do not queue consequential actions silently or portray cached content as current. Evaluate storage and cache clearing after logout or permission changes.

## AI User Interface Patterns

Apply this section only when the interface exposes AI behavior. Coordinate contracts with the AI system rather than invent backend guarantees.

| Pattern | Required design |
| --- | --- |
| Streaming output | Distinguish partial content from completed output; handle interruption, malformed fragments, and incremental rendering. Avoid focus stealing and excessive announcements. Never render generated content as trusted executable markup. |
| Cancellation | Provide an accessible stop action and truthful status. Distinguish stopping generation, stopping display, and canceling tools; do not imply that completed side effects are undone. |
| Retry | Explain whether retry regenerates content or repeats actions. Preserve user input and prevent unintended duplicate tool effects. Make changed results distinguishable. |
| Citations | Attach references to the claims they support, with usable keyboard-accessible links. Do not fabricate citations or imply that a citation guarantees correctness. |
| Sources | Show relevant provenance, freshness, and source availability without revealing unauthorized data. Separate supporting evidence from model-generated explanation. |
| Confidence communication | Describe evidence limits, missing support, uncertainty, and verification needs. Do not invent percentages or treat model self-confidence as calibrated probability. |
| Tool execution progress | Distinguish proposed, awaiting approval, running, completed, failed, canceled, and uncertain outcomes. Avoid invented progress estimates and expose safe recovery options. |
| Human approval | Show the exact action, target, important arguments, consequences, and scope. Offer clear approve and deny paths; changed operations require renewed review. Enforcement belongs outside the UI and model. |

Respect user control and preserve the distinction between a suggestion, an approved action, and an executed result. Sanitize or safely render untrusted content and validate navigation destinations where necessary. Apply [SEC-01](../../ENGINEERING_MANIFESTO.md#sec-01), [SEC-02](../../ENGINEERING_MANIFESTO.md#sec-02), and [VAL-02](../../ENGINEERING_MANIFESTO.md#val-02).

## Testing, Maintainability, and Handoff

Choose verification according to consequences using [VAL-01](../../ENGINEERING_MANIFESTO.md#val-01). Test user-observable behavior and important state transitions rather than component internals alone.

Use appropriate layers: pure logic checks, component interactions, integration tests, and end-to-end critical tasks. Exercise loading, empty, errors, unauthorized access, races, failed mutations, and interrupted work as applicable. Validate responsive behavior with realistic content, not only a single screenshot.

Combine automated accessibility checks with keyboard and appropriate assistive-technology review. Report which environments and interaction paths were actually exercised. Visual checks can detect layout changes but cannot establish semantics or usable recovery.

Review understandable naming, cohesive composition, explicit state ownership, token consistency, dependency cost, and compatibility. Document non-obvious behavior, component contracts, intentional exceptions, and operational limits under [DOC-01](../../ENGINEERING_MANIFESTO.md#doc-01). Avoid comments that merely repeat the code.

Report implemented scope, verification evidence, unperformed checks, and known limits. Separate proposed behavior, observed behavior, and supported environments; do not claim universal browser or accessibility compatibility from limited evidence.

## Escalation and Quality Gates

Stop dependent work and ask a focused question when unknown business behavior, missing API contracts, conflicting accessibility requirements, sensitive-data exposure, or consequential approval rules would materially change the implementation. Explain the blocker and minimum decision needed. Continue independent authorized work where useful.

Before declaring the requested scope complete, verify:

- User tasks, requirements, and acceptance conditions are understood.
- Semantic structure, accessible names, keyboard behavior, focus, and relevant accessibility requirements are checked.
- Responsive behavior supports relevant content, input methods, zoom, and environments.
- Idle, loading, success, empty, error, unauthorized, and offline states are handled or explicitly inapplicable.
- Forms cover validation, pending work, applicable optimistic behavior, safe retry, rollback, and recovery.
- Components, state ownership, rendering, routing, and caching have justified boundaries.
- Tokens and interaction patterns remain consistent, including themes and motion preferences where relevant.
- Performance decisions have evidence appropriate to their scope; failures and interruptions remain usable.
- Applicable AI interactions preserve provenance, uncertainty, user control, and truthful action status.
- Verification and maintainability review are complete within stated limits; unresolved failures are not hidden behind a completion claim.

## Anti-patterns

Do not substitute generic containers for meaningful semantics, create unexplained deep prop drilling, add global state by default, or optimize re-renders without identifying a real cost.

Do not prioritize visual polish over keyboard use, accessibility, mobile behavior, failure states, or preserved user work. Avoid inaccessible custom controls, contradictory state flags, accidental data duplication, and client-only authorization assumptions.

Do not introduce abstractions for hypothetical reuse, replace conventions for novelty, or optimize before establishing a bottleneck or budget. Do not mistake a library's claims, a screenshot, or a passing scan for verified quality.

## Coordination With Existing Skills

[project-planner](../project-planner/SKILL.md) owns substantial scope, architecture planning, milestones, readiness, and approval. Contribute frontend decisions and acceptance criteria to its plan without competing records or bypassing approval.

[mentor-mode](../mentor-mode/SKILL.md) explains choices at the user's preferred depth. Explanations do not replace testing or accessibility validation.

[ai-engineer](../ai-engineer/SKILL.md) owns model behavior, evaluation, tool controls, and AI operational contracts. Frontend Master owns their interface consequences and must not invent confidence, cancellation, citation, or approval guarantees.

Preserve scope and decision ownership under [PRO-01](../../ENGINEERING_MANIFESTO.md#pro-01). These references do not require activating every skill for every UI task.

## Behavioral Examples

These are instructional scenarios, not executed validation results.

### Search Results

Distinguish idle, initial loading, no matches, usable cached results during refresh, and failed refresh. Keep filters shareable where appropriate, prevent old responses replacing newer searches, and expose understandable keyboard-accessible recovery.

### Editable Form

Preserve input when a save fails. If optimistic behavior is justified, reconcile the result and avoid rolling back edits made after submission. A timeout does not prove the save failed; use the actual mutation contract before retrying.

### Responsive Navigation

Reuse established tokens and navigation patterns. Verify narrow layouts, zoom, focus order, menu dismissal, and long labels. A visually compact navigation is not acceptable if essential destinations become unreachable.

### AI Assistant With Tools

Display partial output separately from completed results, preserve accessible reading, and show real tool status. Approval identifies the precise operation; stop and retry controls must not imply reversal or safely repeat side effects without corresponding system guarantees.
