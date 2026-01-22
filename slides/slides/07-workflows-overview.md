---
layout: code-full
---

# Workflows Overview

| Workflow | Purpose | Trigger |
|----------|---------|---------|
| **ci.yml** | Lint, test, build, audit | `workflow_call` |
| **pr.yml** | CI + commit linting | `workflow_call` |
| **release.yml** | Versioning & publish | `workflow_call`, `dispatch` |
| **docs.yml** | Generate & publish docs (Pages/DevPortal) | `workflow_call` |

All workflows require `project-type: node | python` input.

<!--
Four workflows cover the full development lifecycle: CI, PR, release, and docs. All require project-type as the primary input. This keeps the interface simple while supporting both ecosystems. Let's look at the CI workflow first since it's the foundation that others build on.
-->
