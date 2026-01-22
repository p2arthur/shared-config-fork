---
layout: two-cols-header
---

# Docs Workflow

::left::

### Purpose

Build docs and publish to **GitHub Pages** and **DevPortal** by default.

### Inputs

- `project-type`: `node` (TypeDoc) or `python` (Sphinx)
- `publish`: GitHub Pages (default: `true`)
- `publish-devportal`: DevPortal branch (default: `true`)
- `devportal-docs-branch`: default `docs-dist`
- `docs-path`, `working-directory`

::right::

```yaml
uses: mrcointreau/shared-config/.github/workflows/docs.yml@main
with:
  project-type: node
  # Both publish targets enabled by default
  # publish: true
  # publish-devportal: true
```

<div class="mt-4 text-sm">

**Opt-out** with `publish-devportal: false` if needed

</div>

<!--
TypeDoc handles Node projects, Sphinx handles Python. Documentation tooling matches the ecosystem. Both GitHub Pages and DevPortal publish by default. Opt-out rather than opt-in ensures documentation stays current everywhere. Next slide explains why DevPortal is so important.
-->
