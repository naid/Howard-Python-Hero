# Answers — Python Lesson 05: Lists and loops

## Exercise 1 — List stats

```python
data = [4, 7, 2, 9, 5]
print(min(data))
print(max(data))
print(sum(data))
print(sum(data) / len(data))
```

Output: `2`, `9`, `27`, `5.4`

---

## Exercise 2 — Filter positives

```python
def only_positive(numbers):
    return [n for n in numbers if n > 0]

print(only_positive([-1, 2, 0, 3]))  # [2, 3]
```

---

## Exercise 3 — Reverse list

```python
def reverse_list(items):
    result = []
    for i in range(len(items) - 1, -1, -1):
        result.append(items[i])
    return result

print(reverse_list([1, 2, 3]))  # [3, 2, 1]
```

---

## Exercise 4 — Driving log

```python
speeds = [0, 15, 40, 65, 30]
count = sum(1 for s in speeds if s > 35)
print(count)  # 2
```

---

## Exercise 5 — Nested averages

```python
trips = [[30, 40], [50, 60, 70]]
all_speeds = []
for trip in trips:
    avg = sum(trip) / len(trip)
    print(f"Trip avg: {avg}")
    all_speeds.extend(trip)
print(f"Overall: {sum(all_speeds) / len(all_speeds)}")
```

Output: `Trip avg: 35.0`, `Trip avg: 60.0`, `Overall: 48.333...`

---

[← Back to Lesson 05](../lessons/05-lists-and-loops.md)
