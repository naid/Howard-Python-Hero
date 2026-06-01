# Lesson 10 — Generative models, diffusion, and video / world modeling

**Time:** 3 weeks (~30 hours)  
**Prerequisite:** [Lesson 09](09-transformers-and-llms.md)  
**Job alignment:** Generative models, diffusion, generative videos, world modeling

## Learning objectives

- Generative vs discriminative models
- VAEs and GANs (concepts)
- Diffusion models (DDPM intuition)
- Video prediction and world models (high level)
- Multi-modal generative pipelines

## 1. Generative modeling goal

Learn distribution \(p(x)\) to **generate** new samples (images, video frames, trajectories).

Job post emphasis: **generative videos**, **world modeling** — predicting how scenes evolve.

## 2. GAN (sketch)

- **Generator** \(G\): noise → fake image
- **Discriminator** \(D\): real vs fake
- Adversarial training (can be unstable)

## 3. Diffusion (modern standard)

1. Forward process: gradually add noise to image
2. Reverse process: neural net predicts noise to remove
3. Sample by iterative denoising

```python
# High-level: use diffusers library
pip install diffusers
```

```python
from diffusers import StableDiffusionPipeline
# Use smaller models on Mac / limited VRAM for learning
```

On Mac: prefer smaller checkpoints; reduce resolution; use CPU/MPS with patience.

## 4. World models (autonomy context)

A **world model** predicts future states of the environment:

- Input: past camera frames + vehicle actions
- Output: predicted future frames or latent states
- Used for planning and simulation (learn without only real-world rollouts)

Conceptual loop:

```
observe → predict future → plan action → execute
```

## 5. Video networks

Video = sequence of frames + temporal consistency.

Architectures:

- 3D convolutions (C3D)
- ConvLSTM
- Transformer over patch tokens (VideoGPT-style)

Exercise: stack 16 frames as channels or use `torch.nn.Conv3d` on clip tensor `(B, C, T, H, W)`.

## 6. Multi-modal generative models

Combine text + image (+ sensor):

- CLIP: aligned image/text embeddings
- Stable Diffusion: text conditions image generation

Relevant to **compound AI systems** in the job description.

## Readings

- [DDPM paper](https://arxiv.org/abs/2006.11239)
- [World Models (Ha & Schmidhuber)](https://arxiv.org/abs/1803.10122) — historical but instructive

## Exercises

1. Train tiny VAE on MNIST (reconstruction loss).
2. Run pretrained diffusion demo; document GPU/RAM needs on your machine.
3. Write one-page note: how world models could reduce real-world test miles for self-driving.

## Mini-project

**Frame prediction:** given 4 consecutive grayscale driving-style frames (synthetic or dashcam subset), predict 5th frame with a small Conv3D or U-Net.

**Next:** [Lesson 11 — Training paradigms](11-training-paradigms.md)
