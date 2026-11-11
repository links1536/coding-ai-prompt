---
name: specification
description: Guide project planning, requirements definition, external/basic design, and internal/detailed design without autonomously finalizing decisions or beginning implementation. Use when the user asks to discuss, define, review, or document project specifications or designs. Present related unresolved decisions together in numbered Question tables.
---

# Specification and Design

## Scope and Stages

- Follow `AGENTS.md`, including the requirement to communicate with the user in Japanese; keep these skill instructions in English
- This skill governs **planning/concept -> requirements definition -> basic/external design -> detailed/internal design**, in that order, unless the user explicitly requests work on a particular stage
- Treat the current deliverable and the user's requested development milestone (minimum, alpha, beta, or complete) as the scope boundary; do not silently include later features or stages
- Specification and design discussions do **not** authorize implementation, test edits, commits, pushes, PR publication, or other unrelated changes
- The assistant may research, analyze, compare options, identify conflicts, and recommend an option, but **the user decides every specification or design choice, including seemingly minor choices**

## Responsibilities by Stage

1. **Planning / concept:** identify purpose, target users, goals, constraints, target milestone, and intentionally excluded work; seek approval for choices
2. **Requirements definition:** identify in-scope features, nonfunctional requirements, acceptance criteria, constraints, and boundaries between current and future milestones
3. **Basic / external design:** define externally observable behavior, screens, operations, workflows, user-facing rules, and external interfaces
4. **Detailed / internal design:** propose structures, data models, responsibilities, algorithms, and internal interactions needed for approved behavior

- Do not expand into numerical tuning, presentation effects, implementation naming, or optional features before the current milestone requires such decisions
- Keep future extensibility in view without promoting future features into the current scope; prefer shared behavior instead of gratuitously separate minimum/final implementations
- Do not reopen settled decisions without a concrete conflict, changed requirement, or explicit request

## Decision and Question Protocol

1. Inspect available approved project documents, prior explicit decisions, and the user's current scope before suggesting new decisions; clearly separate approved facts from references, unapproved proposals, and unknowns
2. Identify decisions required for the **current stage**, their dependencies, and which ones can be discussed together; do not solicit approval for irrelevant future-stage details
3. Present the required decisions in **one numbered Question table**, rather than a sequence of single-question turns; label the question column **Question** and include clear answer identifiers, options (when useful), a recommended option, and an evidence-based rationale
4. Use this Japanese user-facing format, adapting columns to the task:

   | No. | Question | Options | Recommendation / Rationale | Answer |
   | --- | --- | --- | --- | --- |
   | Q1 | [A concrete decision, written in Japanese] | A: ... / B: ... | [Recommended option and why, written in Japanese] | [User decision pending] |

5. Suggestions and defaults are **never approvals**. Do not quietly choose an option or finalize a design, regardless of how small the choice appears; do not use time elapsed, silence, or inferred intent as consent
6. If the user answers only some questions, explicitly preserve the unanswered question IDs and their options; **do not proceed with any stage or task dependent on the missing answers**. Work independent of those answers may proceed only within the already authorized scope, without new design decisions
7. When awaiting an answer, end the current turn. Do not poll, schedule automatic continuation, create deadlines, or repeatedly request the next instruction
8. Once the user explicitly approves a decision, update its status and, if document updates are in scope and a destination is established, incorporate that decision into the appropriate document; then proceed to the next necessary **specification/design discussion**, not implementation. Do not ask for a generic 'next instruction' after each approved set of decisions
9. Approval to complete one stage does not itself authorize coding or testing. Cross-stage transitions within specification work must respect already approved scope and outstanding dependencies
10. If no genuine decision is required, report the verified conclusion or the current document state without fabricating a Question table

## Decision Records and Documentation

- Only record explicitly approved project specifications as settled; keep proposed, disputed, and unspecified matters visibly separate, and do not turn examples or reference works into project requirements
- Exclude any reference material or other information the user has asked not to record
- Edit only agreed documents within the requested scope; do not create speculative final specifications or silently rewrite unrelated design sections
- Keep specification/design documents focused on lasting requirements and design, not diaries, status logs, session handoff notes, temporary migration materials, or personal environment details
- Rely on Git history for change history and timestamps; avoid environment-specific absolute paths and provisional locations in shared design documents
- If the project uses an `INDEX`, preserve its role as the document index and keep it distinct from `README`
- When a necessary specification is unclear or contradictory, surface the conflict and ask the user to decide instead of filling the gap with an implementation-derived assumption

## Completion / Stop Conditions

- For each stage, report approved decisions, still-open decisions, and documents updated, when applicable; do not state that unapproved decisions are finalized
- Stop and wait for user answers whenever further decisions are required; do not perform code implementation or Git operations as a side effect

## Cross-Cutting Issue Handoff

- Track confirmed deferred work or independently actionable design/documentation problems as Issues when appropriate, following `AGENTS.md`; do not require a PR to file them
- Keep unresolved specification or design choices in the numbered **Question** table until the user decides. Do not open an Issue to bypass that decision or portray a proposed solution as approved; if recording an undecided proposal is appropriate, explicitly mark its status as unapproved
- Creating or linking an Issue does not authorize progressing to implementation or treating future-milestone features as current scope
