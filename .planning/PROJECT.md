# Tooling Release Digest

<!-- TODO: choose specific tech stack and tools (for telegram api), uv venv create path, quality gate -->
<!-- use python guidelines skill to validate plan -->
<!-- run using qwen to validate final plan before implementing it -->
## What This Is

An application that monitors tools, frameworks, and plugins for new releases, analyzes their changelogs, and alerts the user if an update is worth installing. The primary focus is AI tooling (e.g., opencode, qwen-code, superpowers, get-shit-done).

## Core Value

Automatically filtering and alerting on high-value AI tooling updates via Telegram to ensure the user stays current without manual overhead.

## Requirements

### Validated

(None yet — ship to validate)

### Active

- [ ] Polling GitHub releases for a manually defined list of projects and versions.
- [ ] Ignoring nightly builds and patch releases unless specified.
- [ ] Analyzing changelogs to determine if an update is "worth installing".
- [ ] Sending notifications via a Telegram bot.
- [ ] Manual overrides to skip analysis for specific tools.

### Out of Scope

- [ ] Support for F-Droid, websites, and blogs (Deferred to v2).
- [ ] Auto-detection of installed tool versions from the local Linux system (Deferred to v2).

## Context

The project aims to be a lightweight, 12-factor application with minimal dependencies. It should integrate with the local `python-guidelines` skill for Python development standards.

## Constraints

- **Language**: Python 3.13 — Required for modern language features.
- **Dependency**: Minimal — Use standard HTTP requests (httpx/niquests) instead of heavy GitHub API clients.
- **Principles**: 12-factor app — Ensure portability and scalability.
- **Database**: SQLite — Simple, local storage for tool state.
- **Logging**: structlog — Structured logging for better observability.

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| Core Stack: Python 3.13, msgspec, httpx, SQLite | Lightweight and performant defaults for the domain. | — Pending |

---
*Last updated: 2026-03-18 manually*
