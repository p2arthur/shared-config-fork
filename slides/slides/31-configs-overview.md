---
layout: code-full
---

# Configs Overview

### Install from npm

```bash
npm install -D @algokit/shared-config
```

<div>

### Package Exports

```json
{
  "exports": {
    "./eslint": "./configs/eslint.config.mjs",
    "./prettier": "./configs/prettier.config.cjs"
  }
}
```

</div>

<div>

### Usage in your project

```js
// eslint.config.mjs
export { default } from '@algokit/shared-config/eslint'

// prettier.config.cjs
module.exports = require('@algokit/shared-config/prettier')
```

</div>

<!--
One npm install, two re-exports. Your local eslint.config.mjs and prettier.config.cjs just re-export from the package. If you need to override something, you can spread the config and add your own rules. The escape hatch is always there. Let's look at the specific decisions we made for ESLint configuration.
-->
