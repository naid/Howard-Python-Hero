# Lesson 14 — Capstone: autonomy-oriented project

**Time:** 4–6 weeks (~40+ hours)  
**Prerequisite:** Lessons 00–13  
**Job alignment:** End-to-end learning, world modeling, portfolio / publication path

## Goal

Build one **portfolio centerpiece** that demonstrates you can:

1. Curate or synthesize driving-related data
2. Train a PyTorch model (vision, prediction, or policy)
3. Evaluate rigorously with clear metrics
4. Document reproducibility like production ML

## Project options (pick one)

### Option A — Behavioral cloning steering predictor

- Data: [Udacity driving dataset](https://github.com/udacity/self-driving-car/tree/master/datasets/CH2) or simulator logs
- Model: CNN (ResNet18) → steering angle
- Metrics: MAE, visualization of predicted vs expert steering
- Stretch: add speed as multi-task head

### Option B — Next-frame / world-model lite

- Data: sequential dashcam frames (public dataset or synthetic)
- Model: ConvLSTM or small U-Net
- Metrics: MSE / perceptual loss on predicted frame
- Stretch: predict multiple future steps

### Option C — Driving scene classifier + data engine

- Data: labeled road images (weather, time of day)
- Build pipeline: ingest → audit → train → error analysis → re-collect hard cases
- Metrics: F1 per class; report on data quality iterations

### Option D — Offline RL / imitation comparison (advanced)

- Simulator: CartPole or CARLA subset
- Compare BC vs offline RL (Stable-Baselines3)
- Write up distribution shift findings

## Required deliverables

```
capstone/
├── README.md              # Problem, approach, results, ethics note
├── requirements.txt
├── configs/
│   └── default.yaml
├── src/
│   ├── data/
│   ├── models/
│   ├── train.py
│   └── evaluate.py
├── tests/
├── notebooks/               # optional EDA
└── checkpoints/
```

### README must include

- **Problem statement** — what autonomy sub-problem you address
- **Dataset** — source, size, license, splits
- **Model** — architecture diagram or description
- **Training** — hardware (Mac MPS / Debian GPU), hyperparameters
- **Results** — tables, plots, failure case images
- **Reproduction** — exact commands to train and evaluate
- **Future work** — what Tesla-scale data/engine would add

## Suggested timeline

| Week | Milestone |
|------|-----------|
| 1 | Data audit + baseline model |
| 2 | Training pipeline + validation metrics |
| 3 | Improvements (augmentation, multi-task, or world-model steps) |
| 4 | Tests, export, README, demo video or GIF |
| 5–6 | Polish, optional blog post, apply to internships |

## Evaluation rubric (self-grade)

| Criterion | Target |
|-----------|--------|
| Code quality | pytest, ruff, typed core functions |
| ML rigor | Held-out test set, no leakage |
| Relevance | Clear tie to autonomy / perception / prediction |
| Communication | README understandable to a hiring engineer |
| Ambition | At least one "stretch" item attempted |

## Applying to the Tesla role

Highlight in resume / cover letter:

- Capstone repo link
- Specific overlap: PyTorch, CNNs, generative/world models, RL/imitation, data curation
- Quantified results (MAE, accuracy, latency ms)
- Team collaboration (OSS contributions, group projects) if applicable

## Publications path (optional)

If aiming for **first-author conference papers**:

1. Reproduce a known baseline on a public driving benchmark
2. Introduce one clear improvement (data, architecture, training objective)
3. Ablations prove what helped
4. Target workshops: NeurIPS MLSys, ICRA, CoRL (robotics/ML overlap)

## Final checklist

- [ ] GitHub repo public with MIT/Apache license
- [ ] `pytest` passes; `ruff` clean
- [ ] Demo artifact (GIF, short video, or Colab link)
- [ ] Linked from resume and LinkedIn
- [ ] Practiced 2-minute verbal pitch

## Congratulations

You completed the Python Hero curriculum aligned with the Tesla AI Engineering Intern skill set. Keep shipping small experiments — hiring teams care about **velocity and depth**, not checking every box once.

Return to [main README](../README.md) for the full course map.
