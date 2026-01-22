---
layout: two-cols-header
---

# GITHUB_TOKEN vs GitHub App

::left::

### The Problem in `release.yml`

**Back-merge step needs to:**
- Push merge commit to protected `main` branch
- Trigger downstream workflows (e.g., deploy after release)

**GITHUB_TOKEN fails because:**
1. Can't push to protected branches (no bypass mechanism)
2. Won't trigger other workflows (intentional loop prevention)

**Error you'll see:**
```
refusing to allow GitHub App to push
to protected branch
```

::right::

### The Solution

```yaml
# release.yml (lines 158-163)
- name: Generate Bot Token
  id: bot-token
  uses: .../bot-token@main
  with:
    app-id: ${{ secrets.BOT_ID }}
    private-key: ${{ secrets.BOT_SK }}

# release.yml (line 203)
- uses: actions/checkout@v6
  with:
    token: ${{ steps.bot-token.outputs.token }}
```

**Why this works:**
- App added to ruleset bypass actors → can push to `main`
- App token triggers downstream workflows
- Rulesets (not classic protection) allow bypass actors

<!--
The release workflow needs to back-merge into main, but GITHUB_TOKEN can't push to protected branches and won't trigger downstream workflows. GitHub Apps solve both problems: add the App as a ruleset bypass actor to push to main, and App-generated tokens trigger workflows unlike GITHUB_TOKEN. Note that classic branch protection has no bypass option at all - you need rulesets, the modern replacement. PATs are not optimal: they're long-lived, org-wide, and lack audit trails, while GitHub Apps are scoped to specific repos and permissions.
-->
