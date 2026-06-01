# Python Lesson 04 — Functions

**Time:** 3–4 hours  
**Prerequisite:** [Lesson 03](03-control-flow.md)

## 1. Defining functions

```python
def greet(name):
    return f"Hello, {name}"

print(greet("Sam"))
```

## 2. Parameters and defaults

```python
def speed_alert(speed, limit=35):
    if speed > limit:
        return "Slow down"
    return "OK"
```

## 3. Multiple return values

```python
def min_max(values):
    return min(values), max(values)

lo, hi = min_max([3, 1, 9])
```

## 4. Docstrings

```python
def mean(values):
    """Return average of a non-empty list of numbers."""
    return sum(values) / len(values)
```

## 5. Scope

Variables inside a function are local unless declared `global` (avoid `global` until you need it).

## Example

```python
def mph_to_kph(mph):
    return mph * 1.60934

print(mph_to_kph(60))
```

---

## Exercises

Folder: `~/python-hero/practice/python/lesson04/`

### Exercise 1 — Rectangle functions

Write `area(width, height)` and `perimeter(width, height)`. Main code prints both for `w=5`, `h=3`.

**Check:** [Answer](../answers/04-functions-answers.md#exercise-1--rectangle-functions)

### Exercise 2 — is_prime

Write `is_prime(n)` returning `True` if `n` is prime (`n >= 2`). Test with 2, 9, 17.

**Check:** [Answer](../answers/04-functions-answers.md#exercise-2--is_prime)

### Exercise 3 — safe_divide

Write `safe_divide(a, b)` — return `a/b` if `b != 0`, else `None`.

**Check:** [Answer](../answers/04-functions-answers.md#exercise-3--safe_divide)

### Exercise 4 — word_count

Write `count_words(text)` that splits on spaces and returns word count.

**Check:** [Answer](../answers/04-functions-answers.md#exercise-4--word_count)

---

[All answers](../answers/04-functions-answers.md) · **Next:** [Lesson 05](05-lists-and-loops.md)
