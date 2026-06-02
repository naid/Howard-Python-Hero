# PyTorch Lesson 07 — Mini trainer project

**Time:** 6–8 hours  
**Prerequisite:** Lessons 01–06

## Project goal

Build a reusable mini training library for **tabular** or **MNIST** data:

```
mini_trainer/
├── README.md
├── train.py
├── model.py
├── data.py
└── checkpoints/
```

Requirements:

- `get_device()` helper
- `train_epoch` and `evaluate` functions
- Save best checkpoint by validation loss
- CLI: `python train.py --epochs 10` (with venv active — see below)

## Run

From your project folder:

```bash
source ~/python-hero/venv/bin/activate
cd ~/python-hero/practice/pytorch/lesson07/mini_trainer
python train.py --epochs 10
```

## Starter structure

`model.py` — define MLP or SmallCNN  
`data.py` — return train/val DataLoaders  
`train.py` — argparse for epochs and lr

---

## Exercises

Folder: `~/python-hero/practice/pytorch/lesson07/`

Activate your venv before running `train.py` or other scripts:

```bash
source ~/python-hero/venv/bin/activate
```

### Exercise 1 — Project skeleton

Create files above with empty functions, import without errors.

**Check:** [Answer](../answers/07-mini-trainer-project-answers.md#exercise-1--project-skeleton)

### Exercise 2 — Train MNIST 5 epochs

Achieve **>90%** test accuracy on full MNIST (or document hardware limits if subset used).

**Check:** [Answer](../answers/07-mini-trainer-project-answers.md#exercise-2--train-mnist-5-epochs)

### Exercise 3 — README

Document: install, run command, final accuracy, device used (cpu/mps/cuda).

**Check:** [Answer](../answers/07-mini-trainer-project-answers.md#exercise-3--readme)

### Exercise 4 — Loss plot (stretch)

Save train/val loss per epoch to `history.csv` or plot with matplotlib.

**Check:** [Answer](../answers/07-mini-trainer-project-answers.md#exercise-4--loss-plot-stretch)

---

[All answers](../answers/07-mini-trainer-project-answers.md)

**Next:** Advanced track in [`../../lessons/`](../../lessons/) (ML theory, transformers, capstone)
