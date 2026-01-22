---
layout: code-full
---

# Decision Matrix – Language & Tooling

| Area | Choice | Alternative | Why |
|------|--------|-------------|-----|
| Node version | **22 LTS** | 20, 18 | ES2024, performance |
| Python version | **3.12** | 3.11 | Faster startup, type syntax |
| Python tooling | **uv** | pip, poetry, pipenv | Detailed later |
| Python linter | **ruff** | flake8, pylint | All-in-one, Rust speed |
| Node pkg manager | **npm** | yarn, pnpm | Ecosystem stability |
| Semantic release | **Node-based** | Python-semantic-release | One tool for both |

<!--
Node 22 gives ES2024 features, Python 3.12 has faster startup, uv is 10-100x faster than pip. ruff replaces black, flake8, and isort with one fast Rust tool. npm was chosen over pnpm/yarn for ecosystem stability and widest compatibility.
-->

---
layout: code-full
---

# Decision Matrix – Security & Conventions

| Area | Choice | Alternative | Why |
|------|--------|-------------|-----|
| Auth default | **OIDC** | Tokens | No secret rotation |
| Audit level | **moderate** | low, high | Pragmatic security |
| Action versions | **SHA pinning** | @v4 tags | Supply chain security |
| Commit format | **Conventional** | Free-form | Automated changelogs |
| Commit limits | **150/200 chars** | 50-72/100 | Tool-generated messages |
| Subject case | **pascal OK** | lowercase only | Flexibility |
| Branch strategy | **main=beta** | main=stable | Continuous integration |

<!--
OIDC eliminates secret rotation. SHA pinning prevents supply chain attacks from compromised tags. Commit limits are relaxed to 150 chars header and 200 body to accommodate tool-generated messages. The main=beta strategy allows continuous integration while release branch stays production-ready. Let's dive deeper into why we chose uv for Python.
-->
