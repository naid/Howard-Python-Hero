# Answers — PyTorch Lesson 02: Autograd

## Exercise 1 — Gradient of x²

```python
import torch

x = torch.tensor(4.0, requires_grad=True)
y = x ** 2
y.backward()
print(x.grad)  # tensor(8.)
```

---

## Exercise 2 — Manual SGD step

```python
import torch

w = torch.tensor(1.0, requires_grad=True)
b = torch.tensor(0.0, requires_grad=True)
loss = (w * 3 + b - 7) ** 2
loss.backward()
lr = 0.1
with torch.no_grad():
    w -= lr * w.grad
    b -= lr * b.grad
    w.grad.zero_()
    b.grad.zero_()
print(w, b)
```

---

## Exercise 3 — Fit y = 3x

```python
import torch

w = torch.tensor(0.0, requires_grad=True)
b = torch.tensor(0.0, requires_grad=True)
x_data = torch.tensor([0.0, 1.0, 2.0])
y_data = torch.tensor([0.0, 3.0, 6.0])

for _ in range(200):
    pred = w * x_data + b
    loss = ((pred - y_data) ** 2).mean()
    loss.backward()
    with torch.no_grad():
        w -= 0.1 * w.grad
        b -= 0.1 * b.grad
        w.grad.zero_()
        b.grad.zero_()

print(w.item(), b.item())  # ~3.0, ~0.0
```

---

[← Back to Lesson 02](../lessons/02-autograd.md)
