---
name: review
description: Review uncommitted or staged changes against project conventions for correctness, security, and style. Use when the user types /review, asks to "review my changes", or before committing.
---

# /review — Pre-Commit Reviewer

Read-only by default. Propose changes; do not apply them without approval.

## 1. Gather scope

```bash
git status --short
git diff --stat
git diff
git diff --staged
```

If nothing is staged AND nothing is modified, stop and tell the user there's nothing to review.

## 2. Load relevant conventions

For each changed file, read the matching rule file:
- `.vue` / `.ts` / `.tsx` / `*.scss` → `.claude/rules/frontend.md`
- HTTP / `axios` / `src/api/` → `.claude/rules/api.md`
- `*.spec.*` / `*.test.*` / `tests/**` → `.claude/rules/testing.md`

Skip rule files that don't match — don't load all three by default.

## 3. Check by category

For each changed file:

| Category | What to look for |
|----------|------------------|
| **Correctness** | Type errors, off-by-one, null/undefined handling, async/await misuse, missing await on Promise |
| **Security** | XSS via `v-html`, unsanitized user input, hardcoded secrets, axios `baseURL` set to literal URL instead of env var |
| **Conventions** | Deviations from `.claude/rules/*` |
| **Performance** | Unnecessary reactivity, large bundle additions, blocking computation in render |
| **Maintainability** | Unused exports, dead code, missing types, unclear names, comments that explain WHAT (forbidden by global rules) |

## 4. Report

Format findings by severity:

```
🔴 BLOCKERS  — must fix before commit
🟡 SUGGESTED — should fix, not blocking
🔵 NITS      — style/preference, optional
```

Each finding: `path:line — category — problem — proposed change`.

If everything is clean, say so explicitly.

## 5. Offer next step

End with one of:
- "Want me to apply the blockers?"
- "Want me to hand off to the **code-reviewer** subagent for a deeper pass?"
- "Looks ready — want me to draft a commit message?" (do NOT commit; per global rule, always confirm first)

## Guardrails
- This skill is read-only by default.
- NEVER run `git commit`, `git push`, or `gh pr create` from this skill.
- For deep architectural review, escalate to the `code-reviewer` subagent rather than expanding scope here.
