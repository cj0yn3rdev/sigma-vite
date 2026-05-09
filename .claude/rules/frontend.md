# Frontend Conventions

> Stub — populate as conventions emerge. See `~/.claude/CLAUDE.md` for the global convention this file fulfills.

## Stack
- **Framework:** Vue 3 (Composition API preferred for new code)
- **Language:** TypeScript (strict mode TBD — verify in `tsconfig.json`)
- **Build:** Vite 2
- **Router:** vue-router 4
- **UI library:** PrimeVue 3 + PrimeFlex (utility classes) + PrimeIcons
- **Styling:** Sass/SCSS — themes in `src/assets/theme/`

## Component Patterns
- **SFC** (`.vue`) with `<script setup lang="ts">` for new components.
- Keep `<template>` markup-light — extract logic to composables (`src/composables/`).
- Props typed via `defineProps<{...}>()`; emits via `defineEmits<{...}>()`.

## Styling
- Prefer **PrimeFlex utility classes** (`p-d-flex`, `p-mt-3`, etc.) for layout.
- Component-scoped styles via `<style lang="scss" scoped>`.
- Theme variables via SCSS variables in `src/assets/theme/`; switching is wired through `localStorage`.

## State Management (TBD)
- No store configured by default. If/when needed, prefer **Pinia** over Vuex for new code.

## Accessibility (TBD)
- Default to PrimeVue's built-in a11y (ARIA, keyboard nav). Verify with axe / Lighthouse on new components.

## File Layout
```
src/
  components/   shared, presentational
  views/        route-level pages
  layout/       app shell (topbar, sidebar, footer)
  router/       vue-router config
  composables/  reusable Composition API logic
  api/          axios services (see api.md)
  assets/       static + theme SCSS
```
