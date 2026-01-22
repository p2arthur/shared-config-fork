---
layout: code-full
---

# Release Strategy

### Trunk-Based Development

| Branch | Role | Version |
|--------|------|---------|
| `main` | Development trunk (beta) | `1.2.0-beta.1` |
| `release` | Stable releases only | `1.2.0` |

### Flow

- All PRs merge to `main` → triggers beta release automatically
- Merge `main` → `release` for stable release
- Run release workflow manually on `release` branch

<div>

### Back-merge (optional)

Merging `release` → `main` after stable release is **optional**. If disabled, `main` stays pure beta (no stable versions in history). Enable only if you want `main` to track stable releases too.

</div>

<!--
We use trunk-based development where main produces beta releases and the release branch produces stable versions. Back-merge is optional. If disabled, main stays pure beta with no stable version numbers in its history. Let's see how the release workflow implements this branching strategy.
-->
