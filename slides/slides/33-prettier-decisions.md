---
layout: two-cols-header
---

# Prettier Decisions

::left::

### Purpose

Consistent formatting with minimal noise.

### Key settings

- Quotes: single
- Semicolons: off
- Print width: 140
- Trailing commas: all

### Rationale

- Cleaner diffs and modern readability
- Wide code fits modern screens

::right::

```js
module.exports = {
  singleQuote: true,
  jsxSingleQuote: false,
  semi: false,
  printWidth: 140,
  tabWidth: 2,
  trailingComma: 'all',
  arrowParens: 'always',
  endOfLine: 'lf',
}
```

Override any setting locally if needed.

<!--
Single quotes, no semicolons, 140 character width for modern screens, and trailing commas everywhere for cleaner git diffs. These are intentionally opinionated to end bikeshedding. 140 width matches modern widescreen monitors, not the 80 columns from the 1970s. Let's talk about the broader opinionated decisions beyond just linting.
-->
