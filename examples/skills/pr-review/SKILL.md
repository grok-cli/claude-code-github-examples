---
name: pr-review
description: Review a pull request against this repository's conventions. Use when asked to review, check or audit a PR.
---

# PR review checklist

Apply this checklist in order. Comment; do not approve, merge or push.

1. Correctness
   - Does the change do what the PR title and description say?
   - Are there edge cases the diff does not handle (empty input, errors, retries)?
2. Tests
   - Is new behaviour covered by a test? If not, say which test file should change.
   - Do the existing tests still pass? Run `pnpm test` if the environment allows.
3. Conventions (see CLAUDE.md)
   - TypeScript strict mode, no unexplained `any`.
   - No edits under `infra/` or `.github/workflows/` unless the PR is explicitly about them.
4. Security
   - No secrets, tokens or credentials in the diff.
   - No new network calls to hosts that are not already used by the project.

## Output format

- One short summary paragraph.
- A bulleted list of findings, each with file and line, ordered by severity.
- End with one of: `LGTM with nits`, `Needs changes`, `Blocked` and one sentence why.
