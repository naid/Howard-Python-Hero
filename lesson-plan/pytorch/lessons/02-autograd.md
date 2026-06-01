# PyTorch Lesson 02 — Autograd

**Time:** 3–4 hours  
**Prerequisite:** [Lesson 01](01-tensors-and-devices.md)

## 1. requires_grad

```python
import torch

w = torch.tensor(2.0, requires_grad=True)
b = torch.tensor(1.0, requires_grad=True)
x = torch.tensor(3.0)

y = w * x + b
loss = (y - 10) ** 2
loss.backward()

print(w.grad)  # gradient of loss w.r.t. w
print(b.grad)
```

## 2. Zero gradients

```python
w.grad.zero_()
b.grad.zero_()
```

## 3. Simple linear fit (manual)

Goal: learn `w` and `b` so `y ≈ 2*x + 1` for data points.

```python
w = torch.tensor(0.0, requires_grad=True)
b = torch.tensor(0.0, requires_grad=True)
x_data = torch.tensor([1.0, 2.0, 3.0])
y_data = torch.tensor([3.0, 5.0, 7.0])

for step in range(100):
    pred = w * x_data + b
    loss = ((pred - y_data) ** 2).mean()
    loss.backward()
    with torch.no_grad():
        w -= 0.1 * w.grad
        b -= 0.1 * b.grad
        w.grad.zero_()
        b.grad.zero_()
```

---

## Exercises

Folder: `~/python-hero/practice/pytorch/lesson02/`

### Exercise 1 — Gradient of x²

`x = torch.tensor(4.0, requires_grad=True)`, `y = x**2`, backward, print `x.grad` (expect 8.0).

**Check:** [Answer](../answers/02-autograd-answers.md#exercise-1--gradient-of-x²)

### Exercise 2 — Manual SGD step

After backward on `loss = (w*3 + b - 7)**2`, update `w` and `b` by hand with lr=0.1, then zero grads.

**Check:** [Answer](../answers/02-autograd-answers.md#exercise-2--manual-sgd-step)

### Exercise 3 — Fit y = 3x

Data: `x=[0,1,2]`, `y=[0,3,6]`. Train `w,b` for 200 steps; print final `w,b` (expect ~3 and ~0).

**Check:** [Answer](../answers/02-autograd-answers.md#exercise-3--fit-y--3x)

---

[All answers](../answers/02-autograd-answers.md) · **Next:** [Lesson 03](03-neural-networks.md)
