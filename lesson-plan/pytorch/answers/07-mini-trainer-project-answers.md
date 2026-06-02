# Answers — PyTorch Lesson 07: Mini trainer project

## Exercise 1 — Project skeleton

`data.py`:

```python
from torchvision import datasets, transforms
from torch.utils.data import DataLoader, random_split

def get_mnist_loaders(batch_size=64, val_fraction=0.1):
    transform = transforms.ToTensor()
    full = datasets.MNIST("./data", train=True, download=True, transform=transform)
    n_val = int(len(full) * val_fraction)
    n_train = len(full) - n_val
    train_set, val_set = random_split(full, [n_train, n_val])
    test_set = datasets.MNIST("./data", train=False, download=True, transform=transform)
    return (
        DataLoader(train_set, batch_size=batch_size, shuffle=True),
        DataLoader(val_set, batch_size=batch_size),
        DataLoader(test_set, batch_size=batch_size),
    )
```

`model.py`:

```python
import torch.nn as nn

class SmallCNN(nn.Module):
    def __init__(self, num_classes=10):
        super().__init__()
        self.features = nn.Sequential(
            nn.Conv2d(1, 16, 3, padding=1), nn.ReLU(), nn.MaxPool2d(2),
            nn.Conv2d(16, 32, 3, padding=1), nn.ReLU(), nn.MaxPool2d(2),
        )
        self.classifier = nn.Linear(32 * 7 * 7, num_classes)

    def forward(self, x):
        x = self.features(x)
        return self.classifier(x.view(x.size(0), -1))
```

`train.py` (core):

```python
import argparse
import torch
import torch.nn as nn
from model import SmallCNN
from data import get_mnist_loaders

def get_device():
    if torch.cuda.is_available():
        return torch.device("cuda")
    if torch.backends.mps.is_available():
        return torch.device("mps")
    return torch.device("cpu")

def accuracy(model, loader, device):
    model.eval()
    correct, total = 0, 0
    with torch.no_grad():
        for x, y in loader:
            x, y = x.to(device), y.to(device)
            pred = model(x).argmax(1)
            correct += (pred == y).sum().item()
            total += len(y)
    return correct / total

def main():
    parser = argparse.ArgumentParser()
    parser.add_argument("--epochs", type=int, default=5)
    parser.add_argument("--lr", type=float, default=1e-3)
    args = parser.parse_args()

    device = get_device()
    train_loader, val_loader, test_loader = get_mnist_loaders()
    model = SmallCNN().to(device)
    opt = torch.optim.Adam(model.parameters(), lr=args.lr)
    crit = nn.CrossEntropyLoss()
    best_val = float("inf")

    for epoch in range(1, args.epochs + 1):
        model.train()
        for x, y in train_loader:
            x, y = x.to(device), y.to(device)
            opt.zero_grad()
            crit(model(x), y).backward()
            opt.step()
        model.eval()
        val_loss = 0.0
        with torch.no_grad():
            for x, y in val_loader:
                x, y = x.to(device), y.to(device)
                val_loss += crit(model(x), y).item() * len(y)
        val_loss /= len(val_loader.dataset)
        if val_loss < best_val:
            best_val = val_loss
            torch.save(model.state_dict(), "checkpoints/best.pt")
        print(f"Epoch {epoch} val_loss={val_loss:.4f}")

    model.load_state_dict(torch.load("checkpoints/best.pt", map_location=device))
    print(f"Test accuracy: {100 * accuracy(model, test_loader, device):.2f}%")

if __name__ == "__main__":
    main()
```

---

## Exercise 2 — Train MNIST 5 epochs

```bash
source ~/python-hero/venv/bin/activate
cd ~/python-hero/practice/pytorch/lesson07/mini_trainer
mkdir -p checkpoints
python train.py --epochs 5
```

Expect test accuracy **≥90%** on CPU within ~10–20 min; faster on GPU/MPS.

---

## Exercise 3 — README

Example `README.md`:

```markdown
# Mini Trainer

## Install
pip install torch torchvision

## Run
python train.py --epochs 5 --lr 0.001

## Results
Test accuracy: 97.2%
Device: mps (Apple M2)
```

---

## Exercise 4 — Loss plot (stretch)

```python
import csv
history = []
# append each epoch: {"epoch": epoch, "val_loss": val_loss}
with open("history.csv", "w", newline="") as f:
    writer = csv.DictWriter(f, fieldnames=["epoch", "val_loss"])
    writer.writeheader()
    writer.writerows(history)

import matplotlib.pyplot as plt
# load and plt.plot(...)
```

---

[← Back to Lesson 07](../lessons/07-mini-trainer-project.md)
