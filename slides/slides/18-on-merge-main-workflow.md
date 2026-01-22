---
layout: two-cols-header
---

# On-Merge-Main Workflow

::left::

### Purpose

Chain CI → Docs → Release (beta) on every merge to `main`.

### Inputs (minimal)

- `project-type`: `node` or `python`
- `node-version` / `python-version`
- `working-directory` (monorepos)
- `skip-docs`: opt-out if needed

### Hardcoded by design

- `publish: true`: always publish
- `publish-devportal: true`: feed Kapa AI
- No back-merge (betas stay on main)

::right::

```yaml
name: On Merge to Main

on:
  push:
    branches: [main]

jobs:
  pipeline:
    uses: shared-config/.../on-merge-main.yml@main
    with:
      project-type: node
    secrets: inherit
```

<div class="mt-4">

**Output:** `1.2.0-beta.1` (prerelease)

</div>

<!--
This is the main branch orchestration. Minimal inputs because the workflow owns the release strategy. Publish always happens, docs always publish to both targets. The beta suffix comes from semantic-release branch configuration, not the workflow. Consumers just say "node" and get consistent CI, docs, and beta releases.
-->
