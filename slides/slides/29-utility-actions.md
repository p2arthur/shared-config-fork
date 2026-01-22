---
layout: two-cols-header
---

# Utility Actions

::left::

### Purpose

Small helpers used across workflows.

### Actions

- `utils/bot-token`: GitHub App token for protected branches
- `utils/commitlint`: enforce Conventional Commits

### Notes

Commitlint uses a relaxed line-length config (150/200).

::right::

```yaml
# bot-token
- uses: mrcointreau/shared-config/actions/utils/bot-token@main
  with:
    app-id: ${{ secrets.BOT_ID }}
    private-key: ${{ secrets.BOT_SK }}

# commitlint
- uses: mrcointreau/shared-config/actions/utils/commitlint@main
  with:
    from: ${{ github.event.pull_request.base.sha }}
    to: ${{ github.event.pull_request.head.sha }}
```

<!--
bot-token generates GitHub App tokens for branch protection bypass and workflow triggering. GITHUB_TOKEN can't do either of those. That's why we need a GitHub App. commitlint enforces Conventional Commits with relaxed line limits at 150/200 because real commits often need detailed context. That wraps up actions. Now let's look at the shared configs distributed via npm.
-->
