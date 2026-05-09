# Testing Conventions

> Stub — populate as conventions emerge. See `~/.claude/CLAUDE.md` for the global convention this file fulfills.

## Framework
- **Status:** No test runner configured yet. `package.json` has no `test` script.
- **Recommendation when adding:** Vitest (native Vite integration) + `@vue/test-utils` for component tests.

## Conventions (TBD)
- Test file naming: `*.spec.ts` colocated with source, or `tests/` mirror tree
- Coverage target: TBD
- Mocking policy: TBD (prefer real implementations; mock only at network/IO boundary)

## Running tests
```bash
# Once configured
npm run test
```
