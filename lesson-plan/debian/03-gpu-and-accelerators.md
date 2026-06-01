# Debian 03 — GPU and accelerators (CUDA + PyTorch)

**Time:** 3–6 hours (longer if installing NVIDIA drivers)  
**Prerequisite:** [02-python-environment](02-python-environment.md)

## Goals

- Install NVIDIA drivers and CUDA toolkit (if you have an NVIDIA GPU)
- Install PyTorch with CUDA support
- Verify GPU training works

## Path A — No NVIDIA GPU

Skip to **Section 4** and use CPU. Learning is possible; large models will be slow. Consider cloud GPUs later (Colab, Lambda, etc.).

## Path B — NVIDIA GPU

### 1. Check GPU

```bash
lspci | grep -i nvidia
nvidia-smi
```

If `nvidia-smi` fails, install drivers:

```bash
sudo apt install -y linux-headers-$(uname -r) build-essential
sudo apt install -y nvidia-driver firmware-misc-nonfree
sudo reboot
```

After reboot:

```bash
nvidia-smi
```

You should see GPU name, driver version, and memory.

### 2. CUDA toolkit

Debian often uses driver-bundled CUDA. For PyTorch, matching versions matter — use [PyTorch Get Started](https://pytorch.org/get-started/locally/) and pick **Linux**, **pip**, **CUDA** version shown compatible.

Example (CUDA 12.1 — verify on pytorch.org for current command):

```bash
source ~/python-hero/venv/bin/activate
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
```

### 3. Verify CUDA in PyTorch

Save `device_check.py`:

```python
import torch

if torch.cuda.is_available():
    device = torch.device("cuda")
    print("GPU:", torch.cuda.get_device_name(0))
    print("CUDA version:", torch.version.cuda)
else:
    device = torch.device("cpu")
    print("CUDA not available — using CPU")

x = torch.ones(3, 3, device=device)
print(x @ x.T)
```

```bash
python device_check.py
```

### 4. CPU-only PyTorch (no GPU)

```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
```

## 5. ML utilities

```bash
pip install tqdm scikit-learn pillow opencv-python-headless
pip freeze > ~/python-hero/projects/hello/requirements-ml.txt
```

## 6. TensorFlow with GPU (optional, later)

```bash
pip install tensorflow[and-cuda]
```

Primary framework for this course: **PyTorch**.

## 7. Multi-GPU note (advanced, Lesson 13)

`nvidia-smi` listing multiple GPUs means you can use `torch.nn.DataParallel` or **DistributedDataParallel** later. Not required now.

## 8. Monitor GPU while training

```bash
watch -n 1 nvidia-smi
```

## Exercise

1. Run `device_check.py` — record CPU vs CUDA.
2. Time matrix multiply 1000×1000 on GPU vs CPU.
3. Note GPU model and VRAM from `nvidia-smi`.

## Checklist

- [ ] `import torch` works in venv
- [ ] You know CPU vs CUDA status
- [ ] `requirements-ml.txt` saved

**Next:** [Lesson 00 — Roadmap](../lessons/00-roadmap-and-study-habits.md)
