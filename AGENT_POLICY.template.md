# Repository policy

## Bootstrap

Run this section when the user explicitly adopts this template as a repository's agent policy, or when it is already installed as that policy and this section remains. Reading, reviewing, or editing a template copy does not activate it. If the current request is unrelated, offer setup once and proceed with the request if the user defers.

### Environment and configuration

Before asking questions or making changes, inspect the repository and relevant environment: existing policy files and their symlinks or imports, resolved settings from earlier installations, directory layout, Git ignore rules, documentation language, and test and build configuration. Keep discovery read-only and limited to information needed for setup.

Resolve `<SCRATCH_DIR>`, `<DOCS_DIR>`, `<TESTS_DIR>`, and `<DOCUMENTATION_LANGUAGE>`, along with the policy destination and layout. Directory values must be repository-relative paths suited to the existing structure. Keep the scratch directory separate from maintained project content. Selecting paths does not authorize relocating existing files or imposing a new project layout.

Use the user's explicit choices for this installation first; otherwise retain resolved values from the installed copy or an unambiguous predecessor, even if its setup section is gone. For remaining choices, derive preselected options from the environment. Briefly state their basis and uncertainty; where evidence is insufficient, offer a clearly labeled suggestion or leave the choice open. Treat detected and suggested values as proposals until the user accepts them.

Present the proposed setup using the environment's user-question tool or equivalent, in as few interactions as it allows, and ask the user to accept the preselected options or change specific values. Include all currently unresolved settings, path or layout choices, and required approvals. Show explicit and inherited values for reference without asking for reconfirmation. Ask only when a choice or approval remains outstanding; do not change destination files before it is resolved.

### Installation and upgrade

Keep one canonical policy body. Use the user's chosen destination and layout; otherwise preserve an unambiguous existing arrangement. For dual-file use of `AGENTS.md` and `CLAUDE.md`, resolve the canonical file and reference method during setup. Recommend `AGENTS.md` as canonical, referenced from `CLAUDE.md` and `CLAUDE.local.md` rather than symlinked, unless the user knows how every tool they use loads these files. Preserve existing symlinks or imports unless a layout change is requested; use relative targets for new symlinks.

Replacing a predecessor or a conflicting file or link requires explicit overwrite approval unless already given. Adopting this template alone does not grant it. Identify any project-specific rules that replacement would remove and include their disposition in setup; carry them over only when explicitly authorized.

Apply the template with the resolved values, ensure the repository's `.gitignore` ignores the scratch directory without hiding maintained project content, and verify the installed policy and its file references. Do not create documentation or test directories merely because they are configured. After success, remove this entire Bootstrap section, including its subsections, from the installed copy. Check that no configuration placeholders or bootstrap text remain, then tell the user to start a new agent session immediately to load the updated policy and confirm it loaded.

Only the installation and upgrade edits specified here are pre-authorized exceptions to the policy's modification restriction, subject to the overwrite approvals above.

## Scope

This file is repository-wide agent configuration, not project documentation. Keep it short, general, and limited to durable rules that apply across tasks and developers.

Do not encode task-specific instructions, temporary decisions, personal preferences, or machine-specific details here or in other documentation tracked in Git. Do not promote a task's instructions or preferences into standing project rules without explicit user authorization.

## Precedence

Explicit user instructions and established project requirements, such as CI checks and contribution guidelines, take precedence over this policy, though changing this policy still requires an explicit request. On every conflict, follow them, then tell the user which rule was overridden and ask them to resolve the conflict in the environment or this policy.

## Change scope

Keep changes within the task: do not refactor, reformat, rename, or upgrade dependencies outside it unless the user asks. Mention notable unrelated issues instead of fixing them. The test cleanup under Tests is in scope.

## Repository hygiene

Project changes intended for Git must be commit-ready: complete, maintainable, validated, and free of temporary or machine-specific content, secrets, and credentials.

Use Git-ignored `<SCRATCH_DIR>` for scratch work, drafts, experiments, debugging artifacts, one-off validation, and other non-commit work. When unsure whether an artifact belongs in project history, put it there.

Production code, maintained tests, durable documentation, and build workflows must never depend on `<SCRATCH_DIR>`.

## Documentation

Documentation language: **<DOCUMENTATION_LANGUAGE>**. This setting applies only to project documentation, not this policy, source code, identifiers, comments, docstrings, commit messages, logs, or other implementation text.

Use terminology and phrasing natural to developers working in the specified language. Write concise, factual, technically precise documentation that is clear to both human developers and agents. Preserve necessary context; include only detail that helps readers understand, use, or maintain the project.

Keep durable system documentation in `<DOCS_DIR>` and written task briefs, implementation plans, and work logs in `<SCRATCH_DIR>`. Read the relevant documentation before changing an area. Document the current system, not the request that caused a change. Remove or update obsolete content; retain history or explanations of removed or rejected work only when needed to understand the current system.

If `README.md` exists, prioritize first-time understanding and getting started. Do not use it as the default destination for documentation changes or as a task record. Keep detailed developer documentation in `<DOCS_DIR>`; when `<DOCS_DIR>` exists, link to it from a dedicated README section.

Review documentation for impact. Update it when a change makes it inaccurate, exposes missing information necessary for understanding, use, or maintenance, or changes what readers need to know. Leave accurate and sufficient documentation unchanged; restoring already-documented behavior does not by itself require a documentation edit. Make necessary documentation changes with the implementation, in the same commit when committing.

## Local preferences

Put personal preferences, collaboration relationships, and machine-specific settings in ignored, tool-supported local configuration such as `CLAUDE.local.md` referencing `AGENTS.md`, not here.

## Tests

Keep the maintained suite lean and focused on meaningful behavior and established contracts. Reuse or extend suitable existing tests and fixtures; add tests only to close a concrete gap in regression protection. Do not add tests solely because code changed, tests for inputs or states outside the code's contract, or assertions that merely reproduce the implementation.

As part of changes to an affected area, proactively simplify its tests and fixtures: consolidate overlapping cases and remove obsolete, redundant, or low-value tests that provide no distinct regression protection. Preserve meaningful coverage, distinct failure modes, and tests guarding past defects. Do not sweep unrelated suites or remove, weaken, or skip tests to conceal defects or unresolved failures.

Use `<TESTS_DIR>` for maintained tests, respecting existing colocated or framework-required layouts. Maintained tests must be stable, repeatable, maintainable, and provide lasting regression value. Keep one-off tests and reproductions in `<SCRATCH_DIR>`; promote them into the maintained suite only when they meet these standards and fill a concrete coverage gap.

## Completion standard

Before finishing, ensure this task's project changes meet the requirements above.

Run required checks: those mandated by applicable instructions or project requirements, plus the targeted validation necessary to verify affected behavior and address concrete risks. Identify project requirements from existing configuration, CI, and contribution guidance. Honor explicitly mandated scope; keep risk-based checks focused on the change, but run the broader suite when it is fast or the change has wide reach.

Reuse still-valid results. Once required checks pass and the affected behavior is adequately verified, stop validation. Repeat or expand it only for a relevant failure, a concrete uncovered risk, or a change that invalidates earlier results. Report unresolved failures, required checks that could not be completed, removed tests, and scratch artifacts worth keeping.

## Policy changes

Do not modify or translate this file unless the user explicitly requests changes to this policy. Documentation language settings and project-wide editing or translation requests do not grant that authorization.

Extend this policy only with durable repository-wide rules that materially improve future work; prefer revising or removing redundant rules over accumulating instructions.
