# Answers — PyTorch Lesson 03: Neural networks

## Exercise 1 — Two-layer MLP

```python
import torch
import torch.nn as nn

class MLP(nn.Module):
    def __init__(self):
        super().__init__()
        self.net = nn.Sequential(
            nn.Linear(4, 8),
            nn.ReLU(),
            nn.Linear(8, 2),
        )

    def forward(self, x):
        return self.net(x)

model = MLP()
x = torch.randn(5, 4)
print(model(x).shape)  # torch.Size([5, 2])
```

---

## Exercise 2 — Count parameters

```python
total = sum(p.numel() for p in model.parameters() if p.requires_grad)
print(total)  # 4*8+8 + 8*2+2 = 32+8+16+2 = 58
```

---

## Exercise 3 — Single step training

```python
import torch
import torch.nn as nn

model = MLP()
criterion = nn.MSELoss()
optimizer = torch.optim.Adam(model.parameters(), lr=1e-2)

x = torch.randn(8, 4)
y = torch.randn(8, 2)

optimizer.zero_grad()
pred = model(x)
loss = criterion(pred, y)
loss.backward()
optimizer.step()
print(loss.item())
```

---

[← Back to Lesson 03](../lessons/03-neural-networks.md)
