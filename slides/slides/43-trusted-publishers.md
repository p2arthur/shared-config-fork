---
layout: two-cols-header
---

# Trusted Publishers

::left::

### What are Trusted Publishers?

A way for registries to trust GitHub Actions workflows **without storing secrets**.

### How to Configure

**npm:** Package Settings > Publishing access > Add trusted publisher
- Add repository owner, name, workflow file, environment (optional)

**PyPI:** Publishing > Add trusted publisher
- Add repository owner, name, workflow name, environment (optional)

::right::

| Aspect | npm | PyPI |
|--------|-----|------|
| **Available since** | GA July 2025 | 2023 |
| **Classic tokens** | Deprecated Dec 2025 | Still supported |
| **Config location** | Package settings | Project settings |
| **Environment** | Optional | Optional |
| **Auto-provenance** | Yes | Yes |

<!--
Trusted publishers replace classic tokens with OIDC identity verification. npm deprecated classic tokens in December 2025, making OIDC the standard. PyPI has supported trusted publishers since 2023. Both registries use the same underlying OIDC and Sigstore technology. Configuration is simple: add your repo and workflow to the registry settings, then ensure your workflow has id-token write permission. No more token rotation, no more leaked secrets.
-->
