---
layout: two-cols-header
---

# Actions Overview

::left::

### Purpose

Composable building blocks used by workflows.

### Groups

- `ci/`: node, python
- `release/`: node, python
- `publish/`: node, python
- `docs/`: typedoc, sphinx, publish, devportal-publish
- `utils/`: bot-token, commitlint

### Notes

Each action is single-purpose and reusable.

::right::

```mermaid {scale: 0.50}
flowchart TB
    subgraph row1[" "]
        direction LR
        subgraph ci["ci/"]
            node[node]
            python[python]
        end
        subgraph release["release/"]
            relnode[node]
            relpython[python]
        end
        subgraph publish["publish/"]
            pubnode[node]
            pubpython[python]
        end
    end
    subgraph row2[" "]
        direction LR
        subgraph docs["docs/"]
            typedoc[typedoc]
            sphinx[sphinx]
            pubdocs[publish]
            devportal[devportal-publish]
        end
        subgraph utils["utils/"]
            bottoken[bot-token]
            commitlint[commitlint]
        end
    end
    style row1 fill:none,stroke:none
    style row2 fill:none,stroke:none
```

<!--
Each action follows single-responsibility: one action does one thing well. There are five groups: ci/, release/, publish/, docs/, and utils/. Single-purpose actions are easier to test, maintain, and reuse, and you can mix and match them to build custom pipelines. Let's compare the Node and Python CI actions to see how they handle ecosystem differences.
-->
