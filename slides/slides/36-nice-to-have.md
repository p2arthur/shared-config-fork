---
layout: code-full
---

# Nice to Have

### Git Hooks
Enforce linting/formatting locally before commits

- **Node:** `husky` + `lint-staged` — runs ESLint + Prettier on staged files
- **Python:** `pre-commit` — runs ruff format + ruff check on staged files

### Shared tsconfig

Centralized TypeScript configs that repositories can extend

```json
// In consumer repo's tsconfig.json
{
  "extends": "@algokit/shared-config/tsconfig/base.json"
}
```

- Base config with strict settings, path aliases, common compiler options
- Variant configs for different targets (Node, browser, library)

<!--
Git hooks catch issues before they reach CI. Shared tsconfig ensures consistent TypeScript settings across all repos: strict mode, module resolution, target versions. Repos extend the base and override only what's needed.
-->
