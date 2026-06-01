# Mac 03 — GPU and accelerators (PyTorch + MPS)

**Time:** 2–4 hours  
**Prerequisite:** [02-python-environment](02-python-environment.md)

## Goals

- Install PyTorch on macOS
- Understand CPU vs **MPS** (Metal Performance Shaders) on Apple Silicon
- Verify tensor operations on the right device

## 1. Install PyTorch (Mac)

With venv activated:

```bash
pip install torch torchvision torchaudio
```

Verify:

```bash
python -c "import torch; print(torch.__version__)"
```

Official selector: [https://pytorch.org/get-started/locally/](https://pytorch.org/get-started/locally/) — choose **Mac**, **pip**, your OS version.

## 2. Device selection in PyTorch

Save as `~/python-hero/projects/hello/device_check.py`:

```python
import torch

if torch.backends.mps.is_available():
    device = torch.device("mps")
    print("Using Apple Silicon GPU (MPS)")
elif torch.cuda.is_available():
    device = torch.device("cuda")
    print("Using NVIDIA CUDA")
else:
    device = torch.device("cpu")
    print("Using CPU only")

x = torch.ones(3, 3, device=device)
y = x @ x.T
print(y)
print("Device:", y.device)
```

Run:

```bash
python device_check.py
```

### Apple Silicon (M1/M2/M3/M4)

- Expect `mps` when macOS and PyTorch versions are recent enough.
- MPS does not support every CUDA operation; some advanced training may fall back to CPU.

### Intel Mac

- Usually `cpu` only — still fine for learning; use smaller models and batch sizes.

## 3. Memory and performance tips on Mac

| Tip | Why |
|-----|-----|
| Smaller `batch_size` | Unified memory is shared with the OS |
| Close heavy apps | Frees RAM for training |
| Use `float32` unless you need `float16` | MPS mixed precision support evolves |
| Monitor Activity Monitor → Memory | Avoid swap thrashing |

## 4. Install ML utilities

```bash
pip install tqdm scikit-learn pillow opencv-python-headless
pip freeze > ~/python-hero/projects/hello/requirements-ml.txt
```

## 5. TensorFlow (job lists both PyTorch and TensorFlow)

Optional for later lessons:

```bash
pip install tensorflow
python -c "import tensorflow as tf; print(tf.__version__)"
```

On Mac, TensorFlow uses CPU or tensorflow-metal on some setups. Primary course focus remains **PyTorch**.

## 6. Environment variable sanity (optional)

```bash
export PYTORCH_ENABLE_MPS_FALLBACK=1
```

Add to `~/.zshrc` if you hit unsupported MPS ops during training (Lesson 7+).

## Exercise

1. Run `device_check.py` and record which device you got.
2. Create a 1000×1000 random matrix on `device`, multiply it by itself, time with:

```python
import time
start = time.time()
# your matmul
print(time.time() - start)
```

3. Compare CPU vs MPS on Apple Silicon if both work.

## Checklist

- [ ] `import torch` works in venv
- [ ] `device_check.py` runs without error
- [ ] You know whether you are on MPS or CPU

**Next:** [Lesson 00 — Roadmap](../lessons/00-roadmap-and-study-habits.md)
