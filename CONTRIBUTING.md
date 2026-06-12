# Contributing to topological-qubit-library

Welcome! Contributions include new anyon models, braiding compilers, code implementations, algorithms, and simulation improvements.

## Getting Started

```bash
git clone https://github.com/<your-fork>/topological-qubit-library.git
cd topological-qubit-library
python -m venv .venv && source .venv/bin/activate
pip install -e ".[dev]"
pre-commit install
```

## Standards

- Python 3.11+, type annotations, `black` + `ruff` + `mypy --strict`.
- All anyon models and codes must cite primary literature (DOI required in module docstring).
- Braid group implementations must pass algebraic identity tests in `tests/braid_validation/`.

## Testing

```bash
pytest tests/ -v --cov=tql --cov-report=term-missing
```

## Pull Request Process

1. CI passes, one maintainer review (new anyon models need two reviewers), update `CHANGELOG.md`, squash-merge.
