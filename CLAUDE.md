# {{PROJECT_NAME}} — Claude Code Project Configuration

You are working in `{{PROJECT_NAME}}`, a Next.js + TypeScript prototype scaffolded from the Digital Service Orchestra (DSO) NextJS template (`navapbc/digital-service-orchestra-nextjs-template`).

This project is set up for **rapid prototyping by non-engineers**. The DSO plugin powers your workflow: brainstorming features, planning roadmaps, and shipping stories with safety gates.

## Quick Reference

| Action | Command |
|--------|---------|
| Brainstorm a roadmap | `/dso:roadmap` |
| Brainstorm one feature → epic | `/dso:brainstorm` |
| Decompose epic → stories | `/dso:preplanning <epic-id>` |
| Plan a story → tasks | `/dso:implementation-plan <story-id>` |
| Execute an epic end-to-end | `/dso:sprint <epic-id>` |
| Fix a bug (TDD) | `/dso:fix-bug <bug-id>` |
| Commit (with review gates) | `/dso:commit` |
| Run dev server | `npm run dev` |
| Run unit tests | `npm test` |
| Lint | `npm run lint` |
| Format | `npm run format` |
| List ready tickets | `.claude/scripts/dso ticket list` |
| Show ticket details | `.claude/scripts/dso ticket show <id>` |

The first thing to run in a fresh project is `/dso:roadmap` — it walks you from "I have a product idea" to a prioritized epic backlog.

## Architecture

- **Framework**: Next.js (App Router) + TypeScript
- **UI library**: React + USWDS (U.S. Web Design System) via `react-uswds`
- **Styling**: SCSS with USWDS theming
- **Testing**: Jest + React Testing Library; Storybook for component workshop
- **Tooling**: ESLint, Prettier, pre-commit hooks

App source lives at the repo root (no monorepo subdirectory). Entry points: `src/app/page.tsx`, `src/app/layout.tsx`.

## Critical Rules

### Never Do These

1. **Never commit `node_modules/` or `.env*` secrets** — `.gitignore` is configured; do not override.
2. **Never bypass the review gate** with `--no-verify`. The gate is here to catch problems before they land. If a hook is wrong, fix the hook.
3. **Never make changes without a way to validate them** — every code change either has a corresponding test (RED → GREEN), a runnable demo, or an explicit note on how to verify by hand.
4. **Never push directly to `main`** — open a pull request and let the CI workflow run.
5. **Never edit safeguard files** (pre-commit hooks, CI workflow, review gate) without explicit user approval.

### Always Do These

1. **Use `/dso:sprint` for executing epics** — the orchestrator handles batching, review, commit, and merge.
2. **Use `/dso:fix-bug` for bug tickets** — runs the TDD loop with intent verification.
3. **Run `npm run dev` before claiming a UI feature works** — see it in the browser. Type checks alone do not verify behavior.
4. **Create tickets for all discovered issues** via `.claude/scripts/dso ticket create bug "<title>"`.
5. **Parallelize independent tool calls** — Read, Glob, Grep, Bash with no data dependency should run concurrently.

## Working Directory & Paths

The project root is the repo root. The DSO plugin is referenced via `.claude/scripts/dso` (the host-project shim). The shim resolves `dso.plugin_root` from `.claude/dso-config.conf`; this is set automatically by the installer.

## Stack & Conventions

- **TypeScript strict mode** is on. Add types; do not silence the type checker.
- **Functional components** only — no class components.
- **App Router** (not Pages Router) — routes live under `src/app/`.
- **Server Components** by default; mark interactive components with `"use client"`.
- **i18n** uses `next-intl`; translation strings live in `src/i18n/locales/*.json`.

## Documentation

- `project-understanding.md` — what this app does, who it serves, what success looks like. **Edit this** as the project evolves; the DSO planning skills consult it.
- `design-notes.md` — visual design decisions, design system overrides, component patterns. The `/dso:design-review` skill enforces compliance with this file.
- `.claude/ARCH_ENFORCEMENT.md` — architectural invariants and anti-patterns to enforce.
- `docs/` — Architecture Decision Records (ADRs) and operational docs.

## Getting Help

- `/help` — Claude Code help
- Report DSO plugin issues at https://github.com/navapbc/digital-service-orchestra/issues
