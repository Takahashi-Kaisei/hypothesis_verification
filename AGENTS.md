# Repository Guidelines

## Project Structure & Module Organization
This repository is for testing hypotheses with code, notebooks, and reproducible experiments.

- `src/minimal_data_science/`: reusable Python code. Move notebook logic here once reused or tested.
- `notebooks/`: exploratory work and one-off verification. Keep notebooks focused on a single question.
- `tests/`: automated checks for logic moved into `src/`.
- `data/`: local datasets and intermediate outputs.
- `reports/`: exported figures, summaries, and experiment artifacts worth sharing.
- `docs/`, `references/`, `models/`, `modules/`: supporting notes, source material, trained assets, and utility code when needed.

## Build, Test, and Development Commands
- `uv sync`: install project and development dependencies from `pyproject.toml` / `uv.lock`.
- `make requirements`: same as `uv sync`.
- `make test`: run `pytest tests`.
- `make lint`: run `ruff format --check` and `ruff check`.
- `make format`: auto-fix lint issues and format code with Ruff.
- `make clean`: remove `__pycache__` and compiled Python files.

Use `uv run python ...` or `uv run pytest ...` to run inside the managed environment.

## Coding Style & Naming Conventions
Target Python `3.13` and keep code compatible with macOS/MPS and Linux/CUDA when possible.

- Follow Ruff defaults with `line-length = 99`.
- Use 4-space indentation.
- Prefer `snake_case` for functions, variables, notebook filenames, and test files.
- Keep modules small and hypothesis-oriented, for example `src/minimal_data_science/vector_stats.py`.
- Add short comments only where the reasoning is not obvious.

## Testing Guidelines
Use `pytest`. Every reusable function added under `src/` should get a matching test in `tests/` named `test_<behavior>.py`.

- Replace placeholder tests such as `tests/test_data.py` before merging.
- Prefer deterministic tests with small in-repo fixtures or synthetic data.
- For notebook work, promote critical logic into `src/` first, then test that code rather than the notebook itself.

## Commit & Pull Request Guidelines
The current Git history is minimal (`Initial commit`), so use short imperative commit messages such as `Add MPS availability check` or `Refactor experiment loader`.

- Keep each commit scoped to one hypothesis, fix, or refactor.
- In pull requests, state the question being tested, the approach, and the result.
- Link related issues or notes when available.
- Include screenshots or exported plots when notebook or report output changed materially.

## Experiment Workflow
Start in `notebooks/`, extract stable logic into `src/`, validate it in `tests/`, and save any shareable outputs in `reports/`. Optimize for reproducibility over convenience.
