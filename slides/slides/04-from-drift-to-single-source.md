---
layout: two-cols-header
---

# From Drift to Single Source

::left::

## Today

<ul>
  <li v-click="2"><strong>Copy-paste CI/CD</strong> across repos</li>
  <li v-click="3"><strong>Drift</strong> in workflow configurations</li>
  <li v-click="4"><strong>Maintenance burden</strong> multiplied by N repos</li>
  <li v-click="5"><strong>Inconsistent</strong> tooling versions</li>
  <li v-click="6"><strong>Security updates</strong> require touching every repo</li>
</ul>

::right::

<div v-click="1">

## With shared-config

</div>

<ul>
  <li v-click="2"><strong>Single source of truth</strong> for workflows</li>
  <li v-click="3"><strong>Centralized updates</strong> propagate everywhere</li>
  <li v-click="4"><strong>Consistent</strong> Node 22 / Python 3.12</li>
  <li v-click="5"><strong>Opinionated defaults</strong> with escape hatches</li>
  <li v-click="6"><strong>DRY principle</strong> for CI/CD</li>
</ul>

<!--
Each click reveals a problem/solution pair. The core value proposition is security updates in one place versus touching N repos. The "maintenance multiplied by N" pain is real. When teams patched log4j-style issues, centralized teams finished in minutes while decentralized teams took weeks. Now let's see the architecture that makes this possible.
-->
