# CLAUDE.md

Project instructions for Claude Code. Keep this file short; it is read in every session.

## Commands

- Install: `pnpm install`
- Build: `pnpm build`
- Test: `pnpm test` (run before every commit)
- Lint: `pnpm lint`

## Conventions

- TypeScript strict mode; no `any` without a comment explaining why.
- Small pull requests: one concern per PR.
- Commit messages: imperative mood, first line under 72 characters.

## Boundaries

- Never edit files under `infra/` or `.github/workflows/` without an explicit request.
- Never commit secrets. Configuration comes from environment variables.
- Do not push to `main`; open a pull request instead.

## Reporting

- When a task is done, summarise what changed and how it was verified.
- If tests fail, say so and include the failing output rather than working around it.
