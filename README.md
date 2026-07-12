# .github

Default GitHub community files and reusable automation for my personal projects.

This repository is intentionally lightweight. It is meant for a single developer
maintaining projects across different languages, frameworks, and maturity levels.
Individual repositories can override any of these defaults by adding their own
files.

## What This Provides

- Issue templates for bugs, feature ideas, tasks, and maintenance work.
- A pull request template focused on context, risk, and verification.
- Shared contributing, security, support, and code of conduct guidance.
- Reusable GitHub Actions workflows for common CI checks.
- A profile README location at `profile/README.md`.

## Repository-Specific Overrides

Defaults from this repository apply only when another repository does not define
its own version of the same file. For project-specific behavior, add the matching
file directly to that project.

Common override locations:

- `.github/ISSUE_TEMPLATE/`
- `.github/PULL_REQUEST_TEMPLATE.md`
- `.github/workflows/`
- `CONTRIBUTING.md`
- `SECURITY.md`

## Reusable Workflows

Reusable workflows live in `.github/workflows/` and are designed to be called
from project repositories.

Example:

```yaml
name: CI

on:
  pull_request:
  push:
    branches: [main]

jobs:
  checks:
    uses: alberth/.github/.github/workflows/project-ci.yml@main
```

The default workflow detects common package files and runs the matching checks
when possible.
