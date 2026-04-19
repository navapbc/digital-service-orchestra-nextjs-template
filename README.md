# {{PROJECT_NAME}}

A Next.js + TypeScript prototype scaffolded from the [Digital Service Orchestra (DSO) NextJS template](https://github.com/navapbc/digital-service-orchestra-nextjs-template).

## Quick start

```bash
npm install
npm run dev
```

Then open <http://localhost:3000>.

## Working with this project in Claude Code

This project is wired to the **DSO Claude Code plugin**, which provides skills for product roadmapping, epic decomposition, story planning, and TDD-based execution.

```bash
claude        # launches Claude Code in this directory
```

Inside Claude Code, the first command to try:

```
/dso:roadmap
```

It walks you from "I have an idea" to a prioritized backlog of epics. From there, `/dso:sprint <epic-id>` executes an epic end-to-end with safety gates.

See [CLAUDE.md](CLAUDE.md) for the full DSO command reference and project conventions.

## Stack

- **Framework**: [Next.js](https://nextjs.org/) (App Router) + [TypeScript](https://www.typescriptlang.org/)
- **UI**: [USWDS](https://designsystem.digital.gov) via [`react-uswds`](https://github.com/trussworks/react-uswds)
- **Styling**: SCSS with USWDS theming
- **Testing**: [Jest](https://jestjs.io/) + [React Testing Library](https://testing-library.com/), [Storybook](https://storybook.js.org/) for components
- **i18n**: [next-intl](https://next-intl-docs.vercel.app/)

## Available scripts

| Command | What it does |
|---------|--------------|
| `npm run dev` | Start the development server on port 3000 |
| `npm run build` | Build the production bundle |
| `npm run start` | Run the production bundle |
| `npm test` | Run unit tests with Jest |
| `npm run lint` | Run ESLint |
| `npm run format` | Format with Prettier |
| `npm run format:check` | Check formatting without writing |
| `npm run storybook` | Launch Storybook on port 6006 |

## Project documentation

- [CLAUDE.md](CLAUDE.md) — Claude Code project configuration and DSO command reference.
- [project-understanding.md](project-understanding.md) — what this project is, who it serves, what success looks like. **Edit as the project evolves.**
- [design-notes.md](design-notes.md) — design decisions and design-system conventions.
- [.claude/ARCH_ENFORCEMENT.md](.claude/ARCH_ENFORCEMENT.md) — architectural invariants the DSO review skills enforce.
- [docs/](docs/) — Architecture Decision Records and operational docs.

## Provenance and license

This project was scaffolded from the [DSO NextJS template](https://github.com/navapbc/digital-service-orchestra-nextjs-template), which is itself derived from [`navapbc/template-application-nextjs`](https://github.com/navapbc/template-application-nextjs).

Both the template and this scaffolded project are released under the [Apache License 2.0](LICENSE). Attribution to the upstream template is preserved in [NOTICE](NOTICE).

## Security

See [SECURITY.md](SECURITY.md) for vulnerability reporting.
