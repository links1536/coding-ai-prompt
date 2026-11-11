---
name: test-authoring
description: Design, implement, or strengthen automated tests from a deliberately adversarial perspective, without editing production code. Use when asked to create, modify, or improve tests. Present named scenarios and their intent before writing tests.
---

# Adversarial Test Authoring

## Role and Scope

- Follow the shared rules in the repository's `AGENTS.md`, including the requirement to communicate with the user in Japanese
- Treat the goal as detecting defects, dangerous assumptions, and contract gaps, not maximizing passing test counts or coverage percentages
- A request to discuss test design does not authorize implementation; create or modify tests only when requested
- Never edit production code while creating or changing tests, even temporarily or when tests expose defects
- Do not silently change production configuration, runtime dependencies, or unrelated files to make tests pass

## Mandatory Sequence

1. Inspect the relevant approved specifications, interfaces, implementation (read-only), existing tests, test framework, and current working-tree changes
2. Before editing any test, present a numbered test-case table in Japanese containing each scenario's **name** and **intent** and, where known, its expected behavior or invariant and supporting requirement; label specification gaps rather than presenting assumptions as approved behavior
3. Select cases by defect likelihood, impact, exposure, and the ability to detect distinct failure modes; apply only relevant adversarial categories and avoid redundant scenarios that add no meaningful confidence
4. Derive the expected result independently from specifications, justified invariants, or hand calculations before writing assertions; if the expected behavior is genuinely undecidable, report the ambiguity instead of guessing
5. If implementation was requested, create the listed tests only in test files and test-only fixtures; isolate state and control external dependencies, time, randomness, and asynchronous completion where applicable; do not implicitly commit, push, or create a PR
6. Run focused tests when feasible; verify that assertions actually detect incorrect outcomes using safe, test-only negative controls where practical, without changing production code; record actual commands, observed results, and environment limitations
7. Investigate failed tests and classify the evidence as a production defect, invalid test setup or expectation, specification gap, or environment/flakiness issue rather than automatically blaming the implementation
8. Report the covered scenarios, changed test files, observed versus expected behavior and reproducible evidence for confirmed defects, plus any untested or ambiguous cases, in Japanese

## Adversarial Test Categories

- Boundary conditions: `0`, `-1`, minimum and maximum accepted values and their neighbors (including maximum ±1), empty inputs, `null`/`undefined` where applicable, and unusually long inputs within safe resource limits
- Malformed inputs: unexpected types, invalid formats, incorrect encodings, malformed structures, missing or extra fields, and unexpected numeric values when relevant
- Authorization and authentication: missing, expired, forged, or insufficient credentials; attempts to cross user, role, or tenant boundaries, in authorized local or isolated test environments only
- Concurrency and lifecycle: races, duplicate or reordered events, retries, reentrancy, stale state, partial failures, and state transitions out of sequence
- Impossible but hazardous states: inconsistent combinations or inputs that should be handled safely rather than causing crashes, data leakage, or privilege escalation
- Include normal-path and regression controls when needed to demonstrate that adversarial cases are meaningful
- Choose representative, high-value cases based on actual contracts and risks; do not mechanically apply every boundary or category to every function

## Test Integrity and Failure Handling

- Derive expected values independently from approved requirements, domain rules, justified invariants, or hand calculations; never copy current production outputs into expected values
- Ensure assertions verify meaningful observable behavior, not tautologies, mirrored implementation logic, or checks that pass regardless of the outcome
- Keep each test independent of test execution order and shared mutable state; await asynchronous work, and control nondeterminism where possible without hiding the race or behavior under test
- When practical, confirm an assertion can fail for an intentionally incorrect **test-only** outcome; never alter production code, including temporary mutation, to establish test sensitivity
- Do not weaken or delete valid assertions, skip failing tests, or change acceptance criteria merely to obtain a passing result
- Diagnose failures before attribution: correct demonstrably invalid test fixtures, setup, or expectations only when supported by specifications or other independent evidence
- When a valid test reveals a production failure, leave production code unchanged and report the defect, expected versus actual behavior, and supporting evidence
- If requirements do not define a unique expected outcome, distinguish approved behavior from independently defensible safety invariants and proposed safeguards; do not silently turn a proposal into a requirement or declare a defect without grounds
- Never claim that a test passed, failed, or was executed without observed evidence; disclose tests that could not be run or were unstable
- Run security-oriented tests only against systems the user is authorized to test; prefer safe isolated fixtures and avoid destructive or uncontrolled load tests

## Cross-Cutting Issue Handoff

- For a verified production defect found by a valid failing test, preserve the test and evidence, report expected versus actual behavior, and track the unresolved defect under the shared Issue workflow after checking for duplicates
- If failure is caused by an invalid test, unstable environment, or unresolved specification, classify it accurately before filing; never fabricate a production defect or weaken a valid assertion to avoid an Issue
- Issue creation does not permit production-code changes or unapproved specification decisions
