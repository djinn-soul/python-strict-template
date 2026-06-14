# CONTINUITY

## Snapshot
- 2026-06-14 [USER] Goal: add the public `cytoscnpy` Python package to this strict Python template's QA workflow.
- 2026-06-14 [USER] Goal update: configure CytoScnPy features properly, not just install the package.
- 2026-06-14 [TOOL] No repo-local `AGENTS.md` exists; global `~/.codex/AGENTS.md` was reviewed.
- 2026-06-14 [TOOL] No prior `CONTINUITY.md` existed before this task.
- 2026-06-14 [ASSUMPTION] `cytoscnpy` should be a default quality gate, not only an optional documented tool.

## Done (recent)
- 2026-06-14 [CODE] Added `cytoscnpy>=1.2.23` to the dev optional dependencies in `pyproject.toml`.
- 2026-06-14 [CODE] Added Poe task `cytoscnpy` and included it in `quality`.
- 2026-06-14 [CODE] Added `cytoscnpy` to local pre-commit hooks, GitHub Actions, GitLab CI, and README toolchain docs.
- 2026-06-14 [TOOL] Refreshed `uv.lock`, `requirements.txt`, and `requirements-dev.txt` with `uv lock` and `uv export`.
- 2026-06-14 [CODE] Added active `[tool.cytoscnpy]` settings for secrets, danger/taint, quality, tests, notebooks, clones, thresholds, exclusions, secret patterns, and taint sources/sinks/sanitizers.
- 2026-06-14 [CODE] Split dependency analysis into `poe cytoscnpy-deps`; default `poe cytoscnpy` runs the configured static/security/quality/clone/notebook gate.
- 2026-06-14 [CODE] Added CytoScnPy pre-commit hooks for main scan, dependency analysis, GitHub annotations, GitLab Code Quality, Markdown output, and SARIF output.

## Working set
- 2026-06-14 [CODE] `pyproject.toml`
- 2026-06-14 [CODE] `.pre-commit-config.yaml`
- 2026-06-14 [CODE] `.github/workflows/ci.yml`
- 2026-06-14 [CODE] `.gitlab-ci.yml`
- 2026-06-14 [CODE] `README.md`
- 2026-06-14 [CODE] `CONTINUITY.md`
- 2026-06-14 [CODE] `.gitignore`

## Decisions
- 2026-06-14 [ASSUMPTION] D001 ACTIVE: Run CytoScnPy with `--secrets --danger --quality` to match its public package usage and this template's safety focus.
- 2026-06-14 [CODE] D002 ACTIVE: Use active `[tool.cytoscnpy]` config for default scan features; keep dependency analysis as a separate task because generated dev exports create noisy unused-dependency reports.

## Open questions
- 2026-06-14 [USER] UNCONFIRMED: Whether `cytoscnpy` should remain in the default `quality` gate if it creates noisy findings on template/example code.

## Receipts
- 2026-06-14 [TOOL] Live PyPI check reported `cytoscnpy` version `1.2.23` and Python requirement `>=3.10`.
- 2026-06-14 [TOOL] `uv run python` parsed `pyproject.toml`; YAML parse check passed for `.pre-commit-config.yaml`, `.github/workflows/ci.yml`, and `.gitlab-ci.yml`.
- 2026-06-14 [TOOL] `uv run --extra dev` confirmed `cytoscnpy` entry point exists; `uv run poe cytoscnpy` exited 0 and reported analysis findings without failing the task.
- 2026-06-14 [TOOL] `uv run poe cytoscnpy`, `uv run poe cytoscnpy-github`, and `uv run poe cytoscnpy-gitlab` exited 0 with the active config.
- 2026-06-14 [TOOL] `uv run prek run cytoscnpy --all-files` and `uv run prek run cytoscnpy-github --all-files --hook-stage manual` passed.
