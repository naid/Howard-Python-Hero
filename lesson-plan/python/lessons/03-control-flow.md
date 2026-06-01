# Python Lesson 03 — Control flow

**Time:** 3–4 hours  
**Prerequisite:** [Lesson 02](02-variables-and-types.md)

## 1. if / elif / else

```python
speed = 45
if speed > 65:
    print("Ticket risk")
elif speed > 35:
    print("OK in city")
else:
    print("Slow")
```

## 2. Comparison operators

`==`, `!=`, `<`, `>`, `<=`, `>=`

## 3. Logical operators

```python
is_raining = True
speed = 20
if is_raining and speed > 50:
    print("Dangerous")
```

`and`, `or`, `not`

## 4. while loop

```python
count = 3
while count > 0:
    print(count)
    count -= 1
```

## 5. for loop with range

```python
for i in range(5):      # 0, 1, 2, 3, 4
    print(i)

for n in range(1, 6):   # 1 .. 5
    print(n)
```

## Example: speed checker

```python
speed = int(input("Speed (mph): "))
if speed < 0:
    print("Invalid")
elif speed <= 25:
    print("School zone OK")
elif speed <= 55:
    print("City OK")
else:
    print("Highway range")
```

---

## Exercises

Folder: `~/python-hero/practice/python/lesson03/`

### Exercise 1 — Even or odd

Ask for an integer. Print whether it is even or odd. (Hint: `n % 2 == 0`)

**Check:** [Answer](../answers/03-control-flow-answers.md#exercise-1--even-or-odd)

### Exercise 2 — Grade letter

Score 0–100 → A (90+), B (80+), C (70+), D (60+), else F.

**Check:** [Answer](../answers/03-control-flow-answers.md#exercise-2--grade-letter)

### Exercise 3 — FizzBuzz

Print numbers 1–30. Multiples of 3 → `Fizz`, 5 → `Buzz`, both → `FizzBuzz`, else the number.

**Check:** [Answer](../answers/03-control-flow-answers.md#exercise-3--fizzbuzz)

### Exercise 4 — Countdown

Use `while` to count down from 10 to 1, then print `Go!`

**Check:** [Answer](../answers/03-control-flow-answers.md#exercise-4--countdown)

### Exercise 5 — Sum 1 to N

Ask for `N`. Use `for` to compute sum `1 + 2 + ... + N`.

**Check:** [Answer](../answers/03-control-flow-answers.md#exercise-5--sum-1-to-n)

---

[All answers](../answers/03-control-flow-answers.md) · **Next:** [Lesson 04](04-functions.md)
