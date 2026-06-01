# Answers — Python Lesson 01: First program

Try every exercise yourself first. These are **one valid solution** — yours can differ slightly and still be correct.

---

## Exercise 1 — Greeting script

```python
name = input("What is your name? ")
print("Hello,", name + "!")
```

Or with an f-string (Lesson 02):

```python
name = input("What is your name? ")
print(f"Hello, {name}!")
```

---

## Exercise 2 — Simple math

```python
print(10 + 5)
print(10 - 5)
print(10 * 5)
print(10 / 5)
```

Output:

```
15
5
50
2.0
```

Note: `/` always gives a **float** in Python 3.

---

## Exercise 3 — About me

```python
print("Alex")
print("I want to learn ML for autonomy.")
print("I am new to programming.")
```

Any three truthful lines are correct.

---

## Exercise 4 — Fix the bug

Fixed version:

```python
print("Starting...")
x = input("Enter your age: ")
print("You typed", x)
```

Fixes made:

1. `Print` → `print` (lowercase)
2. Missing quotes around the prompt string
3. `input(Enter your age: )` → `input("Enter your age: ")`

---

[← Back to Lesson 01](../lessons/01-first-program.md)
