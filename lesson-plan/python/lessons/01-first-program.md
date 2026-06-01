# Python Lesson 01 — Your first program

**Time:** 2–3 hours  
**Prerequisite:** Mac or Debian setup complete

## What you will learn

- Run Python from the terminal
- Use `print` and `input`
- Save and run a `.py` file

## 1. Hello in the terminal

Activate your virtual environment, then:

```bash
python3
```

```python
print("Hello, Python Hero!")
```

Exit with `exit()` or `Ctrl+D`.

## 2. Your first script

Create `~/python-hero/practice/python/lesson01/hello.py`:

```python
print("Hello, world!")
print("2 + 2 =", 2 + 2)
```

Run:

```bash
cd ~/python-hero/practice/python/lesson01
python hello.py
```

Expected output:

```
Hello, world!
2 + 2 = 4
```

## 3. Asking the user for input

```python
name = input("What is your name? ")
print("Nice to meet you,", name)
```

`input` always returns a **string**. You will convert types in Lesson 02.

## 4. Comments

```python
# This is a comment — Python ignores it
print("Visible line")
```

## 5. Common mistakes

| Mistake | Fix |
|---------|-----|
| `Print("hi")` | Python is case-sensitive: `print` |
| Forgot quotes on text | Use `"hello"` not `hello` |
| Running wrong file | Check `pwd` and path |

---

## Exercises

Do these in `~/python-hero/practice/python/lesson01/`. Try each for at least 10 minutes before checking answers.

### Exercise 1 — Greeting script

Write `greet.py` that asks for the user's name and prints: `Hello, <name>!`

**Check your work:** [Exercise 1 answer](../answers/01-first-program-answers.md#exercise-1--greeting-script)

### Exercise 2 — Simple math

Write `math_demo.py` that prints the result of `10 + 5`, `10 - 5`, `10 * 5`, and `10 / 5` on separate lines.

**Check your work:** [Exercise 2 answer](../answers/01-first-program-answers.md#exercise-2--simple-math)

### Exercise 3 — About me

Write `about_me.py` that prints three lines: your name, your goal for this course, and one fact about you (use three `print` calls).

**Check your work:** [Exercise 3 answer](../answers/01-first-program-answers.md#exercise-3--about-me)

### Exercise 4 — Fix the bug

This program has errors. Copy it to `broken.py`, fix it, and run successfully:

```python
Print("Starting...")
x = input(Enter your age: )
print("You typed", x)
```

**Check your work:** [Exercise 4 answer](../answers/01-first-program-answers.md#exercise-4--fix-the-bug)

---

## All answers for this lesson

[01-first-program-answers.md](../answers/01-first-program-answers.md)

**Next:** [Lesson 02 — Variables and types](02-variables-and-types.md)
