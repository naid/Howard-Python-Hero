# Python Lesson 08 — Modules and mini-project

**Time:** 5–6 hours  
**Prerequisite:** [Lesson 07](07-classes-and-oop.md)

## 1. Importing modules

```python
import math
print(math.sqrt(16))

from math import pi
print(pi)
```

## 2. Your own module

Project layout:

```
lesson08/
├── main.py
└── stats.py
```

`stats.py`:

```python
def mean(values):
    if not values:
        raise ValueError("empty")
    return sum(values) / len(values)
```

`main.py`:

```python
from stats import mean

print(mean([1, 2, 3, 4]))
```

Run from `lesson08/`:

```bash
source ~/python-hero/venv/bin/activate
cd ~/python-hero/practice/python/lesson08
python main.py
```

## 3. `if __name__ == "__main__"`

```python
# stats.py
def mean(values):
    return sum(values) / len(values)

if __name__ == "__main__":
    print(mean([10, 20, 30]))
```

## 4. Packages (preview)

```
fleet/
├── __init__.py
├── models.py
└── main.py
```

---

## Exercises

Folder: `~/python-hero/practice/python/lesson08/`

Activate your venv before running scripts:

```bash
source ~/python-hero/venv/bin/activate
```

### Exercise 1 — stats module

Create `stats.py` with `mean`, `min_value`, `max_value`. `main.py` imports and prints stats for `[5, 1, 9, 3]`.

**Check:** [Answer](../answers/08-modules-and-mini-project-answers.md#exercise-1--stats-module)

### Exercise 2 — utils.format

Module `utils/format.py` with `format_mph(speed)` → `"60.0 mph"`. Import from `main.py`.

**Check:** [Answer](../answers/08-modules-and-mini-project-answers.md#exercise-2--utilsformat)

### Exercise 3 — Test stats manually

In `main.py`, assert `mean([2, 4]) == 3.0` and print `"Tests passed"`.

**Check:** [Answer](../answers/08-modules-and-mini-project-answers.md#exercise-3--test-stats-manually)

---

## Mini-project: Trip report

Build `trip_report/`:

- Read `speeds.txt` (one speed per line)
- Print count, min, max, average
- Use at least one class (`TripStats`) and one module (`stats.py`)

**Check:** [Mini-project answer](../answers/08-modules-and-mini-project-answers.md#mini-project--trip-report)

---

[All answers](../answers/08-modules-and-mini-project-answers.md) · **Next:** [PyTorch track](../../pytorch/README.md)
