# Feature: Rename Agent.md to AGENTS.md

## Overview
This change standardizes the agent instruction filename at the repository root by renaming `Agent.md` to `AGENTS.md`.

## Objective
Ensure repository-level agent guidance follows the canonical uppercase naming pattern used by automation and agent discovery workflows.

## Scope
- Renamed file:
  - `Agent.md` -> `AGENTS.md`

## Implementation Details
- The change is a filesystem-level rename only.
- No content modifications were applied to the file.
- No runtime, build, dependency, or application behavior changes were introduced.

## Validation
- Verified the source file no longer exists under the old name.
- Verified the renamed file exists at the repository root.
- Verified Git tracks the operation as a rename.

## Impact Assessment
- **Code impact:** None
- **Behavioral impact:** None
- **Documentation impact:** Improved consistency for agent-instruction file discovery.

## Rollback Plan
If rollback is required, rename `AGENTS.md` back to `Agent.md`.
