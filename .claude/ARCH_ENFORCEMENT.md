# {{PROJECT_NAME}} — Architectural Enforcement

> Rules and invariants the DSO review skills enforce automatically. Update as patterns solidify.

## Stack invariants

1. **App Router only** — do not introduce Pages Router routes (`pages/` directory). All routes live under `src/app/`.
2. **TypeScript strict mode is non-negotiable** — do not silence the type checker with `// @ts-ignore` or `any` shortcuts; fix the type.
3. **Server Components by default** — only add `"use client"` when the component needs state, effects, or browser APIs.
4. **Single source of styling tokens** — colors, spacing, and typography come from USWDS theme variables (or your declared replacement). No hard-coded hex values in components.

## Anti-patterns

1. **Inline styles for layout** — use SCSS modules or USWDS utility classes; inline `style={{}}` is for one-off, dynamic values only.
2. **Direct DOM manipulation** — no `document.querySelector` in components. Use refs.
3. **Side effects at module scope** — no `console.log`, network calls, or state mutations outside hooks/handlers.
4. **Components > 200 lines** — split into smaller composable pieces. Long components are a refactor smell.
5. **Untested route handlers** — `src/app/api/**/route.ts` files need at least one happy-path test.

## Test invariants

1. **Behavioral tests only** — do not write tests that grep source files or assert "this function exists". Tests must execute code and assert on observable behavior.
2. **No snapshot-only tests** — snapshots are change detectors, not behavior verifiers. Use them sparingly and pair with real assertions.
3. **i18n strings come from translation files** — tests must not hard-code English strings; reference the same source the component does.

## Dependency policy

1. **Prefer existing dependencies** — check `package.json` before adding a new package.
2. **No abandoned packages** — verify `npm` shows recent (last 12 months) maintenance before adding.
3. **License compatibility** — Apache-2.0 / MIT / BSD only; no GPL or proprietary additions without explicit user approval.

## Layout invariants

- Routes live under `src/app/`.
- Reusable UI under `src/components/`.
- Feature modules under `src/features/<feature-name>/`.
- Shared utilities under `src/lib/`.
- Translation strings under `src/i18n/locales/<locale>.json`.
- Tests colocated with source (`src/components/Button.test.tsx`) or in `tests/` for cross-feature integration.

## Review escalation

When a review finding involves any of the rules above, the autonomous resolution loop is **not** allowed to dismiss it as a false positive. Either fix the code or escalate to the user.
