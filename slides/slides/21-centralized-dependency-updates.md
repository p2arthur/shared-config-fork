---
layout: two-cols-header
---

# Centralized Dependency Updates

::left::

### The Problem

- Each repo maintains its own action versions
- `actions/checkout@v3` → `v4` across 40 repos
- Security patches require manual bumps everywhere
- Stale dependencies = stale vulnerabilities

### The Solution

Dependabot runs **once** in shared-config, updating:
- GitHub Actions (`actions/checkout`, `actions/setup-node`)
- npm packages in composite actions
- All consumers inherit updates automatically

::right::

```yaml
# .github/dependabot.yml (in shared-config)
version: 2
updates:
  - package-ecosystem: "github-actions"
    directory: "/"
    schedule:
      interval: "weekly"
    commit-message:
      prefix: "chore(deps)"

  - package-ecosystem: "npm"
    directory: "/actions/release/node"
    schedule:
      interval: "weekly"
```

<div class="mt-4 text-sm">

**Result:** One PR updates all consumers, zero effort per repo

</div>

<!--
Dependabot in shared-config is force multiplication. When actions/checkout releases v5, one automated PR here updates every consumer repo instantly. Compare that to opening 40 PRs manually. Security patches for transitive dependencies in our composite actions flow downstream automatically. The key insight: consumers pinning to @main get continuous updates; those pinning to tags get stability with explicit upgrade paths.
-->
