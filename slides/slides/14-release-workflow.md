---
layout: two-cols-header
---

# Release Workflow

::left::

### Purpose

Version, tag, and publish releases.

### Inputs

- `project-type`: `node` or `python`
- `publish`: enable registry publish
- `use-oidc`: recommended
- `back-merge`: `release` → `main`
- `build-command`: custom build cmd
- Optional: `dry-run`, `config-path`, `dist-directory`, `working-directory`

::right::

```yaml
jobs:
  release:
    uses: mrcointreau/shared-config/.github/workflows/release.yml@main
    with:
      project-type: node
      publish: true
      # use-oidc: true  # default, recommended
      # dry-run: false  # default
      # back-merge: false  # default
    secrets:
      BOT_ID: ${{ secrets.BOT_ID }}
      BOT_SK: ${{ secrets.BOT_SK }}
```

<div>

**Atomic:** if `publish: true` fails, no release created

**Required auth:** GitHub App token + OIDC (or npm/PyPI token)

</div>

<!--
Atomic publish means no Git tag gets created if registry publish fails. Ever had a GitHub release that points to a version that never made it to npm? This eliminates that failure mode entirely. Here's the flow diagram showing the complete release process including back-merge.
-->
