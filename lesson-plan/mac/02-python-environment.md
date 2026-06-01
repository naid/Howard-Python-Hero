# Mac 02 — Python environment

**Time:** 2–3 hours  
**Prerequisite:** [01-system-setup](01-system-setup.md)

## Goals

- Install Python 3.11 or newer
- Use virtual environments (isolated project dependencies)
- Run your first Python program

## 1. Install Python with Homebrew

```bash
brew install python@3.12
```

Verify:

```bash
python3 --version
# Should show Python 3.12.x

which python3
# Often /opt/homebrew/bin/python3
```

## 2. `pip` and upgrading tools

```bash
python3 -m pip install --upgrade pip setuptools wheel
```

Always use `python3 -m pip` instead of bare `pip` to avoid installing into the wrong Python.

## 3. Virtual environments

A **venv** keeps each project’s packages separate — critical for ML (PyTorch versions conflict easily).

```bash
cd ~/python-hero
python3 -m venv venv
```

Activate (you must do this in **every new Terminal window** for this project):

```bash
source ~/python-hero/venv/bin/activate
```

Your prompt should show `(venv)`.

Deactivate when done:

```bash
deactivate
```

### Auto-activate tip (optional)

```bash
echo 'source ~/python-hero/venv/bin/activate' >> ~/.zshrc
```

Only do this if `~/python-hero` is your main workspace.

## 4. First Python program

With venv activated:

```bash
mkdir -p ~/python-hero/projects/hello
cd ~/python-hero/projects/hello
```

Create `main.py`:

```python
name = input("What is your name? ")
print(f"Hello, {name}! Welcome to Python Hero.")
```

Run:

```bash
python main.py
```

## 5. Install early learning packages

```bash
pip install numpy pandas matplotlib jupyter ipython
```

Test imports:

```bash
python -c "import numpy; import pandas; print('OK')"
```

## 6. Jupyter Notebook (optional)

```bash
pip install notebook
cd ~/python-hero/projects/hello
jupyter notebook
```

Browser opens; create a notebook and run:

```python
import numpy as np
np.arange(5)
```

Stop the server with `Ctrl+C` in Terminal.

## 7. `requirements.txt` habit

After installing packages for a project:

```bash
pip freeze > requirements.txt
```

Later, on another machine:

```bash
pip install -r requirements.txt
```

You will use this in every lesson project.

## 8. Common Mac issues

| Problem | Fix |
|---------|-----|
| `command not found: python` | Use `python3`, not `python` |
| `permission denied` on pip | Activate venv first; never `sudo pip` |
| Wrong package version | `pip install package==1.2.3` |
| SSL errors with pip | `brew install openssl`; retry pip |

## Exercise

1. Create venv at `~/python-hero/venv` if not done.
2. Script `circle_area.py`: ask for radius, print area using `3.14159 * r ** 2`.
3. Save `requirements.txt` with numpy, pandas, matplotlib versions.

## Checklist

- [ ] `python3 --version` ≥ 3.11
- [ ] venv activates with `source .../activate`
- [ ] `main.py` runs
- [ ] `import numpy` succeeds inside venv

**Next:** [03-gpu-and-accelerators](03-gpu-and-accelerators.md)
