# PyTorch Lesson 03 — Neural networks (nn.Module)

**Time:** 4 hours  
**Prerequisite:** [Lesson 02](02-autograd.md)

## 1. nn.Module

```python
import torch
import torch.nn as nn

class SimpleMLP(nn.Module):
    def __init__(self):
        super().__init__()
        self.net = nn.Sequential(
            nn.Linear(10, 32),
            nn.ReLU(),
            nn.Linear(32, 1),
        )

    def forward(self, x):
        return self.net(x)

model = SimpleMLP()
x = torch.randn(16, 10)
print(model(x).shape)  # (16, 1)
```

## 2. Loss and optimizer

```python
criterion = nn.MSELoss()
optimizer = torch.optim.Adam(model.parameters(), lr=1e-3)
```

## 3. One training step

```python
model.train()
optimizer.zero_grad()
pred = model(x_batch)
loss = criterion(pred, y_batch)
loss.backward()
optimizer.step()
```

## 4. eval mode

```python
model.eval()
with torch.no_grad():
    pred = model(x_batch)
```

---

## Exercises

Folder: `~/python-hero/practice/pytorch/lesson03/`

### Exercise 1 — Two-layer MLP

Build MLP: input 4 → hidden 8 (ReLU) → output 2. Forward pass on batch size 5.

**Check:** [Answer](../answers/03-neural-networks-answers.md#exercise-1--two-layer-mlp)

### Exercise 2 — Count parameters

Print total trainable parameter count for your MLP.

**Check:** [Answer](../answers/03-neural-networks-answers.md#exercise-2--count-parameters)

### Exercise 3 — Single step training

Random `x` (8,4), `y` (8,2). One forward, MSE loss, backward, optimizer step. Print loss value.

**Check:** [Answer](../answers/03-neural-networks-answers.md#exercise-3--single-step-training)

---

[All answers](../answers/03-neural-networks-answers.md) · **Next:** [Lesson 04](04-training-loop.md)
