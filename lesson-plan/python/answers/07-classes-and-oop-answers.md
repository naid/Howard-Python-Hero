# Answers — Python Lesson 07: Classes and OOP

## Exercise 1 — BankAccount

```python
class BankAccount:
    def __init__(self):
        self.balance = 0.0

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount

    def withdraw(self, amount):
        if amount > 0 and amount <= self.balance:
            self.balance -= amount

acct = BankAccount()
acct.deposit(100)
acct.withdraw(30)
print(acct.balance)  # 70.0
```

---

## Exercise 2 — Rectangle class

```python
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

    def perimeter(self):
        return 2 * (self.width + self.height)

r = Rectangle(4, 5)
print(r.area())       # 20
print(r.perimeter())  # 18
```

---

## Exercise 3 — Fleet

```python
class Fleet:
    def __init__(self):
        self.vehicle_ids = []

    def add(self, vehicle_id):
        self.vehicle_ids.append(vehicle_id)

    def count(self):
        return len(self.vehicle_ids)

fleet = Fleet()
fleet.add("A1")
fleet.add("B2")
print(fleet.count())  # 2
```

---

## Exercise 4 — dataclass Point

```python
from dataclasses import dataclass
import math

@dataclass
class Point:
    x: float
    y: float

    def distance_to_origin(self):
        return math.sqrt(self.x ** 2 + self.y ** 2)

p = Point(3, 4)
print(p.distance_to_origin())  # 5.0
```

---

[← Back to Lesson 07](../lessons/07-classes-and-oop.md)
