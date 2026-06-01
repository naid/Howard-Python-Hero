# Answers — PyTorch Lesson 04: Training loop

## Exercise 1 — Train 20 epochs

```python
import torch
import torch.nn as nn
from torch.utils.data import TensorDataset, DataLoader

N = 500
X = torch.randn(N, 2)
y = (2 * X[:, 0] + 3 * X[:, 1] - 1).unsqueeze(1) + 0.1 * torch.randn(N, 1)

dataset = TensorDataset(X, y)
loader = DataLoader(dataset, batch_size=32, shuffle=True)

class MLP(nn.Module):
    def __init__(self):
        super().__init__()
        self.net = nn.Sequential(nn.Linear(2, 16), nn.ReLU(), nn.Linear(16, 1))

    def forward(self, x):
        return self.net(x)

device = torch.device("cpu")
model = MLP().to(device)
criterion = nn.MSELoss()
optimizer = torch.optim.Adam(model.parameters(), lr=1e-2)

for epoch in range(1, 21):
    model.train()
    total = 0.0
    for xb, yb in loader:
        optimizer.zero_grad()
        loss = criterion(model(xb), yb)
        loss.backward()
        optimizer.step()
        total += loss.item() * len(xb)
    if epoch % 5 == 0:
        print(f"Epoch {epoch} loss: {total / len(dataset):.4f}")
```

Loss should drop well below 0.1.

---

## Exercise 2 — Train/val split

```python
n_train = int(0.8 * N)
train_ds = TensorDataset(X[:n_train], y[:n_train])
val_ds = TensorDataset(X[n_train:], y[n_train:])
train_loader = DataLoader(train_ds, batch_size=32, shuffle=True)
val_loader = DataLoader(val_ds, batch_size=32)

# ... train 20 epochs ...
# val loop:
model.eval()
val_loss = 0.0
with torch.no_grad():
    for xb, yb in val_loader:
        val_loss += criterion(model(xb), yb).item() * len(xb)
print("Val loss:", val_loss / len(val_ds))
```

---

## Exercise 3 — Save weights

```python
torch.save(model.state_dict(), "model.pt")

model2 = MLP()
model2.load_state_dict(torch.load("model.pt", map_location=device))
model2.eval()
```

---

[← Back to Lesson 04](../lessons/04-training-loop.md)
