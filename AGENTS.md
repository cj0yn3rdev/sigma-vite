# AGENTS.md — sigma-vite

Tool-agnostic agent instructions for this project. Read by GitHub Copilot, OpenAI Codex CLI, Cursor, Aider, and other AGENTS.md-aware tools. Inherits all global conventions from `~/AGENTS.md`.

## Project Snapshot
- **Origin:** forked from `savannabits/sigma-vite` (a Vite/Vue 3/TS port of `primefaces/sigma-vue`)
- **Upstream:** `https://github.com/savannabits/sigma-vite`
- **Fork:** `https://github.com/cj0yn3rdev/sigma-vite`
- **Stack:** Vue 3 + TypeScript + Vite 2 + PrimeVue 3 + PrimeFlex + Sass

## Project Rule Files
Per the global convention in `~/AGENTS.md`, project conventions live in `.claude/rules/` (the directory is shared across agents — Codex, Copilot, Cursor, etc. all read it):
- `.claude/rules/testing.md` — testing framework + conventions
- `.claude/rules/api.md` — API/HTTP conventions (axios)
- `.claude/rules/frontend.md` — Vue/PrimeVue/styling conventions

Read these before non-trivial changes; update them when conventions evolve.

## Project Skills (Claude Code)
Defined in `.claude/skills/`. These are Claude Code-specific but the documented protocols (test triage, pre-commit review) translate to other agents:
- `/test` — run tests, triage failures, propose fixes (max 3 iterations)
- `/review` — read-only review of staged/unstaged changes against project rules

## Project Memory
- `./.claude/memory.md` — committed scratchpad for project-specific decisions, gotchas, and upstream sync log. All agents should read it before non-trivial changes and update it when they learn something durable.

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
