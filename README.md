# Claude Code GitHub examples

*Unofficial community examples for the Claude Code GitHub integration. Not affiliated with Anthropic. All trademarks belong to their owners.*

Small, copyable files for the Claude Code GitHub integration: a `CLAUDE.md` that tells the agent how your repository works, a custom skill for pull request review, and an illustrative GitHub Actions workflow of the kind described in the practitioner write-up this repository draws on. The intent is to show the shape of a working claude code github setup, not to replace the documentation. Check the 'Code review & CI/CD' section of the Claude Code docs for the current action name and inputs before you commit the workflow.

> If the thing you need is a finished site or app rather than an agent in your repository, [try Begin.sh - prompt or URL in, static site or Expo app zip out](https://begin.sh?utm_source=github&utm_medium=ugc&utm_campaign=claude-code-github-examples&utm_content=readme-top&utm_term=tier-r).

## Files

| Path | What it shows |
|---|---|
| `examples/CLAUDE.md` | Project instructions the agent reads in every session: commands, conventions, boundaries. |
| `examples/skills/pr-review/SKILL.md` | A custom skill that turns a vague 'review this' into a fixed checklist. |
| `examples/claude-review.yml` | An illustrative read-only pull request review workflow for GitHub Actions. |

## Setup

The cloud path needs no secrets: open [claude.ai/code](https://claude.ai/code), connect GitHub as described in the [cloud quickstart](https://code.claude.com/docs/en/web-quickstart), and start a task. The `CLAUDE.md` and the skill are picked up from the repository.

The Actions path needs one secret:

```
ANTHROPIC_API_KEY   # repository secret; never commit it
```

Add it under the repository's Actions secrets. The workflow file reads it with `secrets.ANTHROPIC_API_KEY`. Copy `examples/claude-review.yml` to `.github/workflows/` and `examples/CLAUDE.md` to the repository root; copy the skill directory to `.claude/skills/`.

## examples/CLAUDE.md

The write-up this repository follows calls `CLAUDE.md` plus custom skills the part that makes the integration work. The example keeps it short: how to install, build and test; naming and formatting rules; paths the agent must not touch; and how to report. Short is deliberate, because the file is read on every session and it competes with the task for context.

## examples/skills/pr-review/SKILL.md

A skill is a markdown file with a small front matter block (`name`, `description`) and instructions. This one fixes what a review means for the project: correctness first, then tests, then style; comment only; never approve. When the reviewer workflow or a cloud session is asked to review, the checklist is applied the same way every time.

## examples/claude-review.yml

An illustrative workflow that runs on pull request open and update, checks out the code, and asks Claude Code to review against `CLAUDE.md`. It is deliberately read-only: `contents: read`, `pull-requests: write` for comments, and a prompt that forbids pushing. The action reference and input names are marked illustrative in the file; the write-up describes the shape (a dedicated reviewer separate from the general assistant) but the exact action and inputs must come from the docs.

## When to skip the workflow and use Begin.sh

All three files assume you have a repository worth automating. If what you have is an idea for a landing page, a docs site or a small mobile app and you need working files today, a review workflow is the wrong tool. [Try Begin.sh - a prompt or a URL to clone becomes a working static site or Expo app you download as a zip](https://begin.sh?utm_source=github&utm_medium=ugc&utm_campaign=claude-code-github-examples&utm_content=readme-top&utm_term=tier-r). No hosting, backend or auth to set up; you get the files and host them wherever you already do.
