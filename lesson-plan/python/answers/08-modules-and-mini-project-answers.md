# Answers — Python Lesson 08: Modules and mini-project

## Exercise 1 — stats module

`stats.py`:

```python
def mean(values):
    return sum(values) / len(values)

def min_value(values):
    return min(values)

def max_value(values):
    return max(values)
```

`main.py`:

```python
from stats import mean, min_value, max_value

data = [5, 1, 9, 3]
print(mean(data))
print(min_value(data))
print(max_value(data))
```

---

## Exercise 2 — utils.format

`utils/format.py`:

```python
def format_mph(speed):
    return f"{speed:.1f} mph"
```

`main.py`:

```python
from utils.format import format_mph

print(format_mph(60))
```

Run from parent folder that contains `utils/` as a package, or add empty `utils/__init__.py`.

`utils/__init__.py` can be empty.

---

## Exercise 3 — Test stats manually

```python
from stats import mean

assert mean([2, 4]) == 3.0
print("Tests passed")
```

---

## Mini-project — Trip report

`speeds.txt`:

```
30
45
60
25
```

`stats.py`:

```python
def mean(values):
    return sum(values) / len(values)
```

`trip_stats.py`:

```python
class TripStats:
    def __init__(self, speeds):
        self.speeds = speeds

    def summary(self):
        return {
            "count": len(self.speeds),
            "min": min(self.speeds),
            "max": max(self.speeds),
            "avg": mean(self.speeds),
        }
```

`main.py`:

```python
from stats import mean
from trip_stats import TripStats

def load_speeds(path):
    speeds = []
    with open(path) as f:
        for line in f:
            speeds.append(float(line.strip()))
    return speeds

speeds = load_speeds("speeds.txt")
report = TripStats(speeds).summary()
for key, value in report.items():
    print(f"{key}: {value}")
```

Expected: count 4, min 25, max 60, avg 40.0

---

[← Back to Lesson 08](../lessons/08-modules-and-mini-project.md)
