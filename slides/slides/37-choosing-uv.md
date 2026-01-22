---
layout: two-cols-header
---

# Choosing uv

::left::

### Key advantages

- 10–100x faster installs
- Single binary, no bootstrap
- `uv run` replaces venv activation
- `uvx` = npx for Python (run tools without install)
- `uv sync` = reproducible lockfile installs

### Astral

From the makers of **ruff** (linter/formatter). Astral is modernizing Python tooling with Rust-powered speed.

::right::

| Tool | Install Speed | Lock Support | Dependency Resolution |
|------|--------------|--------------|----------------------|
| **uv** | ~10-100x faster | Native | Fast SAT solver |
| pip | Baseline | pip-tools | Sequential |
| poetry | Slow | poetry.lock | Custom resolver |
| pipenv | Slow | Pipfile.lock | pip-based |

<!--
uv replaces pip, pip-tools, and virtualenv in a single binary. uvx is like npx - run Python CLI tools without installing them globally. uv sync ensures reproducible installs from lockfile, like npm ci. SAT solver = algorithm that finds package versions satisfying all dependency constraints at once, instead of pip's slower sequential approach. Astral, the company behind uv, also created ruff - the Rust-powered linter that replaces flake8, black, isort, and pylint. They're doing great work modernizing Python tooling.
-->
