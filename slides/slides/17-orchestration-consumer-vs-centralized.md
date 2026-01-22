---
layout: two-cols-header
---

# Orchestration: Consumer vs Centralized

::left::

## Consumer Orchestrates

```yaml
jobs:
  ci:
    uses: shared-config/.../ci.yml@main
  docs:
    needs: ci
    uses: shared-config/.../docs.yml@main
  release:
    needs: [ci, docs]
    uses: shared-config/.../release.yml@main
```

<v-clicks>

- Each repo defines its own job dependencies
- Gate logic scattered across 30+ AlgoKit repos
- Adding a step means updating every consumer
- Drift in `needs:` chains and conditions

</v-clicks>

::right::

## Centralized Orchestrates

```yaml
jobs:
  on-merge:
    uses: shared-config/.../on-merge-main.yml@main
    with:
      project-type: node
    secrets: inherit
```

<v-clicks>

- One line invokes the entire pipeline
- Gate logic lives in shared-config
- Add security scanning? Update one file
- Consistent sequencing everywhere

</v-clicks>

<!--
AlgoKit maintains 30+ SDK and tooling repos that should all behave identically: same beta/stable release strategy, same CI gates, same DevPortal publishing for Kapa AI. With consumer orchestration, every repo duplicates the pipeline logic and drifts independently. With centralized orchestration, the strategy is codified once. When we decide docs must pass before release, or add security scanning, it's one PR, not thirty. At this scale, consistency beats flexibility.
-->
