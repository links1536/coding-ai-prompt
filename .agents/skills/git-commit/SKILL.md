---
name: git-commit
description: Review Git changes and create focused, dependency-ordered commits. Use when the user requests committing changes, splitting commits, staging, or drafting commit messages. Do not use for PR-description-only tasks or design discussions.
---

# Git Commit

## Core Principles

- Follow the shared rules in the repository's `AGENTS.md`, including its Japanese-language response requirement
- Do not create commits unless the user requests a commit
- When asked to preserve or integrate existing code, do not silently add bug fixes, refactors, or design changes
- Do not indiscriminately combine changes with different responsibilities, such as production code and tests, UI and game logic, or status handling and damage calculation
- Check dependencies and determine a logical order before committing
- Use the user's exact commit message when specified; otherwise follow the conventions observed in the existing Git history
- Do not accidentally stage unrelated changes, secrets, or generated artifacts; preserve all existing user changes
- Distinguish independently reviewable changes without splitting commits merely for the sake of producing more commits

## Procedure

1. Inspect `git status --short`, the relevant `git diff` and `git diff --cached`, and, when helpful, `git log -5 --oneline`
2. Identify the requested scope and distinguish relevant edits from unrelated or already-staged changes
3. Group changes by responsibility, taking dependency constraints and ordering into account
4. Stage only the intended files or hunks; avoid indiscriminate `git add -A`
5. Before each commit, inspect `git diff --cached --check` and `git diff --cached` again
6. Commit with the explicitly supplied message or one consistent with existing history; preserve dependency order across multiple commits
7. Verify `git status --short` and the newly created commits using `git log`; report commit IDs, contents, and any remaining uncommitted changes concisely in Japanese

## Restrictions

- If the scope or ownership of a change is unclear and it cannot be safely isolated, do not include it without authorization
- Claim that tests ran only when their execution and results are verified
- Do not amend, rebase, reset, force-push, push, or open a Pull Request unless specifically requested
- If a fix outside the requested scope appears necessary, report it instead of implementing it without authorization
