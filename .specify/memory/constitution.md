<!--
Sync Impact Report:
- Version change: Unversioned template -> 1.0.0
- List of modified principles:
  - Principle 1: [PRINCIPLE_1_NAME] -> I. Modern Java & Simplicity
  - Principle 2: [PRINCIPLE_2_NAME] -> II. Mandatory Automated Testing
  - Principle 3: [PRINCIPLE_3_NAME] -> III. Versioned Database Migrations
  - Principle 4: [PRINCIPLE_4_NAME] -> IV. Idempotent Scheduled Jobs
  - Principle 5: [PRINCIPLE_5_NAME] -> V. Pluggable Probability Models
  - Added Principle 6: VI. Mathematical Honesty & Mandatory Disclaimers
  - Added Principle 7: VII. Externalized Configuration & Secret Management
  - Added Principle 8: VIII. Structured Batch Observability
- Added sections:
  - Technical Constraints & Operational Standards (replacing [SECTION_2_NAME])
  - Development Workflow & Quality Gates (replacing [SECTION_3_NAME])
- Removed sections: None
- Follow-up TODOs: None (all template placeholders fully resolved)
-->

# Euromilhões Probabilities Constitution

## Core Principles

### I. Modern Java & Simplicity
The application MUST be built using Java 25. Code MUST be simple, clear, and readable. Unnecessary frameworks, speculative abstractions, and superfluous architectural layers are strictly prohibited. Developers MUST favor standard Java platform capabilities and concise idioms over heavyweight third-party dependencies.

### II. Mandatory Automated Testing
Automated tests are non-negotiable and MUST gate all deliverables. Probability calculation models MUST be verified with deterministic unit tests proving mathematical accuracy. Integration tests MUST run against real PostgreSQL instances managed via Testcontainers to validate queries, schemas, and persistence behavior under realistic conditions. In-memory database mocks are forbidden.

### III. Versioned Database Migrations
All database structure and reference data changes MUST be executed exclusively through immutable, versioned migration scripts managed by a migration tool. Direct, manual schema alterations or untracked data modifications in any environment are strictly prohibited. Every environment schema MUST be completely reproducible from repository migration history.

### IV. Idempotent Scheduled Jobs
All scheduled and background batch jobs MUST be strictly idempotent: running a job multiple times consecutively or with overlapping execution windows MUST NOT produce duplicate records or corrupt state. Jobs MUST rely on natural unique keys, upsert patterns, and clear transactional boundaries to ensure safe retries and reruns.

### V. Pluggable Probability Models
The calculation engine MUST support pluggable probability models. Introducing, revising, or removing a probability model MUST NOT require modifications to existing model implementations or the public API contract. Each model MUST implement a shared abstraction, remain isolated, and produce standardized output structures.

### VI. Mathematical Honesty & Mandatory Disclaimers
Euromilhões lottery draws are independent, random events; no model can predict winning numbers or improve a player's odds of winning. Every API response and any user-facing interface MUST include a prominent disclaimer clarifying that:
1. No model predicts or improves chances of winning.
2. Only the "real probability" (combinatorial/theoretical) model has a rigorous mathematical basis, while historical or statistical models reflect past data only.

### VII. Externalized Configuration & Secret Management
All environment-specific configuration—including job execution schedules, data source URLs, connection credentials, and database parameters—MUST be externalized using standard environment variables or runtime configuration files. Secrets and sensitive credentials MUST NEVER be committed to the source repository.

### VIII. Structured Batch Observability
All batch and scheduled jobs MUST emit structured, machine-readable logs. Logs MUST capture the full job lifecycle, explicitly recording: execution start, completion status, execution duration, total records/rows processed, and detailed diagnostic context for any failures.

## Technical Constraints & Operational Standards
- Runtime Platform: Java 25 LTS.
- Primary Storage: PostgreSQL. The persistence approach is decided in the
  implementation plan.
- Testing Suite: JUnit-based unit tests, plus Testcontainers for PostgreSQL
  integration tests.
- Configuration Management: Twelve-factor style configuration. Schedules, the
  data source URL and database settings are externalized, and no secrets are
  committed to the repository.

## Development Workflow & Quality Gates
- Automated Gate: All unit and integration tests MUST pass before changes are
  merged into the main branch, enforced by a CI workflow.
- Database Changes: Every schema change MUST be a versioned migration. Migrations
  MUST apply cleanly on an empty database and on a database containing existing
  data, verified by an automated test.
- Honesty Compliance: An automated test MUST verify that every API response
  includes the mandatory disclaimer, so the rule cannot be broken silently.

## Governance
This constitution constitutes the supreme architectural and engineering policy for the Euromilhões Probabilities project. It supersedes informal conventions and unwritten practices.

- Amendments: Any modification to principles, constraints, or governance requires documented discussion, pull request review, and adherence to semantic versioning.
- Versioning Rules:
  - MAJOR bump: Removing or redefining existing core principles or governance requirements.
  - MINOR bump: Adding new principles, sections, or materially expanding existing rules.
  - PATCH bump: Non-semantic clarifications, typographical corrections, or formatting adjustments.
- Compliance: Every pull request and code review MUST verify adherence to all eight core principles.

**Version**: 1.0.1 | **Ratified**: 2026-11-11 | **Last Amended**: 2026-11-11
