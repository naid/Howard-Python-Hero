# Python Lesson 06 — Dictionaries and files

**Time:** 4–5 hours  
**Prerequisite:** [Lesson 05](05-lists-and-loops.md)

## 1. Dictionaries

```python
sensor = {"lidar": 1.2, "camera": 0.9, "radar": 0.7}
print(sensor["lidar"])
sensor["gps"] = 1.0
```

## 2. Looping dicts

```python
for name, value in sensor.items():
    print(name, value)
```

## 3. Reading files

```python
with open("log.txt", "r") as f:
    for line in f:
        print(line.strip())
```

## 4. Writing files

```python
with open("out.txt", "w") as f:
    f.write("line one\n")
    f.write("line two\n")
```

## 5. try / except

```python
try:
    value = int(input("Enter a number: "))
except ValueError:
    print("That was not a valid integer.")
```

## Example: sensor lookup

```python
readings = {"lidar": 1.2, "camera": 0.9}
name = input("Sensor? ")
if name in readings:
    print(readings[name])
else:
    print("Unknown sensor")
```

---

## Exercises

Folder: `~/python-hero/practice/python/lesson06/`

### Exercise 1 — Phone book

Dict `contacts = {"Alice": "555-0100", "Bob": "555-0200"}`. Ask for a name, print number or `"Not found"`.

**Check:** [Answer](../answers/06-dictionaries-and-files-answers.md#exercise-1--phone-book)

### Exercise 2 — Word frequency

String `"to be or not to be"`. Build a dict counting each word (lowercase).

**Check:** [Answer](../answers/06-dictionaries-and-files-answers.md#exercise-2--word-frequency)

### Exercise 3 — Write and read

Write three lines to `notes.txt`, then read and print them with line numbers `1: ...`.

**Check:** [Answer](../answers/06-dictionaries-and-files-answers.md#exercise-3--write-and-read)

### Exercise 4 — CSV-style parse

File content (create `speeds.csv`):

```
30
45
60
```

Read lines, convert to integers, print average.

**Check:** [Answer](../answers/06-dictionaries-and-files-answers.md#exercise-4--csv-style-parse)

### Exercise 5 — Safe input loop

Keep asking for integers until user types `done`. Print running sum. Handle invalid input without crashing.

**Check:** [Answer](../answers/06-dictionaries-and-files-answers.md#exercise-5--safe-input-loop)

---

[All answers](../answers/06-dictionaries-and-files-answers.md) · **Next:** [Lesson 07](07-classes-and-oop.md)
