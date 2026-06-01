# Lesson 08 — CNNs and computer vision

**Time:** 2 weeks (~25 hours)  
**Prerequisite:** [Lesson 07](07-pytorch-fundamentals.md)  
**Job alignment:** Computer vision, CNNs, camera-based autonomy

## Learning objectives

- Convolutions, pooling, receptive field
- Image classification pipeline
- Transfer learning with pretrained models
- Data augmentation for robustness

## 1. Why CNNs for images

- **Local connectivity** — nearby pixels matter
- **Weight sharing** — same filter across locations
- Fewer parameters than fully-connected on raw pixels

## 2. Basic CNN in PyTorch

```python
model = nn.Sequential(
    nn.Conv2d(3, 32, kernel_size=3, padding=1),
    nn.ReLU(),
    nn.MaxPool2d(2),
    nn.Conv2d(32, 64, kernel_size=3, padding=1),
    nn.ReLU(),
    nn.MaxPool2d(2),
    nn.Flatten(),
    nn.Linear(64 * 8 * 8, 10),
)
```

Input shape: `(batch, channels, height, width)` = `(N, 3, 32, 32)` for CIFAR-10.

## 3. Transforms and augmentation

```python
from torchvision import transforms

train_tf = transforms.Compose([
    transforms.RandomHorizontalFlip(),
    transforms.RandomRotation(10),
    transforms.ToTensor(),
    transforms.Normalize((0.5,), (0.5,)),
])
```

Augmentation simulates diverse driving conditions (lighting, angle).

## 4. Transfer learning

```python
from torchvision.models import resnet18, ResNet18_Weights

weights = ResNet18_Weights.DEFAULT
model = resnet18(weights=weights)
model.fc = nn.Linear(model.fc.in_features, num_classes)
```

Freeze early layers initially; fine-tune later.

## 5. Datasets to practice

| Dataset | Size | Task |
|---------|------|------|
| MNIST | Small | Digit classification |
| CIFAR-10 | Medium | 10-class objects |
| [CamVid](http://mi.eng.cam.ac.uk/research/projects/VideoRec/CamVid/) | Driving scenes | Segmentation (advanced) |

```python
from torchvision.datasets import CIFAR10
from torchvision import transforms

train_set = CIFAR10(root="./data", train=True, download=True, transform=train_tf)
```

## 6. Evaluation for vision

- Confusion matrix per class
- Visualize misclassified images

## Exercises

1. Train CNN from scratch on CIFAR-10; target >70% test accuracy.
2. Same with ResNet18 transfer learning; compare convergence speed.
3. Grad-CAM visualization (optional library `pytorch-grad-cam`) on one image.

## Mini-project

**Traffic sign or vehicle patch classifier** — organize folder-per-class dataset, train ResNet, document metrics.

**Next:** [Lesson 09 — Transformers and LLMs](09-transformers-and-llms.md)
