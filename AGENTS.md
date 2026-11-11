# Shared Agent Rules

- Always communicate with the user in Japanese, regardless of the input language
- Write all generated user-facing content in Japanese unless the user explicitly requests another language
- Keep technical identifiers, code references, commands, paths, and URLs in their original form
- Distinguish verified facts from assumptions, inferences, and unverified information; never invent evidence
- Evaluate the user's stated rationale against the actual changes rather than accepting it uncritically
- Do not confuse reference material with approved project specifications or intended changes with unrelated modifications
- Stay within the requested scope; do not introduce unrelated bug fixes, refactors, or design changes
- Do not interpret specification or design discussions as authorization to implement code, commit, push, or publish a Pull Request
- For project planning, requirements, or design discussions and documents, follow `.agents/skills/specification/SKILL.md`
- For explicitly requested production-code creation or changes, follow `.agents/skills/implementation/SKILL.md`
- For test creation or modification, follow `.agents/skills/test-authoring/SKILL.md`
- For commit tasks, follow `.agents/skills/git-commit/SKILL.md`
- For Pull Request descriptions or creation, follow `.agents/skills/github-pr/SKILL.md`
- Treat specification decisions, implementation, test authoring, committing, and publishing a Pull Request as distinct actions; do not infer authorization for one from a request for another
- Do not independently finalize specification or design choices, regardless of their apparent size or importance; distinguish proposals from user-approved decisions
- When a task requires user decisions, group related questions in a numbered Question table, preserve unanswered items, and stop the current turn while awaiting answers; never treat elapsed time as approval

## Cross-Cutting GitHub Issue Tracking

- Treat Issues as records for verified defects, actionable improvements, and deferred work **across** specification, implementation, testing, and PR work. Issue tracking is not a development phase, a mandatory PR subtask, or a substitute for specification approval
- At relevant checkpoints, identify concrete issues arising from the work. Do not create Issues simply to increase issue counts or perform unrelated speculative audits
- When an actionable finding is outside the authorized current change, search the target repository's open and closed Issues for duplicates before filing. Create at most one Issue per distinct actionable finding; use an existing Issue instead of duplicating it
- Do not file a separate Issue for work already fully handled by the current authorized change or PR unless separate future tracking is genuinely necessary. An Issue may exist without a PR, and a PR does not require a newly created Issue
- An Issue proposal is **not** approval of a new requirement, design choice, implementation, or priority. Record any undecided behavior as a question or explicitly unapproved proposal; never change approved specifications as a side effect
- Issue creation is generally preauthorized when the repository and the designated GitHub App are known and access is available; do not ask for approval for every qualifying new Issue. If those prerequisites are not met, report a draft and the blocker rather than inventing credentials or an identity
- Before creating an Issue, confirm its actionable problem and supporting evidence. Use the fixed Issue format below, and never invent reproduction steps, verified impacts, or links
## Issue Description Format

- Write the Issue title and body in Japanese, keeping the English section headings below unchanged; preserve identifiers and URLs in their original form
- Keep the title short and specific to one actionable defect or improvement. Avoid vague titles, exaggerated impact, and assumed root causes
- Keep the body as concise as a PR description: one sentence per prose section when practical, and at most two checklist items under `Acceptance Criteria`. Include only essential verified evidence and needed context; do not sacrifice accurate reproduction or meaningful completion criteria merely to shorten it
- Distinguish observed facts from unverified hypotheses. Present `Proposal` as a suggestion, not an approved requirement or implementation instruction
- Use `.github/ISSUE_TEMPLATE/issue.md` as the canonical GitHub Issue body template, removing YAML frontmatter and instructional HTML comments when constructing the API body. Set the concise Japanese Issue title in GitHub's title field, not in the Issue body
- Use the exact Markdown structure below. Omit the entire optional `Related PR` section if no related PR has been verified. Do not add filler sections

```markdown
## Context
(One concise sentence explaining the relevant situation)

## Problem
(One or two concise sentences describing the verified problem or actionable opportunity and evidence; label uncertainty explicitly)

## Proposal
(One concise sentence describing a proposed next step, not an approved decision)

## Acceptance Criteria
- [ ] (One verifiable completion condition)
- [ ] (A second condition, only if necessary)

## Related PR
- (Verified PR reference only; omit this entire section if none exists)
```

## Issue Label Rules

- Use `bug` for confirmed defects. Generally use `enhancement` for improvements to features, performance, maintainability, or other non-defect work. Do not misclassify an unverified suspicion as a confirmed bug
- Preserve project-specific label rules when they exist. When setting up or applying the standard priority labels, use the exact labels and criteria below rather than guessing from the label names

| Label | Decision criteria |
| --- | --- |
| `priority: critical` | The software cannot operate, or there is a serious security vulnerability or similarly critical impact |
| `priority: high` | A major defect or a substantial negative impact on user experience |
| `priority: medium` | Ordinary improvements or routine work |
| `priority: low` | Low-impact, experimental, or long-term improvements |
| `priority: unassessed` | The Issue's priority has not yet been evaluated |

- Assign a priority only when evidence supports the classification; if a priority label is needed but cannot yet be justified, use `priority: unassessed`
- Apply labels that exist in the target repository. Do not silently create or change repository labels; perform label-management operations only when authorized and through the designated GitHub App

- Leave adoption, deferral, and closure decisions to the user. Never close an Issue or infer approval of its proposal without an explicit instruction
- Reading/listing Issues and PRs and checking their status need no individual confirmation; use the designated GitHub App for Issue and label creation/editing/comments/closure, and the existing user authentication for PR and Git operations. Do not silently substitute identities
- Before changing multiple existing Issues or labels in bulk, present a Japanese table of targets, before/after values, and reasons, and obtain authorization. After approval, batch the edits where practical; on partial failure, re-read all affected items, apply only pending changes, and verify the final state
- Never expose GitHub App private keys, JWTs, installation tokens, or other secrets in the repository, logs, or user-facing output
- If no actionable new finding is confirmed, do not create an Issue. When reporting Issue activity, distinguish created, linked/existing, proposed-only, and none; do not claim publication without verified results
