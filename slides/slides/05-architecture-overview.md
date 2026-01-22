---
layout: diagram-tight
---

# Architecture Overview

<div>

```mermaid {scale: 0.49}
flowchart TB
    subgraph shared-config["shared-config"]
        subgraph workflows["Reusable Workflows"]
            CI[ci.yml]
            PR[pr.yml]
            Release[release.yml]
            Docs[docs.yml]
        end
        subgraph actions["Composite Actions"]
            subgraph ci-actions["CI"]
                CINode[ci/node]
                CIPython[ci/python]
            end
            subgraph rel-actions["Release"]
                RelNode[release/node]
                RelPython[release/python]
            end
            subgraph doc-actions["Docs"]
                DocsTypedoc[docs/typedoc]
                DocsSphinx[docs/sphinx]
                DocsPublish[docs/publish]
            end
            subgraph util-actions["Utils"]
                BotToken[bot-token]
                Commitlint[commitlint]
            end
        end
        subgraph configs["Shared Configs"]
            ESLint[eslint.config.mjs]
            Prettier[prettier.config.cjs]
        end
    end
    subgraph yourrepo["AlgoKit Repository"]
        YourCI[.github/workflows/ci.yml]
        YourPR[.github/workflows/pr.yml]
        YourRel[.github/workflows/release.yml]
    end
    YourCI -->|"uses:"| CI
    YourPR -->|"uses:"| PR
    YourRel -->|"uses:"| Release
    CI --> CINode
    CI --> CIPython
    PR --> Commitlint
    Release --> BotToken
    Release --> RelNode
    Release --> RelPython
    Docs --> DocsTypedoc
    Docs --> DocsSphinx
    Docs --> DocsPublish
    actions ~~~ configs
```

</div>

<!--
There are three distinct layers here. Workflows are the entry points that consuming repos call, actions are implementation details, and configs are npm packages. This separation of concerns makes maintenance tractable. You can change an action's internals without touching workflow signatures. Before we dive into each layer, let's discuss how to reference these, because branching strategy matters.
-->
