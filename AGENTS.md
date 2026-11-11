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
