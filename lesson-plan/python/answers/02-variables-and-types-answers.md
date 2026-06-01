# Answers — Python Lesson 02: Variables and types

## Exercise 1 — Celsius to Fahrenheit

```python
c = float(input("Celsius: "))
f = c * 9 / 5 + 32
print(f"{f:.1f} Fahrenheit")
```

---

## Exercise 2 — Rectangle area

```python
width = 4.5
height = 3.2
area = width * height
perimeter = 2 * (width + height)
print(f"Area: {area}")
print(f"Perimeter: {perimeter}")
```

Output: `Area: 14.4`, `Perimeter: 15.4`

---

## Exercise 3 — Type detective

```python
a = 10
b = 3.14
c = "hello"
d = False
print(a, type(a))
print(b, type(b))
print(c, type(c))
print(d, type(d))
```

---

## Exercise 4 — Seconds to minutes

```python
total = int(input("Seconds: "))
minutes = total // 60
seconds = total % 60
print(f"{minutes} min {seconds} sec")
```

Example: `125` → `2 min 5 sec`

---

[← Back to Lesson 02](../lessons/02-variables-and-types.md)
