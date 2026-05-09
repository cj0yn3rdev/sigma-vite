# API Conventions

> Stub — populate as conventions emerge. See `~/.claude/CLAUDE.md` for the global convention this file fulfills.

## HTTP Client
- **axios** (^0.21.4) — already in dependencies.
- Centralize base URL, auth headers, and interceptors in a single `src/api/` (or `src/services/`) module — do not scatter `axios.create()` calls across components.

## Conventions (TBD)
- Base URL strategy: env var (`VITE_API_BASE_URL`) — TBD
- Auth: bearer token / cookie / session — TBD
- Error format: standardize on `{ code, message, details? }` — TBD
- Pagination: cursor vs offset — TBD
- Naming: kebab-case URLs, camelCase JSON keys — TBD

## Patterns
- Wrap raw axios calls in typed service functions (`fetchInvoices()`, `createInvoice(payload)`).
- Map API responses to domain models before they leave the service layer — components should never see raw API shapes.
- Surface errors with discriminated union return types or thrown typed errors — pick one, document here once chosen.
