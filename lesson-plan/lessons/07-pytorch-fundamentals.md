# Lesson 07 — PyTorch fundamentals

**Time:** 3 weeks (~30 hours)  
**Prerequisite:** [Lesson 06](06-deep-learning-theory.md)  
**Platform notes:** Use `mps` (Mac) or `cuda` (Debian) from your setup track

## Learning objectives

- Tensors and `device`
- `autograd` and computation graphs
- `nn.Module`, optimizers, training loops
- `Dataset` / `DataLoader`

## 1. Device helper (use in all projects)

```python
import torch

def get_device():
    if torch.cuda.is_available():
        return torch.device("cuda")
    if torch.backends.mps.is_available():
        return torch.device("mps")
    return torch.device("cpu")
```

## 2. Tensors

```python
x = torch.randn(32, 10, device=device)  # batch 32, features 10
w = torch.randn(10, 1, device=device, requires_grad=True)
y = x @ w
loss = y.pow(2).mean()
loss.backward()
print(w.grad.shape)
```

## 3. Training loop pattern

```python
import torch.nn as nn
import torch.optim as optim

model = nn.Sequential(
    nn.Linear(10, 64),
    nn.ReLU(),
    nn.Linear(64, 1),
).to(device)

optimizer = optim.Adam(model.parameters(), lr=1e-3)
criterion = nn.MSELoss()

for epoch in range(10):
    model.train()
    for batch_x, batch_y in train_loader:
        batch_x, batch_y = batch_x.to(device), batch_y.to(device)
        optimizer.zero_grad()
        pred = model(batch_x)
        loss = criterion(pred, batch_y)
        loss.backward()
        optimizer.step()
```

## 4. DataLoader

```python
from torch.utils.data import Dataset, DataLoader

class TabularDataset(Dataset):
    def __init__(self, X, y):
        self.X = torch.tensor(X, dtype=torch.float32)
        self.y = torch.tensor(y, dtype=torch.float32)

    def __len__(self):
        return len(self.X)

    def __getitem__(self, idx):
        return self.X[idx], self.y[idx]

loader = DataLoader(dataset, batch_size=32, shuffle=True)
```

## 5. Save / load

```python
torch.save(model.state_dict(), "model.pt")
model.load_state_dict(torch.load("model.pt", map_location=device))
```

## 6. `torch.nn` building blocks

- `nn.Conv2d`, `nn.Linear`, `nn.BatchNorm2d`, `nn.Dropout`
- `nn.CrossEntropyLoss` for multi-class (expects class indices)

## Exercises

1. Train MLP on sklearn digits (flatten 8×8 → classes).
2. Add validation loop; track best val accuracy.
3. Plot train vs val loss per epoch.

## Mini-project

`pytorch_trainer` module: reusable `train_one_epoch`, `evaluate`, `get_device`.

**Next:** [Lesson 08 — CNNs and computer vision](08-cnns-computer-vision.md)
