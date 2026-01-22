---
layout: two-cols-header
---

# On-Merge-Release Workflow

::left::

### Purpose

Promote to stable release when merging `main` → `release`.

### Triggers

- **Push to `release`**: automatic on merge
- **Manual dispatch**: run from GitHub UI

### What it does

1. **Skips CI & Docs**: already passed on main
2. **Creates stable release**: `1.2.0`
3. **Publishes to registry**: npm or PyPI
4. **Back-merges to main**: sync version history

::right::

```yaml
name: On Merge to Release

on:
  push:
    branches: [release]

jobs:
  pipeline:
    uses: shared-config/.../on-merge-release.yml@main
    with:
      project-type: node
    secrets: inherit
```

<div class="mt-2 text-sm">

Or trigger manually via **Actions → Run workflow**

</div>

<!--
The release workflow supports both automatic and manual triggers. Automatic runs on merge to release branch. Manual dispatch lets you re-run a failed release or trigger from the GitHub UI without pushing. Either way, it skips CI and docs since they passed on main, creates a stable version, and back-merges.
-->
