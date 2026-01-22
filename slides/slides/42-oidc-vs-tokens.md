---
layout: two-cols-header
---

# OIDC vs Tokens

::left::

### Purpose

Choose the safest publishing auth method.

### Recommendation

Use OIDC by default; tokens are a fallback.

### When tokens make sense

- npm org lacks OIDC support
- Self-hosted runners without OIDC
- Legacy infra with rotation

::right::

| Aspect | OIDC Trusted Publishing | Token-based |
|--------|------------------------|-------------|
| **Setup** | Configure in npm/PyPI settings | Generate & store secret |
| **Security** | No long-lived secrets | Token can leak |
| **Rotation** | Automatic | Manual rotation needed |
| **Provenance** | Signed attestations | None |
| **Recommendation** | **Default, preferred** | Legacy fallback |

<!--
OIDC trusted publishing eliminates secret rotation and provides signed provenance attestations. Tokens are a fallback for legacy setups. New projects should always use OIDC. Tokens only make sense for orgs without OIDC support, self-hosted runners, or existing rotation workflows. Let's first see how to configure trusted publishers in npm and PyPI.
-->
