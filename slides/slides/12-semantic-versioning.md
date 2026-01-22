---
layout: code-full
---

# Semantic Versioning

| Commit Type | Version Bump | Example |
|-------------|--------------|---------|
| `feat` | **Minor** (1.0.0 → 1.1.0) | New feature |
| `fix` | **Patch** (1.0.0 → 1.0.1) | Bug fix |
| `feat!` or `BREAKING CHANGE:` | **Major** (1.0.0 → 2.0.0) | Breaking API change |
| `perf`, `build`, `chore` | **Patch** | Performance, build, maintenance |
| `docs`, `style`, `refactor`, `test`, `ci` | No release | Non-user-facing |

**Breaking Changes:** `feat!: message` or footer `BREAKING CHANGE: description`

<!--
This table shows why Conventional Commits matter: feat bumps minor, fix bumps patch, breaking changes bump major. The non-user-facing types like docs, style, refactor, test, and ci don't create releases because they don't affect the published package. Use this as a reference when deciding commit type; the exclamation mark like feat! is shorthand for breaking changes.
-->
