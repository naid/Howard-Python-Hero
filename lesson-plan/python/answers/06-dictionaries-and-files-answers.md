# Answers — Python Lesson 06: Dictionaries and files

## Exercise 1 — Phone book

```python
contacts = {"Alice": "555-0100", "Bob": "555-0200"}
name = input("Name? ")
if name in contacts:
    print(contacts[name])
else:
    print("Not found")
```

---

## Exercise 2 — Word frequency

```python
text = "to be or not to be"
counts = {}
for word in text.lower().split():
    counts[word] = counts.get(word, 0) + 1
print(counts)
# {'to': 2, 'be': 2, 'or': 1, 'not': 1}
```

---

## Exercise 3 — Write and read

```python
with open("notes.txt", "w") as f:
    f.write("alpha\nbeta\ngamma\n")

with open("notes.txt", "r") as f:
    for i, line in enumerate(f, start=1):
        print(f"{i}: {line.strip()}")
```

---

## Exercise 4 — CSV-style parse

`speeds.csv`:

```
30
45
60
```

```python
speeds = []
with open("speeds.csv", "r") as f:
    for line in f:
        speeds.append(int(line.strip()))
print(sum(speeds) / len(speeds))  # 45.0
```

---

## Exercise 5 — Safe input loop

```python
total = 0
while True:
    raw = input("Enter integer or 'done': ").strip()
    if raw.lower() == "done":
        break
    try:
        total += int(raw)
    except ValueError:
        print("Invalid, try again.")
print(f"Sum: {total}")
```

---

[← Back to Lesson 06](../lessons/06-dictionaries-and-files.md)
