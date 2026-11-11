---
name: implementation
description: Implement explicitly authorized production-code changes according to user-approved requirements and designs while respecting scope and unresolved decisions. Use when the user requests actual coding or code modification, not when merely discussing specifications, tests, or Git operations.
---

# Implementation

## Preconditions and Authority

- Follow `AGENTS.md`, including its Japanese-language response requirement
- Begin writing or modifying production code only when the user has explicitly requested implementation
- Read the relevant approved requirements and design documents, existing behavior, tests (read-only unless separately authorized), and current working-tree state before changing files
- Do not treat design review, a question, a suggested solution, or approval of a specification as implicit permission to start coding
- The user retains authority over **all new specification and design choices**, even if they seem minor; do not silently decide unresolved behavior or architecture

## Implementation Procedure

1. Define the exact authorized files, features, and behaviors from the user's request and approved project documents
2. Identify missing or conflicting requirements or design decisions that affect the implementation; propose options with reasons, using a numbered **Question** table in Japanese as specified by `specification/SKILL.md`; stop work dependent on the unanswered decisions and end the turn if answers are required
3. Implement only what is already authorized and determined; preserve existing conventions without using them as a substitute for user approval on newly required design choices
4. Keep unrelated bug fixes, refactors, dependency changes, new features, and design changes out of scope; report needed out-of-scope fixes instead of silently adding them
5. Inspect the diff for unintended edits and verify implementation against the approved behaviors; run relevant existing checks when feasible without creating or modifying tests unless separately asked
6. Report changed files, verification actually performed, remaining uncertainties, and any blocked or deferred work in Japanese; never invent test results or claim work was completed when it was not

## Separation of Work

- Production-code implementation and test authoring are separate tasks; use `test-authoring/SKILL.md` for new or changed tests only when explicitly requested
- Do not automatically commit, push, create branches, or publish a Pull Request; use the appropriate Git skills only upon an explicit request
- A test failure or discovered defect does not authorize unrelated fixes or changes to approved requirements
- Do not use speculative behavior as a default, and do not treat elapsed time or unanswered questions as approval

## Cross-Cutting Issue Handoff

- Report independently actionable defects, risks, or improvements uncovered outside the authorized implementation scope; use the shared Issue workflow to track verified deferred work without inserting unrelated changes into the current patch
- Do not create redundant Issues for a problem already completely addressed in the current change. A finding that warrants an Issue does not authorize its implementation, a new design decision, or PR publication
