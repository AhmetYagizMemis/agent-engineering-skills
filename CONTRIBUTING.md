# Contributing

Contributions to Agent Engineering Skills should improve engineering decisions, reduce mistakes, and keep this project maintainable. Read the [project principles](README.md#core-engineering-principles) before proposing a change. Favor sustainable scope over short-term completeness.

The repository is currently in its foundation phase. No skills are implemented. Skill proposals are welcome; implementation should follow agreement on scope and validation.

## How to Contribute

1. Check existing issues and pull requests for related work once the GitHub repository is available.
2. Describe the problem and the change you propose. For a new skill, include its purpose, activation conditions, scope, expected outcomes, and validation approach.
3. Discuss substantial additions or behavior changes with maintainers before implementation.
4. Make a focused change with the necessary documentation and verification.
5. Submit a pull request with enough context for a reviewer to assess the result.

Documentation corrections and small, focused fixes can be submitted directly. Avoid including unrelated cleanup in the same change.

Do not publish credentials, private project material, personal data, or confidential evaluation inputs. Report security concerns privately through a maintainer-designated channel when one is available; public reports should omit sensitive details.

## Coding Standards

When supporting code is needed:

- Follow the language's established conventions and repository tooling.
- Prefer readable names, small cohesive units, explicit dependencies, and straightforward control flow.
- Add abstractions only when they solve a demonstrated problem.
- Handle expected errors and describe relevant environment assumptions.
- Use safe defaults, least privilege, and appropriate input validation.
- Keep dependencies justified and reproducible; document setup and supported versions.
- Verify changed behavior and relevant failure paths with proportionate tests.
- Consider performance requirements early and use measurements to justify optimization.
- Include accessibility in frontend behavior and verification.

The foundation does not prescribe a language, formatter, or test runner. Future code contributions should establish appropriate tooling within their scope.

## Documentation Standards

- Use concise technical English and consistent Markdown formatting.
- Explain prerequisites, decisions, expected outcomes, and limitations.
- Distinguish planned behavior from implemented and verified behavior.
- Keep links, commands, paths, and terminology accurate.
- Use real, reproducible examples with sensitive information removed.
- Avoid invented results, unsupported compatibility claims, and marketing language.
- Update related documentation and the changelog when behavior or scope changes.

## Skill Writing Standards

Every new skill must include:

| Component | Required content |
| --- | --- |
| Purpose | The engineering problem, intended benefit, and scope boundaries |
| Activation conditions | When to use the skill, required context, and when another workflow is more appropriate |
| Workflow | Actionable steps, decision points, prerequisites, outputs, and verification |
| Engineering rationale | Why the workflow makes these choices and which tradeoffs depend on project context |
| Examples | Realistic, validated applications with enough context to reproduce or assess them |
| Anti-patterns | Common mistakes, their consequences, and how to avoid them |
| Quality checklist | Observable criteria for assessing completion and result quality |

A skill should encode decision-making rather than merely request an output. It should inspect project context before prescribing changes and explain how to handle missing information or conflicting constraints.

Document required tools, permissions, dependencies, and compatibility evidence. Instructions must respect user authorization and repository rules, protect sensitive data, and identify consequential actions that require human involvement.

Keep scope bounded. Reuse shared guidance where practical, but avoid dependencies that make a skill difficult to understand or use independently. Final packaging conventions will be established when the first skills are designed.

### Organization and Compatibility

Place each future skill directly under `skills/` using a globally unique, stable, lowercase hyphenated identifier. Categories will belong in a future discovery catalog, not in directory paths. A skill may have several categories; adding categories must not require moving skills.

Keep entry instructions focused and load supporting material only when needed. Document dependencies between skills explicitly. Changes to identifiers or behavior require migration guidance when users are affected.

The [Skill Execution Pipeline](README.md#skill-execution-pipeline) is conceptual. Explain which responsibilities a skill addresses without requiring every task to execute every stage.

The empty `templates/skill-template/` directory is reserved for later design. Do not add placeholder content or treat it as an available authoring template.

## Validation Expectations

Validate a skill against realistic tasks, including ambiguous inputs and relevant failure cases. Record which agent, version, environment, and workflow were exercised. Explain expected outcomes and observed limitations.

Validation should show whether the skill reduces engineering mistakes, not just whether an agent produces output. Assess correctness, maintainability, security, developer experience, and other principles relevant to the task.

For documentation-only changes, check accuracy, formatting, and links. Do not introduce artificial tests that simply repeat the instructions.

## Pull Request Process

1. Create a branch for one coherent change.
2. Explain the problem, resulting behavior, scope, and engineering rationale in the pull request description.
3. Include validation evidence and known limitations. List tool compatibility only when exercised.
4. Update the README, supporting documentation, and `CHANGELOG.md` as appropriate.
5. Review your diff for unrelated edits, secret exposure, unclear instructions, and unsupported claims.
6. Address reviewer feedback and repeat relevant checks when changes affect prior validation.
7. Maintainers review the contribution before merging.

Do not invent a release number or declare planned features complete. Record notable changes under `Unreleased`; maintainers will organize release entries when publishing.

## Review Checklist

- The problem and scope are clear.
- Instructions are actionable and their rationale is explained.
- The change follows the project's engineering principles.
- Examples and compatibility claims have supporting evidence.
- Relevant risks, failure cases, and limitations are documented.
- Verification matches the change and demonstrates meaningful outcomes.
- Scope, identifiers, and dependencies support long-term maintenance.
- Documentation and changelog entries reflect the final contribution.

## License

Contributions are submitted under the repository's [MIT license](LICENSE). Submit only material you have the right to contribute, and retain required attribution for third-party material.
