# Answers — Python Lesson 03: Control flow

## Exercise 1 — Even or odd

```python
n = int(input("Number: "))
if n % 2 == 0:
    print("even")
else:
    print("odd")
```

---

## Exercise 2 — Grade letter

```python
score = int(input("Score: "))
if score >= 90:
    print("A")
elif score >= 80:
    print("B")
elif score >= 70:
    print("C")
elif score >= 60:
    print("D")
else:
    print("F")
```

---

## Exercise 3 — FizzBuzz

```python
for n in range(1, 31):
    if n % 3 == 0 and n % 5 == 0:
        print("FizzBuzz")
    elif n % 3 == 0:
        print("Fizz")
    elif n % 5 == 0:
        print("Buzz")
    else:
        print(n)
```

---

## Exercise 4 — Countdown

```python
count = 10
while count >= 1:
    print(count)
    count -= 1
print("Go!")
```

---

## Exercise 5 — Sum 1 to N

```python
n = int(input("N: "))
total = 0
for i in range(1, n + 1):
    total += i
print(f"Sum 1 to {n} = {total}")
```

For `N=5`, output: `Sum 1 to 5 = 15`

---

[← Back to Lesson 03](../lessons/03-control-flow.md)
