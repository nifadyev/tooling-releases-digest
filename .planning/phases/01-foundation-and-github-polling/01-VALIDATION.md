---
phase: 01
slug: foundation-and-github-polling
status: draft
nyquist_compliant: true
wave_0_complete: false
created: 2026-03-19
---

# Phase 01 — Validation Strategy

> Per-phase validation contract for feedback sampling during execution.

---

## Test Infrastructure

| Property | Value |
|----------|-------|
| **Framework** | pytest 8.x |
| **Config file** | pyproject.toml |
| **Quick run command** | `uv run pytest -q --tb=short` |
| **Full suite command** | `uv run pytest -n auto` |
| **Estimated runtime** | ~1 seconds |

---

## Sampling Rate

- **After every task commit:** Run `uv run pytest -q -k [keyword]`
- **After every plan wave:** Run `uv run pytest -n auto`
- **Before `/gsd-verify-work`:** Full suite must be green
- **Max feedback latency:** 1 seconds

---

## Per-Task Verification Map

| Task ID | Plan | Wave | Requirement | Test Type | Automated Command | File Exists | Status |
|---------|------|------|-------------|-----------|-------------------|-------------|--------|
| 01-01-01 | 01 | 1 | CORE-03 | unit | `uv run pytest tests/test_config.py` | ❌ W0 | ⬜ pending |
| 01-01-02 | 01 | 1 | CORE-02 | unit | `uv run pytest tests/test_db.py` | ❌ W0 | ⬜ pending |
| 01-02-01 | 02 | 2 | CORE-01 | int | `uv run pytest tests/test_github.py` | ❌ W0 | ⬜ pending |
| 01-02-02 | 02 | 2 | CORE-01 | e2e | `uv run pytest tests/test_cli.py` | ❌ W0 | ⬜ pending |

*Status: ⬜ pending · ✅ green · ❌ red · ⚠️ flaky*

---

## Wave 0 Requirements

- [ ] `tests/test_config.py` — stubs for config loading
- [ ] `tests/test_db.py` — stubs for DB
- [ ] `tests/test_github.py` — stubs for GitHub polling
- [ ] `tests/test_cli.py` — stubs for CLI execution
- [ ] `tests/conftest.py` — shared fixtures for db and mock HTTP (respx)
- [ ] Test tools install via `uv`

---

## Manual-Only Verifications

| Behavior | Requirement | Why Manual | Test Instructions |
|----------|-------------|------------|-------------------|
| None | N/A | All automated | N/A |

*If none: "All phase behaviors have automated verification."*

---

## Validation Sign-Off

- [x] All tasks have `<automated>` verify or Wave 0 dependencies
- [x] Sampling continuity: no 3 consecutive tasks without automated verify
- [x] Wave 0 covers all MISSING references
- [x] No watch-mode flags
- [x] Feedback latency < 5s
- [x] `nyquist_compliant: true` set in frontmatter

**Approval:** approved 2026-03-19