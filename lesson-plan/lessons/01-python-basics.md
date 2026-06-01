# Lesson 01 — Python basics

**Time:** 2 weeks (~20 hours)  
**Prerequisite:** OS setup + Lesson 00

## Learning objectives

- Variables, types, operators
- `if`, `for`, `while`
- Functions and docstrings
- Lists, dicts, tuples, sets

Maps to job requirement: **Strong Python experience**

## 1. Variables and types

```python
speed_mph = 65.0          # float
num_cameras = 8           # int
vehicle_id = "TS-001"     # str
is_autonomous = True      # bool

print(type(speed_mph))
```

## 2. Operators and strings

```python
distance_km = speed_mph * 1.60934 * 2  # hours implied
message = f"Vehicle {vehicle_id} traveled ~{distance_km:.1f} km"
print(message)
```

## 3. Conditionals

```python
def safety_alert(speed, limit=35):
    if speed > limit:
        return "SLOW DOWN"
    elif speed < 0:
        return "INVALID"
    else:
        return "OK"
```

## 4. Loops

```python
sensor_readings = [0.2, 0.5, 0.9, 0.4]
above_threshold = []
for r in sensor_readings:
    if r > 0.45:
        above_threshold.append(r)

# List comprehension (prefer when readable)
above_threshold = [r for r in sensor_readings if r > 0.45]
```

## 5. Functions

```python
def mean(values):
    """Return arithmetic mean of a non-empty list."""
    if not values:
        raise ValueError("values must not be empty")
    return sum(values) / len(values)
```

## 6. Core collections

```python
# dict — key/value (e.g. sensor name -> reading)
readings = {"lidar": 1.2, "radar": 0.8, "camera": 0.95}

# tuple — immutable (e.g. lat, lon)
gps = (37.3861, -122.0839)

# set — unique items
unique_ids = {101, 102, 101}  # {101, 102}
```

## 7. Files (preview)

```python
with open("log.txt", "w") as f:
    f.write("session start\n")
```

Full file handling in Lesson 02.

## Exercises

1. **Temperature converter** — Celsius ↔ Fahrenheit functions.
2. **Driving log** — List of `(time, speed)` tuples; print max speed and average.
3. **Word count** — Read a `.txt` file (you create it); count lines and words.
4. **FizzBuzz** — 1–100: divisible by 3 → "Fizz", by 5 → "Buzz", both → "FizzBuzz".

## Mini-project: trip statistics

Script `trip_stats.py`:

- Input: list of speeds (or read from file)
- Output: min, max, mean, count above speed limit

Save under `~/python-hero/projects/lesson01/`.

## Checklist

- [ ] Can write functions with type hints (optional: `def f(x: float) -> float`)
- [ ] Comfortable with `for` and list comprehensions
- [ ] Completed mini-project

**Next:** [Lesson 02 — Python intermediate](02-python-intermediate.md)
