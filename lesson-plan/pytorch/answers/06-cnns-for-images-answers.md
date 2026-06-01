# Answers — PyTorch Lesson 06: CNNs for images

## Exercise 1 — DataLoader MNIST

```python
from torchvision import datasets, transforms
from torch.utils.data import DataLoader

transform = transforms.ToTensor()
train_set = datasets.MNIST("./data", train=True, download=True, transform=transform)
loader = DataLoader(train_set, batch_size=64, shuffle=True)

images, labels = next(iter(loader))
print(images.shape, labels.shape)  # torch.Size([64, 1, 28, 28]) torch.Size([64])
```

---

## Exercise 2 — One epoch MNIST

```python
import torch
import torch.nn as nn
from torch.utils.data import DataLoader, Subset

# ... SmallCNN class from lesson ...

subset = Subset(train_set, range(5000))
loader = DataLoader(subset, batch_size=64, shuffle=True)
device = torch.device("cpu")
model = SmallCNN().to(device)
crit = nn.CrossEntropyLoss()
opt = torch.optim.Adam(model.parameters(), lr=1e-3)

model.train()
total, n = 0.0, 0
for images, labels in loader:
    images, labels = images.to(device), labels.to(device)
    opt.zero_grad()
    loss = crit(model(images), labels)
    loss.backward()
    opt.step()
    total += loss.item() * len(labels)
    n += len(labels)
print("Avg loss:", total / n)
```

---

## Exercise 3 — Evaluate accuracy

```python
test_set = datasets.MNIST("./data", train=False, download=True, transform=transform)
test_loader = DataLoader(Subset(test_set, range(1000)), batch_size=64)

model.eval()
correct, total = 0, 0
with torch.no_grad():
    for images, labels in test_loader:
        pred = model(images).argmax(dim=1)
        correct += (pred == labels).sum().item()
        total += len(labels)
print(f"Accuracy: {100 * correct / total:.1f}%")
```

Expect roughly 85%+ after 1 epoch on 5k train; more epochs → higher.

---

## Exercise 4 — Transfer learning (stretch)

```python
from torchvision.models import resnet18, ResNet18_Weights

weights = ResNet18_Weights.DEFAULT
model = resnet18(weights=weights)
model.fc = nn.Linear(model.fc.in_features, 10)

# MNIST is 1 channel — wrap or repeat channels:
# transforms.Compose([transforms.Grayscale(3), ...])  # 3-channel grayscale
# Or use CIFAR-10 instead for natural RGB transfer learning
```

For MNIST, a common trick:

```python
transform = transforms.Compose([
    transforms.ToTensor(),
    transforms.Lambda(lambda x: x.repeat(3, 1, 1)),
    transforms.Resize(224),
    transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225]),
])
```

Train only `model.fc` for 1 epoch first (freeze backbone) for speed.

---

[← Back to Lesson 06](../lessons/06-cnns-for-images.md)
