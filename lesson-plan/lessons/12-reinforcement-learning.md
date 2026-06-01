# Lesson 12 — Reinforcement learning

**Time:** 3 weeks (~30 hours)  
**Prerequisite:** [Lesson 11](11-training-paradigms.md)  
**Job alignment:** RL for robustness, offline/off-policy RL, RL for training

## Learning objectives

- MDP: states, actions, rewards
- Policy vs value functions
- Q-learning and DQN (basics)
- Policy gradients (REINFORCE sketch)
- Offline / off-policy RL
- RL for training (RLHF-style overview)

## 1. Markov Decision Process

- **State** \(s\) — observation (sensors, latent)
- **Action** \(a\) — steer, throttle, brake
- **Reward** \(r\) — +1 stay in lane, -100 crash
- **Policy** \(\pi(a|s)\) — what to do
- **Goal** — maximize cumulative reward

## 2. Exploration vs exploitation

Agent must try actions to discover better strategies — not only copy the expert.

## 3. Q-learning (tabular intuition)

Learn \(Q(s,a)\) = expected return from taking \(a\) in \(s\).

Update:

\[
Q(s,a) \leftarrow Q(s,a) + \alpha [r + \gamma \max_{a'} Q(s',a') - Q(s,a)]
\]

## 4. DQN (deep Q-network)

Neural net approximates \(Q\). Experience replay + target network for stability.

```bash
pip install gymnasium
```

```python
import gymnasium as gym
env = gym.make("CartPole-v1")
```

CartPole is the "hello world" of RL — master before driving simulators.

## 5. Policy gradients

Directly optimize policy parameters:

\[
\nabla_\theta J(\theta) \approx \mathbb{E}[\nabla_\theta \log \pi_\theta(a|s) \cdot R]
\]

Algorithms: REINFORCE, PPO, SAC — common in robotics and games.

## 6. Offline / off-policy RL

**Problem:** Cannot run millions of unsafe trials on real roads.

**Offline RL:** Learn from fixed logged dataset (Tesla's miles of driving + interventions).

- Off-policy: learn about one policy while data comes from another (e.g. human driver)
- Challenges: distributional shift, overestimation

Read: [Offline Reinforcement Learning: Tutorial, Review](https://arxiv.org/abs/2005.01643)

## 7. RL for training (RLHF-style)

Use RL to optimize a **model** (not only a vehicle):

- Reward model scores outputs
- Fine-tune LLM with PPO to maximize reward
- Job post: "RL for training" — aligns objectives (safety, style, task success)

## 8. Simulators for autonomy RL

- [CARLA](https://carla.org/) — driving simulator (heavy; Linux-friendly)
- [gymnasium](https://gymnasium.farama.org/) — lightweight start

## Exercises

1. Solve CartPole with a tutorial DQN (Stable-Baselines3 acceptable).
2. Compare behavioral cloning vs RL on a toy environment.
3. Write summary: why offline RL matters for self-driving.

```bash
pip install stable-baselines3 shimmy
```

## Mini-project

Train PPO or DQN on `CartPole-v1`; plot reward curve; save policy.

**Next:** [Lesson 13 — Efficient training and deployment](13-efficient-training-and-deployment.md)
