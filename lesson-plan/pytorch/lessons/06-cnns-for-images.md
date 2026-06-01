# PyTorch Lesson 06 — CNNs for images

**Time:** 5–6 hours  
**Prerequisite:** [Lesson 05](05-dataloader.md)

## 1. Install torchvision

```bash
pip install torchvision
```

## 2. Simple CNN

```python
import torch.nn as nn

class SmallCNN(nn.Module):
    def __init__(self, num_classes=10):
        super().__init__()
        self.features = nn.Sequential(
            nn.Conv2d(1, 16, 3, padding=1),
            nn.ReLU(),
            nn.MaxPool2d(2),
            nn.Conv2d(16, 32, 3, padding=1),
            nn.ReLU(),
            nn.MaxPool2d(2),
        )
        self.classifier = nn.Linear(32 * 7 * 7, num_classes)

    def forward(self, x):
        x = self.features(x)
        x = x.view(x.size(0), -1)
        return self.classifier(x)
```

MNIST images are `1×28×28`.

## 3. Load MNIST

```python
from torchvision import datasets, transforms

transform = transforms.ToTensor()
train_set = datasets.MNIST(root="./data", train=True, download=True, transform=transform)
```

## 4. Training tip

Start with subset (e.g. 5000 images) if your machine is slow.

---

## Exercises

Folder: `~/python-hero/practice/pytorch/lesson06/`

### Exercise 1 — DataLoader MNIST

`DataLoader` batch 64, shuffle. Print one batch shape (`N, 1, 28, 28`) and labels shape.

**Check:** [Answer](../answers/06-cnns-for-images-answers.md#exercise-1--dataloader-mnist)

### Exercise 2 — One epoch MNIST

Train `SmallCNN` 1 epoch on 5000 training samples. Print average loss.

**Check:** [Answer](../answers/06-cnns-for-images-answers.md#exercise-2--one-epoch-mnist)

### Exercise 3 — Evaluate accuracy

Compute % correct on 1000 test images.

**Check:** [Answer](../answers/06-cnns-for-images-answers.md#exercise-3--evaluate-accuracy)

### Exercise 4 — Transfer learning (stretch)

Use `resnet18` with pretrained weights; replace final layer for 10 classes; train 1 epoch on subset.

**Check:** [Answer](../answers/06-cnns-for-images-answers.md#exercise-4--transfer-learning-stretch)

---

[All answers](../answers/06-cnns-for-images-answers.md) · **Next:** [Lesson 07](07-mini-trainer-project.md)
