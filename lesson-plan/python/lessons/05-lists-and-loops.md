# Python Lesson 05 — Lists and loops

**Time:** 4 hours  
**Prerequisite:** [Lesson 04](04-functions.md)

## 1. Creating lists

```python
speeds = [0, 15, 30, 45, 60]
mixed = [1, "two", 3.0]
empty = []
```

## 2. Indexing and slicing

```python
speeds = [10, 20, 30, 40]
print(speeds[0], speeds[-1])   # 10, 40
print(speeds[1:3])            # [20, 30]
```

## 3. List methods

```python
nums = [3, 1, 2]
nums.append(4)
nums.sort()
print(nums)  # [1, 2, 3, 4]
```

## 4. Looping

```python
for s in speeds:
    print(s)

for i, s in enumerate(speeds):
    print(i, s)
```

## 5. List comprehensions

```python
speeds = [10, 55, 70, 25]
fast = [s for s in speeds if s > 50]
```

## Example: statistics

```python
def average(values):
    return sum(values) / len(values)

speeds = [30, 45, 60, 25]
print(f"Avg: {average(speeds):.1f}")
print(f"Max: {max(speeds)}")
```

---

## Exercises

Folder: `~/python-hero/practice/python/lesson05/`

### Exercise 1 — List stats

Given `data = [4, 7, 2, 9, 5]`, print min, max, sum, and average (use functions).

**Check:** [Answer](../answers/05-lists-and-loops-answers.md#exercise-1--list-stats)

### Exercise 2 — Filter positives

Write `only_positive(numbers)` returning a new list with values `> 0`.

**Check:** [Answer](../answers/05-lists-and-loops-answers.md#exercise-2--filter-positives)

### Exercise 3 — Reverse list

Write `reverse_list(items)` **without** using `reversed()` or `.reverse()` — use a loop.

**Check:** [Answer](../answers/05-lists-and-loops-answers.md#exercise-3--reverse-list)

### Exercise 4 — Driving log

List of speeds `[0, 15, 40, 65, 30]`. Print how many are above 35 mph (use a loop or comprehension).

**Check:** [Answer](../answers/05-lists-and-loops-answers.md#exercise-4--driving-log)

### Exercise 5 — Nested averages

`trips = [[30, 40], [50, 60, 70]]` — print average speed per trip, then overall average.

**Check:** [Answer](../answers/05-lists-and-loops-answers.md#exercise-5--nested-averages)

---

[All answers](../answers/05-lists-and-loops-answers.md) · **Next:** [Lesson 06](06-dictionaries-and-files.md)
