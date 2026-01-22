---
layout: diagram-tight
---

# Release Workflow Flow

```mermaid {scale: 0.55}
flowchart LR
  subgraph inputs[Inputs]
    pt([project-type])
    pub([publish])
    bm([back-merge])
    dr([dry-run])
  end
  pt -->|node| rel_node[release/node]
  pt -->|python| rel_python[release/python]
  pub -.->|npm publish| rel_node
  pub -.->|pypi publish| rel_python
  rel_node --> merge_check
  rel_python --> merge_check
  bm --> merge_check{back-merge && !dry-run?}
  dr --> merge_check
  merge_check -->|yes| back_merge[back-merge job]
  merge_check -->|no| done[done]
```

::caption::
`publish` enables atomic registry publishing; `back-merge` only runs on real releases

<!--
The publish flag enables atomic registry publishing and OIDC controls authentication. Back-merge only runs on real releases, not dry-runs. The dry-run option lets you preview what would happen without side effects, which is useful for testing release configuration changes. Here's what the actual consumer workflow looks like; notice how simple it is.
-->
