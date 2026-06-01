# Answers — PyTorch Lesson 05: DataLoader

## Exercise 1 — Custom Dataset

```python
import torch
from torch.utils.data import Dataset, DataLoader

N = 100
X = torch.randn(N, 3)
y = X.sum(dim=1, keepdim=True) + 0.1 * torch.randn(N, 1)

class TabularDataset(Dataset):
    def __init__(self, X, y):
        self.X = X
        self.y = y

    def __len__(self):
        return len(self.X)

    def __getitem__(self, idx):
        return self.X[idx], self.y[idx]

loader = DataLoader(TabularDataset(X, y), batch_size=16, shuffle=True)
```

---

## Exercise 2 — Iterate one epoch

```python
for i, (xb, yb) in enumerate(loader):
    print(xb.shape, yb.shape)
    if i == 2:
        break
# torch.Size([16, 3]) torch.Size([16, 1])  (last batch may be smaller)
```

---

## Exercise 3 — CSV pipeline

`data.csv` (example rows):

```
x1,x2,y
1.0,2.0,3.1
0.5,1.5,2.0
```

```python
import pandas as pd
import torch
import torch.nn as nn
from torch.utils.data import TensorDataset, DataLoader

df = pd.read_csv("data.csv")
# generate more rows in practice
X = torch.tensor(df[["x1", "x2"]].values, dtype=torch.float32)
y = torch.tensor(df["y"].values, dtype=torch.float32).unsqueeze(1)
loader = DataLoader(TensorDataset(X, y), batch_size=8, shuffle=True)

class MLP(nn.Module):
    def __init__(self):
        super().__init__()
        self.net = nn.Sequential(nn.Linear(2, 8), nn.ReLU(), nn.Linear(8, 1))
    def forward(self, x):
        return self.net(x)

model = MLP()
opt = torch.optim.Adam(model.parameters(), lr=1e-2)
crit = nn.MSELoss()

for epoch in range(10):
    for xb, yb in loader:
        opt.zero_grad()
        crit(model(xb), yb).backward()
        opt.step()
```

---

[← Back to Lesson 05](../lessons/05-dataloader.md)
