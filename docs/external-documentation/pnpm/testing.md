<!-- Authored for repository documentation after migration from Bun to pnpm on 2026-04-26. -->
<!-- Include this file in context when running or troubleshooting tests with pnpm. -->

# pnpm Testing Guide

This project uses `pnpm` as the package manager and script orchestrator across the monorepo.
`pnpm` does not provide a built-in test runner. Instead, it executes test commands defined in each package's `package.json`.

## Run Tests

Run tests from the repository root:

```bash
pnpm test
```

If the root `test` script delegates to a task runner (for example `task test`), pnpm executes that command exactly as configured.

## Run Tests for a Specific Workspace

Use the workspace filter flag to run tests for one package or application:

```bash
pnpm --filter @starter-project/models test
```

You can also target by path or glob pattern:

```bash
pnpm --filter "./packages/*" test
pnpm --filter "./apps/next-app" test
```

## Run Test Scripts Recursively

To execute `test` in all workspaces that define that script:

```bash
pnpm -r test
```

Useful recursive options:

- `--parallel`: run scripts in parallel.
- `--workspace-concurrency <n>`: set max concurrent workspace jobs.
- `--stream`: stream logs prefixed by workspace name.

Example:

```bash
pnpm -r --parallel --stream test
```

## Run in Watch Mode

If a workspace exposes a watch test script, execute it with pnpm:

```bash
pnpm --filter "./apps/next-app" test:watch
```

## CI/CD Integration

In CI environments, use deterministic installs and then execute tests:

```bash
pnpm install --frozen-lockfile
pnpm test
```

For monorepos, a common CI pattern is:

```bash
pnpm -r --workspace-concurrency=1 test
```

This favors stable output ordering and reproducibility.

## Troubleshooting

### Missing script: "test"

If pnpm reports a missing test script, add a `test` entry in the relevant `package.json`.

### Filtering returns no projects

Verify that:

- The workspace is included in root workspace configuration.
- The `--filter` selector matches package name or path.

### Lockfile mismatch in CI

Run locally and commit lockfile updates:

```bash
pnpm install
```

Then re-run:

```bash
pnpm install --frozen-lockfile
```

## References

- pnpm CLI documentation: https://pnpm.io/cli
- pnpm filtering documentation: https://pnpm.io/filtering
- pnpm workspaces documentation: https://pnpm.io/workspaces
