---
layout: diagram-tight
---

# PR Workflow Flow

```mermaid {scale: 0.7}
flowchart LR
  subgraph inputs[Inputs]
    ci_inputs([CI inputs])
    scl([skip-commit-lint])
  end
  ci_inputs --> ci[ci job]
  ci -->|calls| ci_wf[ci.yml workflow]
  scl --> check{false?}
  check -->|yes| commitlint[commitlint action]
  check -->|no| skip[skip]
```

::caption::
CI inputs pass through to ci.yml; `ci` and `commit-lint` jobs run in parallel

<!--
CI and commit-lint run in parallel so developers get both results quickly; neither blocks the other. Note that fetch-depth: 0 is required for commitlint to see the full commit range. Now let's look at semantic versioning and how we handle beta versus stable releases.
-->
