---
layout: two-cols-header
---

# CI Actions Comparison

::left::

### Purpose

Compare the CI action steps for Node and Python.

### Outputs

`audit-outcome`, `lint-outcome`, `test-outcome`, `build-outcome`

### Audit-level limitation

`npm audit --audit-level` allows filtering by severity (low/moderate/high/critical). `pip-audit` only has `--strict` (fail on any vuln). **No granular threshold for Python.**

::right::

| Aspect | Node (`ci/node`) | Python (`ci/python`) |
|--------|------------------|---------------------|
| **Setup** | `setup-node` | `setup-python` + `setup-uv` |
| **Install** | `npm ci` | `uv sync` |
| **Audit** | `npm audit --audit-level` | `uvx pip-audit --strict` |
| **Lint** | `npm run lint` | `uv run ruff check .` |
| **Test** | `npm test` | `uv run pytest` |
| **Build** | `npm run build` | `uv build` |

<!--
Node uses npm commands, Python uses uv equivalents. The parallel structure keeps the mental model simple. We chose uv over pip/poetry because it's 10-100x faster. Note that pip-audit lacks audit-level filtering unlike npm audit; it's all-or-nothing with --strict. Now let's look at the release actions and how they integrate with semantic-release.
-->
