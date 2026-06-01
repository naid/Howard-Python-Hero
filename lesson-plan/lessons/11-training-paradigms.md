# Lesson 11 — Advanced training paradigms

**Time:** 3 weeks (~25 hours)  
**Prerequisite:** [Lesson 10](10-generative-models.md)  
**Job alignment:** Self-/semi-supervised, multi-task, imitation learning, data collection

## Learning objectives

- Self-supervised learning (SSL)
- Semi-supervised learning
- Multi-task learning
- Imitation learning for driving policies
- Network-driven data collection (active learning intro)

## 1. Self-supervised learning

Labels come from the data itself.

| Method | Idea |
|--------|------|
| Contrastive (SimCLR) | Augmented views of same image should be close in embedding space |
| Masked modeling (MAE, BERT) | Predict masked patches/tokens |
| Next-frame prediction | Predict future from past frames |

Driving example: predict next camera frame or masked road patch — no human label needed.

## 2. Semi-supervised learning

Small labeled set + large unlabeled set.

- Pseudo-labeling: model labels unlabeled data; retrain with confidence threshold
- Consistency regularization: model should agree on augmented versions

## 3. Multi-task learning

One backbone, multiple heads:

```python
class MultiTaskNet(nn.Module):
    def __init__(self):
        super().__init__()
        self.backbone = ...
        self.speed_head = nn.Linear(...)
        self.lane_head = nn.Linear(...)

    def forward(self, x):
        feat = self.backbone(x)
        return self.speed_head(feat), self.lane_head(feat)
```

Loss = weighted sum of task losses. Shared representation improves data efficiency.

## 4. Imitation learning

Learn policy \(\pi(a|s)\) from expert demonstrations (human driver logs).

- **Behavioral cloning:** supervised learning on (state, action) pairs
- Challenge: **distribution shift** — errors compound on road

```python
# Behavioral cloning sketch
loss = criterion(policy(observation), expert_action)
```

Job post: leverage millions of miles of driving data — imitation is central to end-to-end stacks.

## 5. Data engine mindset

1. Train model → find failure modes → collect more data in those scenes → retrain
2. Prioritize **diversity** (weather, lighting, geography) and **quality** (calibration, sync)

Your Lesson 04 audit script is a miniature data engine.

## Exercises

1. SimCLR-style toy experiment on CIFAR-10 subset (use existing tutorial code).
2. Multi-task: predict speed bucket + object presence from shared CNN.
3. Behavioral cloning on [Udacity self-driving simulator CSV](https://github.com/udacity/self-driving-car) (steering angle prediction).

**Next:** [Lesson 12 — Reinforcement learning](12-reinforcement-learning.md)
