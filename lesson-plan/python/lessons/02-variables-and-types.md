# Python Lesson 02 — Variables and types

**Time:** 3–4 hours  
**Prerequisite:** [Lesson 01](01-first-program.md)

## 1. Variables

```python
speed = 55
vehicle_id = "CAR-42"
is_moving = True
```

## 2. Types

```python
print(type(55))        # <class 'int'>
print(type(55.0))      # <class 'float'>
print(type("hi"))      # <class 'str'>
print(type(True))      # <class 'bool'>
```

## 3. Converting types

```python
age_str = input("Age? ")
age = int(age_str)
height = float("1.75")
```

## 4. f-strings

```python
speed = 60
print(f"Speed is {speed} mph")
print(f"Double speed is {speed * 2}")
```

## 5. Operators

```python
a, b = 10, 3
print(a + b, a - b, a * b, a / b, a // b, a % b, a ** b)
```

| Operator | Meaning |
|----------|---------|
| `//` | Integer division |
| `%` | Remainder |
| `**` | Power |

## Example: trip distance

```python
speed_mph = 60.0
hours = 2.5
distance = speed_mph * hours
print(f"Drove {distance} miles")
```

---

## Exercises

Folder: `~/python-hero/practice/python/lesson02/`

### Exercise 1 — Celsius to Fahrenheit

Write `celsius_to_fahrenheit.py`. Ask for Celsius, print Fahrenheit using `F = C * 9/5 + 32` (round to 1 decimal).

**Check:** [Answer](../answers/02-variables-and-types-answers.md#exercise-1--celsius-to-fahrenheit)

### Exercise 2 — Rectangle area

Store `width = 4.5` and `height = 3.2`. Print area and perimeter.

**Check:** [Answer](../answers/02-variables-and-types-answers.md#exercise-2--rectangle-area)

### Exercise 3 — Type detective

Create variables: one `int`, one `float`, one `str`, one `bool`. Print each value and its `type(...)`.

**Check:** [Answer](../answers/02-variables-and-types-answers.md#exercise-3--type-detective)

### Exercise 4 — Seconds to minutes

Ask for total seconds (integer). Print minutes and remaining seconds (e.g. 125 → 2 min 5 sec).

**Check:** [Answer](../answers/02-variables-and-types-answers.md#exercise-4--seconds-to-minutes)

---

[All answers](../answers/02-variables-and-types-answers.md) · **Next:** [Lesson 03](03-control-flow.md)
