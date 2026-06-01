# Python Lesson 07 — Classes and OOP

**Time:** 4–5 hours  
**Prerequisite:** [Lesson 06](06-dictionaries-and-files.md)

## 1. Defining a class

```python
class Vehicle:
    def __init__(self, vehicle_id, speed=0.0):
        self.vehicle_id = vehicle_id
        self.speed = speed

    def accelerate(self, amount):
        self.speed += amount

    def __repr__(self):
        return f"Vehicle({self.vehicle_id}, speed={self.speed})"

v = Vehicle("TS-001", 10)
v.accelerate(5)
print(v)
```

## 2. Dataclass (clean data objects)

```python
from dataclasses import dataclass

@dataclass
class GPSPoint:
    lat: float
    lon: float

p = GPSPoint(37.38, -122.08)
```

## 3. Methods vs attributes

- **Attributes** — data (`self.speed`)
- **Methods** — functions on the object (`accelerate`)

## Example: driving sample

```python
class DrivingSample:
    def __init__(self, timestamp, speed, steering):
        self.timestamp = timestamp
        self.speed = speed
        self.steering = steering

    def is_fast(self, limit=55):
        return self.speed > limit
```

---

## Exercises

Folder: `~/python-hero/practice/python/lesson07/`

### Exercise 1 — BankAccount

Class with `balance` starting at 0, methods `deposit(amount)` and `withdraw(amount)` (no negative balance).

**Check:** [Answer](../answers/07-classes-and-oop-answers.md#exercise-1--bankaccount)

### Exercise 2 — Rectangle class

Attributes `width`, `height`; methods `area()` and `perimeter()`.

**Check:** [Answer](../answers/07-classes-and-oop-answers.md#exercise-2--rectangle-class)

### Exercise 3 — Fleet

Class `Fleet` holding a list of `Vehicle` ids. Methods `add(id)` and `count()`.

**Check:** [Answer](../answers/07-classes-and-oop-answers.md#exercise-3--fleet)

### Exercise 4 — dataclass Point

Use `@dataclass` for `Point(x, y)` with method `distance_to_origin()`.

**Check:** [Answer](../answers/07-classes-and-oop-answers.md#exercise-4--dataclass-point)

---

[All answers](../answers/07-classes-and-oop-answers.md) · **Next:** [Lesson 08](08-modules-and-mini-project.md)
