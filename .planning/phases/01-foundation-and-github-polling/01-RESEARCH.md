# Phase 01: Foundation and GitHub Polling - Research

## Domain Knowledge: GitHub API Polling
- **Endpoint**: `GET /repos/{owner}/{repo}/releases/latest`
- **Rate limiting**: Authenticated requests allow 5,000 requests/hour. Needs `GITHUB_TOKEN` environment variable for PAT.
- **Data required**: The response includes `tag_name` and `published_at`.

## Configuration Schema (`projects.toml`)
- Using `tomllib` (Python 3.11+) or `tomli`. Since Python 3.11+, `tomllib` is built-in.
- Structure:
  ```toml
  [[projects]]
  name = "uv"
  repo = "astral-sh/uv"
  current_version = "0.1.0"
  ```

## SQLite State Schema
- Table: `releases`
  - `repo` (TEXT)
  - `tag` (TEXT)
  - `published_at` (TEXT)
  - `discovered_at` (TEXT)
  - PRIMARY KEY (`repo`, `tag`)
- Using raw `sqlite3`.

## Environment and Config (`pydantic-settings`)
- `Settings` class:
  - `github_token`: str
  - `projects_file`: str (default `projects.toml`)
  - `db_path`: str (default `state.db`)
  - `log_level`: str (default `INFO`)

## Project Tooling & Architecture
- **Dependency Management**: `uv` + `pyproject.toml`.
- **Pre-commit**: `lefthook` configured for `ruff format`, `ruff check`, and `mypy`.
- **Testing**: `pytest`, `pytest-xdist`, `respx` for mocking `httpx`, `faker` for test data.
- **Logging**: `structlog` outputting JSON to `stdout`.

## Validation Architecture
- **Unit Tests**: DB operations and configuration parsing.
- **Integration Tests**: `respx` mocked GitHub API requests checking if new releases are correctly identified and inserted into SQLite.
- **E2E Tests**: Executing the `main.py` CLI using a dummy `projects.toml` and temporary `state.db`.
