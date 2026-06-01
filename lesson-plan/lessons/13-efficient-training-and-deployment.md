# Lesson 13 — Efficient training, scale, and deployment

**Time:** 3 weeks (~30 hours)  
**Prerequisite:** [Lesson 12](12-reinforcement-learning.md)  
**Job alignment:** Sparse training, pruning, distributed computing, TensorFlow, production ML

## Learning objectives

- Mixed precision training
- Pruning and sparsity
- Latency vs accuracy tradeoffs
- Distributed data parallel training
- TensorFlow basics (second framework in job post)
- Production and safety-critical practices

## 1. Mixed precision

```python
from torch.cuda.amp import autocast, GradScaler

scaler = GradScaler()
with autocast():
    loss = model(x)
scaler.scale(loss).backward()
scaler.step(optimizer)
scaler.update()
```

On Mac MPS: check current PyTorch docs for autocast support; fall back to float32 if needed.

## 2. Pruning and sparse training

**Pruning:** remove small weights → smaller, faster model.

```python
import torch.nn.utils.prune as prune
prune.l1_unstructured(module, name="weight", amount=0.3)
```

**Sparse training:** train while keeping most weights at zero — research area for latency on vehicle hardware.

## 3. Latency optimization

| Technique | Effect |
|-----------|--------|
| Smaller model | Faster inference |
| Quantization (INT8) | Smaller memory, faster on edge chips |
| TorchScript / ONNX export | Deploy outside Python |
| Batch size = 1 tuning | Real-time inference |

Measure:

```python
import time
start = time.perf_counter()
with torch.no_grad():
    model(x)
print(time.perf_counter() - start)
```

## 4. Distributed training (PyTorch)

**DistributedDataParallel (DDP)** — one process per GPU:

```bash
# Debian multi-GPU example
torchrun --nndevices=2 train.py
```

Concepts:

- Each GPU gets a batch shard
- Gradients synchronized across GPUs
- Enables training foundation-scale models

Cloud option if local GPU is weak: single-node Colab, Lambda Labs, etc.

## 5. TensorFlow quick comparison

```bash
pip install tensorflow
```

```python
import tensorflow as tf
model = tf.keras.Sequential([
    tf.keras.layers.Dense(64, activation="relu"),
    tf.keras.layers.Dense(10),
])
model.compile(optimizer="adam", loss="sparse_categorical_crossentropy")
```

Job lists **both** frameworks — understand Keras API; primary depth remains PyTorch.

## 6. Production ML checklist

- [ ] Versioned datasets and model weights
- [ ] Reproducible seeds and config files
- [ ] Unit tests on preprocessing
- [ ] Monitoring: input drift, latency, error rate
- [ ] Rollback plan for bad deployments

## 7. Safety-critical mindset (vehicles)

- Fail-safe defaults (e.g. hand back to human, safe stop)
- Redundant checks on model outputs
- Extensive validation in sim + closed track before fleet
- Document assumptions and known failure modes

## Exercises

1. Prune 30% of weights on Lesson 08 CNN; compare accuracy vs inference time.
2. Export model to ONNX (`pip install onnx onnxruntime`).
3. Read one Tesla-related public talk or paper on fleet learning (blog/paper summary in notes).

## Mini-project

Optimize Lesson 08 model for inference (prune OR quantize); document accuracy/latency tradeoff in README.

**Next:** [Lesson 14 — Capstone](14-capstone-autonomy-project.md)
