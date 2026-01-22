---
layout: two-cols-header
---

# Sample CI/CD Workflow

::left::

```yaml
jobs:
  ci:
    uses: mrcointreau/shared-config/.github/workflows/ci.yml@main
    with:
      project-type: node   # or python
  release:
    needs: ci
    uses: mrcointreau/shared-config/.github/workflows/release.yml@main
    with:
      project-type: node   # or python
      publish: true
    secrets:
      BOT_ID: ${{ secrets.BOT_ID }}
      BOT_SK: ${{ secrets.BOT_SK }}
```

::right::

### Node vs Python

- `project-type`: `node` or `python`
- `publish`: works for both
- Everything else is identical

<!--
Node and Python share identical workflow structure; only project-type differs. This is the abstraction paying off. Your workflow files look the same whether you're in TypeScript or Python, so context switching between repos becomes trivial. Next, let's look at orchestration strategies for managing when releases happen.
-->
