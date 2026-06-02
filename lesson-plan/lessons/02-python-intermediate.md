# Lesson 02 — Python intermediate

**Time:** 2 weeks (~20 hours)  
**Prerequisite:** [Lesson 01](01-python-basics.md)

## Learning objectives

- Classes and objects
- Modules and packages
- Exceptions and context managers
- Iterators, generators, `*args` / `**kwargs`

## 1. Classes

```python
class DrivingSample:
    def __init__(self, timestamp, speed, steering):
        self.timestamp = timestamp
        self.speed = speed
        self.steering = steering

    def is_stationary(self):
        return self.speed < 0.5

    def __repr__(self):
        return f"DrivingSample(t={self.timestamp}, v={self.speed})"
```

## 2. Dataclasses (cleaner data containers)

```python
from dataclasses import dataclass

@dataclass
class DrivingSample:
    timestamp: float
    speed: float
    steering: float
```

Install nothing extra — `dataclasses` is in the standard library (Python 3.7+).

## 3. Modules

File `utils/stats.py`:

```python
def mean(values):
    return sum(values) / len(values)
```

File `main.py`:

```python
from utils.stats import mean
```

Run from project root:

```bash
source ~/python-hero/venv/bin/activate
cd ~/python-hero/projects/lesson02   # or your project folder
python main.py
```

## 4. Exceptions

```python
try:
    data = load_json(path)
except FileNotFoundError:
    print(f"Missing file: {path}")
    raise
except json.JSONDecodeError as e:
    print(f"Invalid JSON: {e}")
```

**Rule:** Catch specific errors; avoid bare `except:`.

## 5. Generators (memory-efficient pipelines)

```python
def read_lines(path):
    with open(path) as f:
        for line in f:
            yield line.strip()
```

Used heavily in data loading for large driving logs.

## 6. Type hints and `mypy` (preview for Lesson 3)

```python
def clip(value: float, low: float, high: float) -> float:
    return max(low, min(high, value))
```

## Exercises

1. **Fleet class** — `Vehicle` with id, list of `DrivingSample`; method `average_speed()`.
2. **CSV reader** — Parse `timestamp,speed,steering` without pandas first.
3. **Generator** — Yield samples where `speed > 60` from a large file.
4. **Package layout** — `lesson02/` with `models/`, `io/`, `main.py`.

## Mini-project: driving log parser

- Input: CSV of driving data (create 1000+ rows synthetically if needed)
- Output: summary JSON (total samples, avg speed, % stationary)
- Use classes + generator + error handling for malformed rows

**Next:** [Lesson 03 — Software engineering](03-software-engineering.md)
