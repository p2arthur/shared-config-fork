# @mrcointreau/shared-config

Reusable GitHub Actions workflows and shared configurations for Node.js and Python projects.

[![npm](https://img.shields.io/npm/v/@mrcointreau/shared-config.svg)](https://www.npmjs.com/package/@mrcointreau/shared-config)
[![npm@beta](https://img.shields.io/npm/v/@mrcointreau/shared-config/main.svg?label=npm@beta)](https://www.npmjs.com/package/@mrcointreau/shared-config)

## Overview

This package provides:

- **Reusable GitHub Actions workflows** for CI, PR validation, releases, documentation, and publishing
- **Shared ESLint configuration** for TypeScript projects with Prettier integration
- **Shared Prettier configuration** with consistent formatting rules

Designed to standardize CI/CD pipelines across multiple repositories while keeping configuration DRY.

## Reusable Workflows

| Workflow | Description |
|----------|-------------|
| `ci.yml` | Run lint, test, build, and security audit |
| `pr.yml` | CI + conventional commit linting for pull requests |
| `release.yml` | Semantic release with optional npm/PyPI publishing |
| `docs.yml` | Generate and publish documentation (TypeDoc/Sphinx) |

### CI Workflow

```yaml
# .github/workflows/ci.yml
name: CI

on:
  push:
    branches: [main]

jobs:
  ci:
    uses: mrcointreau/shared-config/.github/workflows/ci.yml@main
    with:
      project-type: node  # or 'python'
```

### PR Workflow

```yaml
# .github/workflows/pr.yml
name: PR

on:
  pull_request:
    branches: [main]

jobs:
  pr:
    uses: mrcointreau/shared-config/.github/workflows/pr.yml@main
    with:
      project-type: node
```

### Release Workflow

```yaml
# .github/workflows/release.yml
name: Release

on:
  push:
    branches: [main]

permissions:
  contents: write
  issues: write
  pull-requests: write
  id-token: write

jobs:
  release:
    uses: mrcointreau/shared-config/.github/workflows/release.yml@main
    with:
      project-type: node
      publish: true
      use-oidc: true
    secrets:
      BOT_ID: ${{ secrets.BOT_ID }}
      BOT_SK: ${{ secrets.BOT_SK }}
```

### Workflow Inputs

#### Common Inputs

| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `project-type` | string | *required* | `node` or `python` |
| `node-version` | string | `22` | Node.js version |
| `python-version` | string | `3.12` | Python version |
| `working-directory` | string | `.` | Working directory |

#### CI/PR Inputs

| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `build-command` | string | auto | Custom build command |
| `lint-command` | string | auto | Custom lint command |
| `test-command` | string | auto | Custom test command |
| `skip-build` | boolean | `false` | Skip build step |
| `skip-lint` | boolean | `false` | Skip lint step |
| `skip-test` | boolean | `false` | Skip test step |
| `skip-audit` | boolean | `false` | Skip security audit |
| `audit-level` | string | `moderate` | Audit severity threshold |

#### Release Inputs

| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `publish` | boolean | `false` | Publish to npm/PyPI |
| `use-oidc` | boolean | `true` | Use OIDC trusted publishing |
| `dist-directory` | string | `dist` | Built package directory |
| `config-path` | string | built-in | Custom semantic-release config |
| `back-merge` | boolean | `false` | Merge release branch back to main |
| `dry-run` | boolean | `false` | Dry-run mode |

## Shared Configs

### Installation

```bash
npm install -D @mrcointreau/shared-config
```

### Peer Dependencies

```bash
npm install -D eslint @eslint/js typescript-eslint eslint-config-prettier eslint-plugin-unused-imports prettier
```

### ESLint Configuration

Create `eslint.config.mjs`:

```javascript
export { default } from '@mrcointreau/shared-config/eslint'
```

Features:
- TypeScript-ESLint recommended rules
- Unused imports detection and auto-removal
- Prettier integration
- Sensible defaults for `node_modules`, `dist`, `build`, `coverage`

### Prettier Configuration

Create `prettier.config.cjs`:

```javascript
module.exports = require('@mrcointreau/shared-config/prettier')
```

Configuration:
- Single quotes
- No semicolons
- 2-space tabs
- Trailing commas
- 140 character line width
- LF line endings

## Composite Actions

Lower-level actions used by the workflows:

| Action | Description |
|--------|-------------|
| `actions/ci/node` | Node.js CI (lint, test, build, audit) |
| `actions/ci/python` | Python CI (lint, test, build, audit) |
| `actions/release/node` | Node.js semantic release |
| `actions/release/python` | Python semantic release |
| `actions/docs/typedoc` | Generate TypeDoc documentation |
| `actions/docs/sphinx` | Generate Sphinx documentation |
| `actions/docs/publish` | Publish to GitHub Pages |
| `actions/utils/bot-token` | Generate GitHub App token |
| `actions/utils/commitlint` | Validate conventional commits |

## Requirements

### GitHub App (for releases)

Create a GitHub App with:
- Repository permissions: Contents (write), Issues (write), Pull requests (write)
- Store `BOT_ID` (App ID) and `BOT_SK` (private key) as repository secrets

### OIDC Trusted Publishing

For npm/PyPI publishing without tokens:
- **npm**: Configure trusted publisher in package settings
- **PyPI**: Configure trusted publisher in project settings

## Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
