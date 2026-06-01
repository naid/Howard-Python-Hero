# Answers — Python Lesson 04: Functions

## Exercise 1 — Rectangle functions

```python
def area(width, height):
    return width * height

def perimeter(width, height):
    return 2 * (width + height)

w, h = 5, 3
print(area(w, h))        # 15
print(perimeter(w, h))  # 16
```

---

## Exercise 2 — is_prime

```python
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True

print(is_prime(2))   # True
print(is_prime(9))   # False
print(is_prime(17))  # True
```

---

## Exercise 3 — safe_divide

```python
def safe_divide(a, b):
    if b == 0:
        return None
    return a / b

print(safe_divide(10, 2))   # 5.0
print(safe_divide(10, 0))   # None
```

---

## Exercise 4 — word_count

```python
def count_words(text):
    if not text.strip():
        return 0
    return len(text.split())

print(count_words("hello world"))  # 2
print(count_words("one"))          # 1
```

---

[← Back to Lesson 04](../lessons/04-functions.md)
