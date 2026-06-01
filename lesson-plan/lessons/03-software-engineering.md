# Lesson 03 — Software engineering best practices

**Time:** 2 weeks (~15 hours)  
**Prerequisite:** [Lesson 02](02-python-intermediate.md)  
**Job alignment:** Production-quality, safety-critical software habits

## Learning objectives

- Git workflow
- Unit tests with `pytest`
- Linting and formatting (`ruff`, `black`)
- Project structure, logging, configuration

## 1. Git essentials

```bash
cd ~/python-hero/projects/lesson03
git init
git add .
git commit -m "Initial driving log parser"
```

Daily workflow:

```bash
git status
git diff
git add specific_file.py
git commit -m "Add validation for negative speeds"
```

Create a GitHub account; push repos (public portfolio).

## 2. Project layout

```
lesson03/
├── README.md
├── requirements.txt
├── pyproject.toml      # optional
├── src/
│   └── fleet/
│       ├── __init__.py
│       ├── models.py
│       └── stats.py
└── tests/
    └── test_stats.py
```

## 3. pytest

`tests/test_stats.py`:

```python
from fleet.stats import mean

def test_mean_simple():
    assert mean([1, 2, 3]) == 2

def test_mean_raises_on_empty():
    import pytest
    with pytest.raises(ValueError):
        mean([])
```

Run:

```bash
pip install pytest
pytest -v
```

## 4. Linting and formatting

```bash
pip install ruff black
ruff check src/
black src/ tests/
```

## 5. Logging (not print) for real systems

```python
import logging

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

logger.info("Loaded %d samples", len(samples))
```

## 6. Configuration

Use environment variables or a `config.yaml` for paths, batch size, learning rate — never hardcode secrets.

```python
import os
data_root = os.environ.get("DATA_ROOT", "/data/driving")
```

## 7. Code review checklist (Tesla-relevant)

- [ ] Inputs validated (speed ranges, file existence)
- [ ] Tests for edge cases
- [ ] Deterministic behavior or documented random seeds
- [ ] README explains how to reproduce results
- [ ] No secrets in git

## Exercises

1. Add tests until `pytest` covers core functions.
2. Add `ruff` to CI locally: script `scripts/check.sh` runs lint + test.
3. Write `CONTRIBUTING.md` with how to run tests.

## Mini-project

Refactor Lesson 02 parser into `src/fleet` package with tests and README.

**Next:** [Lesson 04 — NumPy, Pandas, data](04-numpy-pandas-data.md)
