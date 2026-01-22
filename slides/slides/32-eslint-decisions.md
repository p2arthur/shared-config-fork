---
layout: two-cols-header
---

# ESLint Decisions

::left::

### Purpose

TypeScript-first linting with pragmatic defaults.

### Key decisions

- Base: `typescript-eslint` recommended
- Unused imports: `eslint-plugin-unused-imports`
- Console: `warn` (catch debug leftovers)
- Strings: `prefer-template`

### Rationale

- Keeps strictness without blocking flow
- Auto-fixes for unused imports
- Compatible with Prettier (last in chain)

::right::

```js
export default defineConfig([
  eslint.configs.recommended,
  ...tseslint.configs.recommended,
  {
    plugins: { 'unused-imports': unusedImports },
    rules: {
      'no-console': 'warn',
      'unused-imports/no-unused-imports': 'error',
      'unused-imports/no-unused-vars': ['warn', {
        argsIgnorePattern: '^_', varsIgnorePattern: '^_',
        ignoreRestSiblings: true,
      }],
      'prefer-template': 'error',
    },
  },
  prettier,
])
```

<!--
This is a TypeScript-first config with the unused-imports plugin for auto-removal. console.log is a warning, not error, so it catches debug leftovers without blocking you. Prettier is last in the config chain to avoid conflicts, and the underscore-prefix convention for intentionally unused variables is respected. Now let's see the Prettier decisions, equally opinionated but overridable.
-->
