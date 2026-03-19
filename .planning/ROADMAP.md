# Roadmap: Tooling Release Digest

**Status:** Proposed
**Current Milestone:** v1.0
**Requirements Mapped:** 8/8 ✓

## Milestone: v1.0 — Initial Polling and Notification

Goal: Build a functional tool to monitor and alert on AI tooling releases via Telegram.

### Phase 1: Foundation and GitHub Polling

**Goal:** Establish the 12-factor foundation and core polling engine for GitHub releases.
**Requirements:** CORE-01, CORE-02, CORE-03
**Plans:** 2 plans
- [ ] 01-01-PLAN.md — Foundation and Database
- [ ] 01-02-PLAN.md — GitHub Polling Engine and CLI
**Success Criteria:**
1. Application can fetch latest releases from GitHub for a hardcoded list of projects.
2. Application correctly identifies new releases using a local SQLite state.
3. Application logs are structured (structlog) and environment-based (env-config).

### Phase 2: Analysis and Filtering Logic

**Goal:** Implement logic to filter out noise (nightly, non-major) and identify high-value updates.
**Requirements:** FLTR-01, FLTR-02, FLTR-03
**Success Criteria:**
1. Nightly/pre-releases are filtered out by default.
2. Manual overrides successfully skip analysis or force alerting for specific tools.
3. Application can extract and log the "worth installing" summary for a new release.

### Phase 3: Telegram Integration and Delivery

**Goal:** Integrate with Telegram bot API to deliver formatted alerts.
**Requirements:** ALRT-01, ALRT-02
**Success Criteria:**
1. Formatted alerts are received in the target Telegram chat.
2. Alerts contain all required project metadata and analysis summaries.
3. Full end-to-end polling-to-alerting loop is verified.

---
*Roadmap created: 2026-03-17*
*Last updated: 2026-03-17 after initialization*
