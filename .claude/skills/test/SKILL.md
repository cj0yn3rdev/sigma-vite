---
name: test
description: Run the project's tests, diagnose failures, and propose fixes. Use when the user types /test, asks to "run tests", or after code changes that need verification.
---

# /test — Test Runner & Fixer

## 1. Detect the test runner

Check `package.json` for a `test` script. If absent:
- Look for installed runners: `vitest`, `jest`, `mocha`, `@vue/test-utils`
- If none found, **stop and tell the user no runner is configured**. Recommend **Vitest** (native Vite integration) and ask whether to set it up. Do not assume.

## 2. Run the suite

```bash
npm test 2>&1
```

Capture full output. Do not silently retry on failure.

## 3. Triage failures

For each failure:
- Read the failing test file
- Read the production code under test
- Identify root cause (per `.claude/rules/testing.md`)
- Classify: production bug / test bug / environmental issue / flake

## 4. Propose fixes

For each failure, show the user:
- Cause (one sentence)
- File + line range (`path:line`)
- Proposed change as a diff

Apply changes only after explicit approval for non-trivial edits.

## 5. Re-run, capped

Re-run after fixes. Cap at **3 iterations** — if failures persist, stop and ask for direction. Do not thrash.

## Guardrails
- Read `.claude/rules/testing.md` before editing tests.
- NEVER delete failing tests to make the suite pass.
- NEVER add `try/catch` around test bodies to swallow errors.
- NEVER mark tests `.skip` to bypass them — surface the failure instead.
