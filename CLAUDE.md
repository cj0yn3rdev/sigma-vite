# CLAUDE.md — sigma-vite

Project-specific Claude Code instructions. Inherits all global conventions from `~/.claude/CLAUDE.md`.

## Project Snapshot
- **Origin:** forked from `savannabits/sigma-vite` (a Vite/Vue 3/TS port of `primefaces/sigma-vue`)
- **Upstream:** `https://github.com/savannabits/sigma-vite` (configured as `upstream` remote)
- **Fork:** `https://github.com/cj0yn3rdev/sigma-vite` (configured as `origin`)
- **Stack:** Vue 3 + TypeScript + Vite 2 + PrimeVue 3 + PrimeFlex + Sass

## Project Rule Files
Per the global convention, project conventions live in `.claude/rules/`:
- `.claude/rules/testing.md` — testing framework + conventions
- `.claude/rules/api.md` — API/HTTP conventions (axios)
- `.claude/rules/frontend.md` — Vue/PrimeVue/styling conventions

Read these before non-trivial changes; update them when conventions evolve.

## Project Skills
Slash commands defined in `.claude/skills/`:
- `/test` — run the test suite, triage failures, propose fixes (capped at 3 iterations)
- `/review` — read-only review of staged/unstaged changes against project rules

## Memory Layers
1. **Global auto-memory** — `~/.claude/projects/-Users-cj0yn3r/memory/` (cross-project preferences; auto-managed; sigma-vite is registered there)
2. **Project memory** — `./.claude/memory.md` (sigma-vite-specific decisions, gotchas, upstream sync log; committed to repo)
3. **Conversation context** — TaskCreate/TaskUpdate (ephemeral, session-scoped)

Update `./.claude/memory.md` when you learn something the next session shouldn't have to rediscover.

## Upstream Sync Notes
- This is a fork of an active template repo. When pulling from `upstream`, the project-level `CLAUDE.md`, `AGENTS.md`, and `.claude/` directory are local additions — they will not exist upstream and should not conflict.
- Sync command: `git fetch upstream && git merge upstream/main`

## Quick Commands
```bash
npm install              # first-time setup
npm run dev              # vite dev server
npm run build            # vue-tsc typecheck + vite build
npm run serve            # preview production build
```

## Local Notes
_(Add project-specific guidance here as it emerges — architectural decisions, gotchas, deviations from global rules.)_
