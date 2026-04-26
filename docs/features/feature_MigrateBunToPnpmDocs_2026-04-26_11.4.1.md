# Feature: Migrate External Documentation from Bun to pnpm

## Overview
This change updates external tooling documentation to reflect the migration from Bun-based guidance to pnpm-based guidance.

## Objective
Ensure contributors and agents use package-management and testing workflows aligned with the current pnpm monorepo standard.

## Scope
- Renamed external documentation folder:
  - `docs/external-documentation/bun` -> `docs/external-documentation/pnpm`
- Replaced Bun-specific testing guidance with pnpm testing and workspace execution guidance.

## Implementation Details
- The folder rename was applied using Git-aware move semantics.
- The testing document was rewritten with pnpm-specific commands and operational patterns.
- The new guidance includes root-level execution, workspace filtering, recursive runs, CI usage, and troubleshooting.

## Validation
- Verified the legacy `bun` folder is no longer present under `docs/external-documentation`.
- Verified `docs/external-documentation/pnpm/testing.md` exists with pnpm guidance.
- Verified Git tracks both the folder rename and documentation content update.

## Impact Assessment
- **Code impact:** None
- **Behavioral impact:** None at runtime
- **Documentation impact:** Aligns external tooling documentation with current package manager and test execution workflow.

## Rollback Plan
If rollback is required, rename `docs/external-documentation/pnpm` back to `docs/external-documentation/bun` and restore Bun-specific testing documentation.
