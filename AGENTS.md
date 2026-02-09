# Repository Guidelines

## Project Structure & Module Organization
This repository hosts the Caricare wiki built with Docsify. Key paths:
- `docs/` published wiki content and config (`_sidebar.md`, `_navbar.md`, `index.html`).
- `docs/docs-*/` localized content (e.g., `docs/docs-it`, `docs/docs-en`).
- `docs/_images` and `docs/_media` assets referenced by the wiki.
- `src/`, `packages/`, `build/` Docsify source and build scripts.
- `server.js` local dev server used by `npm run serve`.

## Build, Test, and Development Commands
- `npm install` install dependencies.
- `npm run serve` start the local server on `http://localhost:3000`.
- `npm run dev` run the server with JS/CSS watchers.
- `npm run lint` run ESLint with auto-fix.
- `npm test` run linting only.
- `npx docsify serve docs` run the Docsify CLI server for wiki content.

## Coding Style & Naming Conventions
- JavaScript follows `xo-space`: 2-space indentation, no semicolons.
- ESLint config lives in `.eslintrc`.
- Keep filenames consistent with existing patterns (e.g., `machine-*.png`, `docs-<lang>`).

## Testing Guidelines
There are no unit tests in this repository, and no coverage targets are defined. Use `npm test` or `npm run lint` before submitting changes. If you add tests, document the runner and location (e.g., `tests/`).

## Commit & Pull Request Guidelines
Git history uses short, descriptive messages, sometimes with PR numbers (e.g., `fix: typo`, `Update index.html`, `... (#43)`). Keep commits concise and scoped.
Pull requests should explain the change, include validation steps, and add tests when relevant or note why none are needed. Smaller PRs review faster.

## Configuration Tips
The wiki is served from `docs/`. Update Markdown there and verify locally with `npx docsify serve docs` or `npm run serve` before publishing.
