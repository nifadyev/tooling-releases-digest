# Tooling Release Digest

## Purpose
An app that monitors tools, frameworks, and plugins for new releases, analyzes their changelogs, and alerts you if an update is worth installing. The primary focus is AI tooling (e.g., opencode, qwen-code, superpowers, get-shit-done).

## Features
- Polls for new releases periodically.
- Ignores nightly builds.
- Allows manual overrides to skip analysis for specific tools, alerting only on major releases.
- Sends notifications via a Telegram bot.

## Technical Constraints
- Follow 12-factor app principles.
- Keep dependencies to a minimum (e.g., use standard HTTP requests instead of heavy GitHub API clients).
- Incorporate the [pylines skill](https://github.com/community-of-python/pylines/blob/main/pylines-skill/SKILL.md), to be manually adapted later.

## Stack
- **Core:** Python 3.13, a Telegram SDK, msgspec (serialization and DB models), httpx or niquests (API requests), structlog (logging), SQLite.
- **Dev:** uv, ruff, flake8 + wemake-python-styleguide, lefthook, pyright or mypy.
- **Test:** pytest, faker, hypothesis or schemathesis.

## Roadmap
1. Check GitHub releases for a manually defined list of projects and versions.
2. Add support for F-Droid, websites, and blogs.
3. Auto-detect installed tool versions from the local Linux system.
