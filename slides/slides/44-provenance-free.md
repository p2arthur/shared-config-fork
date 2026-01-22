---
layout: two-cols-header
---

# Provenance: Free with OIDC

::left::

### What Provenance Proves

- **Source commit** - Exact commit SHA that built the package
- **Workflow** - Which CI workflow ran the build
- **Runner** - GitHub-hosted runner environment
- **Build inputs** - Dependencies and build context

### Why It Matters

- **Supply chain security** - Verify package origin
- **Tamper detection** - Cryptographic proof of build
- **Audit trail** - Link releases to source code
- **Trust** - Users can verify before installing

::right::

### How It Works

```
Sigstore signs attestations automatically:

1. Workflow builds package
2. GitHub OIDC issues JWT
3. Sigstore signs attestation
4. Registry stores provenance
5. Users can verify origin
```

### Zero Configuration

- **No key management** - Sigstore handles signing
- **No secrets** - OIDC provides identity
- **Automatic** - Enabled with trusted publishing

### Verify Packages

```bash
npm audit signatures  # npm
```

<!--
Provenance is a cryptographic attestation that links a published package to its source code and build process. With OIDC trusted publishing, you get provenance for free. Sigstore signs the attestation using your workflow's OIDC identity. No key management, no secrets to rotate. Users can verify any package came from the claimed repository and workflow. This is critical for supply chain security. The verifiable link between source and package makes it much harder for attackers to inject malicious code.
-->
