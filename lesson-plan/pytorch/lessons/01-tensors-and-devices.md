# PyTorch Lesson 01 — Tensors and devices

**Time:** 3–4 hours  
**Prerequisite:** [Python track](../../python/README.md) complete

## 1. Import and device

```python
import torch

def get_device():
    if torch.cuda.is_available():
        return torch.device("cuda")
    if torch.backends.mps.is_available():
        return torch.device("mps")
    return torch.device("cpu")

device = get_device()
print(device)
```

## 2. Creating tensors

```python
a = torch.tensor([1.0, 2.0, 3.0])
b = torch.zeros(2, 3)
c = torch.randn(4, 4)
d = torch.ones(3, device=device)
```

## 3. Shape and dtype

```python
x = torch.randn(32, 10)
print(x.shape, x.dtype)
```

## 4. Operations

```python
x = torch.tensor([[1.0, 2.0], [3.0, 4.0]])
y = x @ x.T
print(y.mean(), y.sum())
```

## 5. NumPy bridge

```python
import numpy as np
arr = np.array([1, 2, 3], dtype=np.float32)
t = torch.from_numpy(arr)
```

---

## Exercises

Folder: `~/python-hero/practice/pytorch/lesson01/`

### Exercise 1 — Device checker

Script prints device type and creates a `3×3` tensor of ones on that device.

**Check:** [Answer](../answers/01-tensors-and-devices-answers.md#exercise-1--device-checker)

### Exercise 2 — Matrix multiply

Create `A` shape `(2, 3)` and `B` shape `(3, 2)`. Compute `A @ B` and print shape and result.

**Check:** [Answer](../answers/01-tensors-and-devices-answers.md#exercise-2--matrix-multiply)

### Exercise 3 — Temperature tensor

Tensor of 5 Celsius values. Convert to Fahrenheit: `F = C * 9/5 + 32` (vectorized, no loop).

**Check:** [Answer](../answers/01-tensors-and-devices-answers.md#exercise-3--temperature-tensor)

### Exercise 4 — Mean and std

Random tensor shape `(100,)`. Print mean and standard deviation using PyTorch functions.

**Check:** [Answer](../answers/01-tensors-and-devices-answers.md#exercise-4--mean-and-std)

---

[All answers](../answers/01-tensors-and-devices-answers.md) · **Next:** [Lesson 02](02-autograd.md)
