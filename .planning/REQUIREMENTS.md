# Requirements: Tooling Release Digest

**Defined:** 2025-01-20
**Core Value:** Automatically filtering and alerting on high-value AI tooling updates via Telegram.

## v1 Requirements

### Core Polling Engine

- [ ] **CORE-01**: Application can poll GitHub releases for a manually defined list of projects (repos).
- [ ] **CORE-02**: Application persists current project versions in a local SQLite database to detect new releases.
- [ ] **CORE-03**: Application implements 12-factor principles (env-based config, stateless execution, structured logging).

### Analysis and Filtering

- [ ] **FLTR-01**: Application ignores nightly builds and pre-releases unless specifically enabled for a project.
- [ ] **FLTR-02**: Application can parse and analyze changelog text (using a simple heuristic or LLM if needed) to determine if an update is "worth installing".
- [ ] **FLTR-03**: User can specify manual overrides per tool to skip analysis and only alert on major releases.

### Telegram Alerts

- [ ] **ALRT-01**: Application sends formatted alerts to a configured Telegram chat via bot API.
- [ ] **ALRT-02**: Alerts include the project name, new version, and a brief summary of why it's worth installing.

## v2 Requirements

### Expanded Sources

- **SRC-01**: Support for monitoring F-Droid releases.
- **SRC-02**: Support for monitoring updates on arbitrary websites and blogs (RSS/HTML scraping).

### System Integration

- **SYS-01**: Auto-detect installed tool versions from the local Linux system to provide context for "worth installing" analysis.

## Out of Scope

| Feature | Reason |
|---------|--------|
| Real-time monitoring | Polling is sufficient for releases; low complexity requirement. |
| Web Dashboard | Telegram bot is the primary and sufficient interface for v1. |
| Heavy GitHub API SDKs | Requirement for minimal dependencies and direct HTTP requests. |

## Traceability

| Requirement | Phase | Status |
|-------------|-------|--------|
| CORE-01 | Phase 1 | Pending |
| CORE-02 | Phase 1 | Pending |
| CORE-03 | Phase 1 | Pending |
| FLTR-01 | Phase 2 | Pending |
| FLTR-02 | Phase 2 | Pending |
| FLTR-03 | Phase 2 | Pending |
| ALRT-01 | Phase 3 | Pending |
| ALRT-02 | Phase 3 | Pending |

**Coverage:**
- v1 requirements: 8 total
- Mapped to phases: 8
- Unmapped: 0 ✓

---
*Requirements defined: 2025-01-20*
*Last updated: 2025-01-20 after initial definition*
