# {{PROJECT_NAME}} — Design Notes

> This file holds **visual design decisions** for `{{PROJECT_NAME}}`. The `/dso:design-review` skill checks proposed UI changes against this file. Update it as the design evolves so reviews stay aligned.

## Design system

This project uses the **U.S. Web Design System (USWDS)** via the [`react-uswds`](https://github.com/trussworks/react-uswds) component library.

USWDS is the default for two reasons:
1. The DSO NextJS template targets civic-tech and government-service prototypes; USWDS is the standard for `.gov` services.
2. Pre-built accessible components reduce the surface for accessibility regressions during prototyping.

If your project does not need USWDS (internal tools, non-government audiences), the design system can be swapped out. Document the swap and rationale here so the design-review skill knows the new baseline.

## Theming

Theme tokens live in SCSS. Override USWDS variables in `src/styles/_uswds-theme.scss` (or the equivalent path for your styling setup). Do not hard-code colors in components — reference theme tokens.

## Component patterns

- Prefer `react-uswds` components over hand-rolled equivalents.
- When `react-uswds` does not provide a component, prefer a thin wrapper around the corresponding USWDS HTML pattern over a from-scratch implementation.
- Server Components by default; mark interactivity-required components with `"use client"`.

## Accessibility

- All interactive components must reach WCAG 2.1 AA.
- Forms must associate labels with inputs (`<label htmlFor>`).
- Pages must have a single `<h1>`; headings nest without skipping levels.
- Color contrast is checked at design time; do not rely on color alone to convey meaning.

## Responsive behavior

- Mobile-first: design for narrow viewports first, then scale up.
- Breakpoints follow USWDS defaults (`mobile`, `tablet`, `desktop`).

## Open design decisions

*Track decisions you have not yet made here so the design-review skill can flag any code that pre-empts them.*

## Decisions log

*Record decisions with a date and rationale as you make them — this becomes the canonical reference when reviewing future changes.*
