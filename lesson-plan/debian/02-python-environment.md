# Debian 02 — Python environment

**Time:** 2–3 hours  
**Prerequisite:** [01-system-setup](01-system-setup.md)

## Goals

- Install Python 3.11+ on Debian
- Create and use virtual environments
- Run your first Python program

## 1. Install Python

Debian 12 includes Python 3.11:

```bash
sudo apt install -y python3 python3-pip python3-venv python3-dev
python3 --version
```

For **Python 3.12** (optional):

```bash
sudo apt install -y python3.12 python3.12-venv python3.12-dev
# Use python3.12 below instead of python3 if you prefer 3.12
```

## 2. Upgrade pip inside projects only

Never `sudo pip install` globally — it breaks system packages.

```bash
cd ~/python-hero
python3 -m venv venv
source ~/python-hero/venv/bin/activate
python -m pip install --upgrade pip setuptools wheel
```

Prompt shows `(venv)`.

Deactivate:

```bash
deactivate
```

## 3. First Python program

```bash
source ~/python-hero/venv/bin/activate
mkdir -p ~/python-hero/projects/hello
cd ~/python-hero/projects/hello
```

Create `main.py` with `nano main.py`:

```python
name = input("What is your name? ")
print(f"Hello, {name}! Welcome to Python Hero.")
```

Run:

```bash
python main.py
```

## 4. Early learning packages

```bash
pip install numpy pandas matplotlib jupyter ipython
python -c "import numpy; import pandas; print('OK')"
```

## 5. Jupyter (optional)

```bash
pip install notebook
jupyter notebook --no-browser
```

On a remote server, SSH port forwarding:

```bash
# From your local machine:
ssh -L 8888:localhost:8888 user@server
```

Then open the URL Jupyter prints (with token) in your local browser.

## 6. requirements.txt

```bash
pip freeze > requirements.txt
```

Restore elsewhere:

```bash
pip install -r requirements.txt
```

## 7. Common Debian issues

| Problem | Fix |
|---------|-----|
| `externally-managed-environment` | Always use a venv; do not pip install system-wide |
| Missing `python3-dev` | `sudo apt install python3-dev` before pip installs that compile C code |
| `ModuleNotFoundError` | Activate venv; confirm `which python` points inside `venv` |

## Exercise

1. Venv at `~/python-hero/venv`
2. `circle_area.py`: radius input → print area
3. `requirements.txt` with numpy, pandas, matplotlib

## Checklist

- [ ] `python3 --version` ≥ 3.11
- [ ] venv activates
- [ ] `main.py` runs
- [ ] numpy imports inside venv

**Next:** [03-gpu-and-accelerators](03-gpu-and-accelerators.md)
