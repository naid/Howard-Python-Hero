# Answers — PyTorch Lesson 01: Tensors and devices

## Exercise 1 — Device checker

```python
import torch

def get_device():
    if torch.cuda.is_available():
        return torch.device("cuda")
    if torch.backends.mps.is_available():
        return torch.device("mps")
    return torch.device("cpu")

device = get_device()
print("Device:", device)
x = torch.ones(3, 3, device=device)
print(x)
```

---

## Exercise 2 — Matrix multiply

```python
import torch

A = torch.tensor([[1.0, 2.0, 3.0], [4.0, 5.0, 6.0]])
B = torch.tensor([[1.0, 2.0], [3.0, 4.0], [5.0, 6.0]])
C = A @ B
print(C.shape)  # torch.Size([2, 2])
print(C)
```

---

## Exercise 3 — Temperature tensor

```python
import torch

C = torch.tensor([0.0, 10.0, 20.0, 30.0, 37.0])
F = C * 9 / 5 + 32
print(F)
```

---

## Exercise 4 — Mean and std

```python
import torch

x = torch.randn(100)
print(x.mean().item())
print(x.std().item())
```

---

[← Back to Lesson 01](../lessons/01-tensors-and-devices.md)
