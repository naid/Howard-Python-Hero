# PyTorch Lesson 04 — Training loop

**Time:** 4–5 hours  
**Prerequisite:** [Lesson 03](03-neural-networks.md)

## Full training pattern

```python
import torch
import torch.nn as nn

def train_epoch(model, loader, criterion, optimizer, device):
    model.train()
    total_loss = 0.0
    for x_batch, y_batch in loader:
        x_batch = x_batch.to(device)
        y_batch = y_batch.to(device)
        optimizer.zero_grad()
        pred = model(x_batch)
        loss = criterion(pred, y_batch)
        loss.backward()
        optimizer.step()
        total_loss += loss.item() * len(x_batch)
    return total_loss / len(loader.dataset)

def evaluate(model, loader, criterion, device):
    model.eval()
    total_loss = 0.0
    with torch.no_grad():
        for x_batch, y_batch in loader:
            x_batch = x_batch.to(device)
            y_batch = y_batch.to(device)
            pred = model(x_batch)
            loss = criterion(pred, y_batch)
            total_loss += loss.item() * len(x_batch)
    return total_loss / len(loader.dataset)
```

## Synthetic regression example

```python
# y = 2*x1 + 3*x2 - 1 + noise
N = 500
X = torch.randn(N, 2)
y = (2 * X[:, 0] + 3 * X[:, 1] - 1).unsqueeze(1) + 0.1 * torch.randn(N, 1)
```

Train for 20 epochs and watch loss drop.

---

## Exercises

Folder: `~/python-hero/practice/pytorch/lesson04/`

### Exercise 1 — Train 20 epochs

Use synthetic data above. MLP `2→16→1`, MSE, Adam. Print train loss every 5 epochs.

**Check:** [Answer](../answers/04-training-loop-answers.md#exercise-1--train-20-epochs)

### Exercise 2 — Train/val split

Hold out 20% for validation. Print train and val loss after training.

**Check:** [Answer](../answers/04-training-loop-answers.md#exercise-2--trainval-split)

### Exercise 3 — Save weights

After training, save `model.state_dict()` to `model.pt` and reload into a new model.

**Check:** [Answer](../answers/04-training-loop-answers.md#exercise-3--save-weights)

---

[All answers](../answers/04-training-loop-answers.md) · **Next:** [Lesson 05](05-dataloader.md)
