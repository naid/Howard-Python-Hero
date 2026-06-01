# Python Hero: Lesson Plan for Tesla AI Engineering Intern Readiness

This curriculum takes you from **zero programming experience** to the skills described in the Tesla AI Engineering Intern (Summer 2026) posting: Python, PyTorch, deep learning theory, computer vision, LLMs, generative models, reinforcement learning, distributed training, and production ML habits.

## How to use this course

1. **Pick your operating system track** and complete it before Lesson 1:
   - [Mac users](mac/README.md) — macOS setup, Homebrew, Python, PyTorch with MPS (Apple Silicon)
   - [Linux (Debian) users](debian/README.md) — Debian setup, apt, Python, PyTorch with CUDA (NVIDIA GPU)

2. **Learn Python first, then PyTorch** (recommended for beginners):
   - [Python track](python/README.md) — 8 lessons with exercises + [answer keys](python/answers/)
   - [PyTorch track](pytorch/README.md) — 7 lessons with exercises + [answer keys](pytorch/answers/)

3. **Advanced topics** — continue under [`lessons/`](lessons/) (ML theory, transformers, RL, capstone).

4. **Study cadence:** ~10–15 hours per week → roughly **36 weeks** (9 months). Adjust pace as needed.

5. **Practice rule:** Do every exercise before opening the linked answer file. Type code yourself; do not only read.

## Job skills map

| Job requirement | Where you learn it |
|-----------------|-------------------|
| Python & software engineering | Lessons 1–3 |
| PyTorch, TensorFlow, CNNs, GPT | Lessons 5–10 |
| Loss functions, optimization, layers | Lesson 6 |
| Computer vision, video networks | Lessons 8, 10 |
| LLMs, generative & diffusion models | Lessons 9–10 |
| Self-/semi-supervised, multi-task learning | Lesson 11 |
| Imitation & reinforcement learning | Lesson 12 |
| Dataset curation, data engines | Lessons 4, 11 |
| Sparse training, pruning, latency | Lesson 13 |
| Distributed & large-scale training | Lessons 7, 13 |
| Production / safety-critical habits | Lessons 3, 13–14 |
| World modeling & autonomy capstone | Lesson 14 |

## Curriculum phases

### Phase 0 — Environment (Week 1)
| Step | Mac | Debian |
|------|-----|--------|
| System & tools | [01-system-setup](mac/01-system-setup.md) | [01-system-setup](debian/01-system-setup.md) |
| Python & venv | [02-python-environment](mac/02-python-environment.md) | [02-python-environment](debian/02-python-environment.md) |
| GPU / accelerator | [03-gpu-and-accelerators](mac/03-gpu-and-accelerators.md) | [03-gpu-and-accelerators](debian/03-gpu-and-accelerators.md) |

### Phase 1 — Python foundations (Weeks 2–5)
| Lesson | Topic |
|--------|--------|
| [00-roadmap](lessons/00-roadmap-and-study-habits.md) | How to learn, glossary, job alignment |
| [01-python-basics](lessons/01-python-basics.md) | Variables, types, control flow, functions |
| [02-python-intermediate](lessons/02-python-intermediate.md) | OOP, files, errors, modules, comprehensions |

### Phase 2 — Engineering discipline (Weeks 6–7)
| Lesson | Topic |
|--------|--------|
| [03-software-engineering](lessons/03-software-engineering.md) | Git, tests, linting, project layout, debugging |

### Phase 3 — Data & classical ML (Weeks 8–10)
| Lesson | Topic |
|--------|--------|
| [04-numpy-pandas-data](lessons/04-numpy-pandas-data.md) | NumPy, Pandas, visualization, dataset curation |
| [05-ml-foundations](lessons/05-ml-foundations.md) | Train/val/test, metrics, scikit-learn pipelines |

### Phase 4 — Deep learning theory (Weeks 11–13)
| Lesson | Topic |
|--------|--------|
| [06-deep-learning-theory](lessons/06-deep-learning-theory.md) | Neurons, layers, losses, optimizers, backprop |

### Phase 5 — PyTorch & vision (Weeks 14–18)
| Lesson | Topic |
|--------|--------|
| [07-pytorch-fundamentals](lessons/07-pytorch-fundamentals.md) | Tensors, autograd, training loops, DataLoader |
| [08-cnns-computer-vision](lessons/08-cnns-computer-vision.md) | CNNs, image classification, transfer learning |

### Phase 6 — Modern AI stack (Weeks 19–24)
| Lesson | Topic |
|--------|--------|
| [09-transformers-and-llms](lessons/09-transformers-and-llms.md) | Attention, transformers, GPT-style models |
| [10-generative-models](lessons/10-generative-models.md) | VAEs, diffusion, video & world-modeling intro |

### Phase 7 — Advanced training (Weeks 25–30)
| Lesson | Topic |
|--------|--------|
| [11-training-paradigms](lessons/11-training-paradigms.md) | SSL, semi-supervised, multi-task, imitation learning |
| [12-reinforcement-learning](lessons/12-reinforcement-learning.md) | RL, offline/off-policy, RL for training |
| [13-efficient-training-and-deployment](lessons/13-efficient-training-and-deployment.md) | Pruning, distributed training, TensorFlow, production |

### Phase 8 — Capstone (Weeks 31–36)
| Lesson | Topic |
|--------|--------|
| [14-capstone-autonomy-project](lessons/14-capstone-autonomy-project.md) | End-to-end project aligned with autonomy / world modeling |

## Recommended resources (free unless noted)

- [Python official tutorial](https://docs.python.org/3/tutorial/)
- [PyTorch tutorials](https://pytorch.org/tutorials/)
- [fast.ai Practical Deep Learning](https://course.fast.ai/) (optional parallel track)
- [Spinning Up in RL](https://spinningup.openai.com/) (Lesson 12 supplement)
- Papers: Attention Is All You Need, ResNet, DDPM, GPT-2/3 (linked in lessons)

## Progress checklist

Copy this into your notes and check off as you go:

```
[ ] Mac OR Debian setup track complete
[ ] Lessons 00–03
[ ] Lessons 04–06
[ ] Lessons 07–08
[ ] Lessons 09–10
[ ] Lessons 11–13
[ ] Lesson 14 capstone + portfolio README
```

## Folder structure

```
lesson-plan/
├── README.md                 ← you are here
├── mac/                      ← macOS-only setup
├── debian/                   ← Debian-only setup
├── python/
│   ├── lessons/              ← Python lessons (with exercise links)
│   └── answers/              ← Answer keys (check after trying)
├── pytorch/
│   ├── lessons/              ← PyTorch lessons (with exercise links)
│   └── answers/              ← Answer keys
└── lessons/                  ← advanced shared curriculum
```

Good luck — consistency beats intensity. Ship small projects every phase.
