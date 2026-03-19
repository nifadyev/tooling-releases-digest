# Phase 1: Foundation and GitHub Polling - Context

**Gathered:** 2026-03-19
**Status:** Ready for planning

<domain>
## Phase Boundary

Establish the 12-factor foundation and core polling engine for GitHub releases. The application will fetch the latest releases from GitHub for a hardcoded list of projects, correctly identify new releases using a local SQLite state, and output structured logs. Analysis and alerting are out of scope for this phase.

</domain>

<decisions>
## Implementation Decisions

### Execution Model
- Manually run CLI script (`main.py` at project root).
- Projects are processed sequentially (one at a time).
- On error fetching a project, log the error and continue to the next project.
- No dry-run mode or CLI framework for now.

### Configuration Source
- TOML format (`projects.toml`) for listing monitored projects and their full settings.
- Config file lives local to the project.
- Secrets (like GitHub PAT) provided via `.env` file, loaded with `pydantic-settings`.

### GitHub Authentication
- Use Personal Access Token (PAT) via the GitHub REST API.
- If rate limit is hit, fail fast for now.

### State Storage Depth
- Store a basic history of all seen releases (tag, date) and the user's currently used version (specified in config).
- Use a local `state.db` file in the project root.
- Use raw `sqlite3` (no SQLAlchemy).
- Schema managed via custom SQL migrations.

### Project Structure
- `src/` for application logic, `tests/` for tests.
- Dependency management with `pyproject.toml` + `uv`.
- Virtual environment managed externally (`~/.virtualenvs/tooling-releases-digest`).
- CI/CD via GitHub Actions and local pre-commit hooks via `lefthook` (lint, format, mypy/pyright).

### Logging Details
- Structured JSON logging using `structlog`.
- Default log level is `INFO`.
- Include context fields (`repo`, `release_id`, `status`).
- Output to `stdout` only.

### Testing Strategy
- Use `pytest` + `pytest-xdist` + `faker`.
- Prioritize integration tests (fast, not logic-heavy), with unit tests as needed.
- Mock HTTP requests using `respx`.

### Application Flow
- On initial run (empty DB), read the currently used version from the predefined config.
- When a new release is detected, log it and save the state (no alerting yet).

### Claude's Discretion
- Specific schema design for `state.db` and migration script structure.
- Exact TOML structure for `projects.toml`.

</decisions>

<canonical_refs>
## Canonical References

**Downstream agents MUST read these before planning or implementing.**

### General Guidelines
- `.planning/PROJECT.md` — Project vision and constraints
- `.planning/REQUIREMENTS.md` — Phase 1 requirements
- `python-guidelines` skill — For DI, style, and testing standards

</canonical_refs>

<code_context>
## Existing Code Insights

### Reusable Assets
- None (greenfield phase).

### Established Patterns
- Will establish `structlog` setup, `httpx` wrapper, and raw `sqlite3` connection handling.

</code_context>

<specifics>
## Specific Ideas

- Setup `lefthook` for pre-commit hooks to run linting, formatting, and type-checking locally.

</specifics>

<deferred>
## Deferred Ideas

- Cron-triggered execution (deferred to v2 / future phase).
- Parallel processing of projects (deferred to next phases).
- Wait-and-retry on GitHub rate limits (deferred to next phases).
- Logging to a file (deferred to next phase).

</deferred>

---

*Phase: 01-foundation-and-github-polling*
*Context gathered: 2026-03-19*
