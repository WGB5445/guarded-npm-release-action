# Guarded NPM Release Action

A standalone composite GitHub Action for safe npm releases.

## What it does

- Validates version format:
  - stable: `x.y.z` -> `latest`
  - beta: `x.y.z-beta.n` -> `beta`
- Optional tag/version match check
- Optional main-branch ancestry guard
- Optional npm version existence check
- Supports three modes:
  - `preflight`
  - `dry-run`
  - `publish`

## Minimal usage

```yaml
jobs:
  release:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      id-token: write
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 22.x
          registry-url: https://registry.npmjs.org
      - uses: pnpm/action-setup@v4
        with:
          version: 10.11.0
          run_install: false
      - uses: WGB5445/guarded-npm-release-action@v1
        with:
          package_dir: packages/sdk
          publish_mode: dry-run
```

## Inputs / outputs

See [`action.yml`](./action.yml).
