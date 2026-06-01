# Lesson 09 — Transformers and large language models

**Time:** 3 weeks (~30 hours)  
**Prerequisite:** [Lesson 08](08-cnns-computer-vision.md)  
**Job alignment:** GPT, foundation models, multi-modal systems (language side)

## Learning objectives

- Attention mechanism
- Transformer encoder/decoder
- GPT-style causal language modeling
- Hugging Face ecosystem for fine-tuning

## 1. Why transformers

- Capture long-range dependencies in sequences (text, tokens, patches)
- Parallelizable training vs RNNs
- Foundation for **GPT**, BERT, ViT (vision transformer)

## 2. Self-attention (intuition)

Each token produces Query, Key, Value vectors. Attention weights:

\[
\text{Attention}(Q,K,V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V
\]

## 3. GPT = decoder-only stack

Predict next token:

```
"The car will" → predict "stop"
```

Training objective: cross-entropy on next-token prediction (self-supervised).

## 4. Hugging Face quickstart

```bash
pip install transformers datasets accelerate
```

```python
from transformers import AutoTokenizer, AutoModelForCausalLM

tokenizer = AutoTokenizer.from_pretrained("gpt2")
model = AutoModelForCausalLM.from_pretrained("gpt2")

inputs = tokenizer("The vehicle detected a pedestrian", return_tensors="pt")
outputs = model.generate(**inputs, max_new_tokens=20)
print(tokenizer.decode(outputs[0]))
```

## 5. Fine-tuning (LoRA overview)

Full fine-tune of billion-parameter models is expensive. **LoRA** (Low-Rank Adaptation) trains small adapter matrices — common in production.

```bash
pip install peft
```

Follow Hugging Face PEFT docs for a small text classification or generation task.

## 6. Vision transformer (ViT) — bridge to multi-modal

Images split into patches; patches treated as tokens. Connects CNN world to transformer world (relevant for **multi-modal generative models** in the job post).

## Readings

- Paper: [Attention Is All You Need](https://arxiv.org/abs/1706.03762)
- Paper: [Language Models are Unsupervised Multitask Learners](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf) (GPT-2)

## Exercises

1. Tokenize sentences; inspect token IDs and attention mask.
2. Fine-tune DistilBERT on small text classification dataset (AG News).
3. Summarize how GPT differs from BERT (causal vs bidirectional).

## Mini-project

Fine-tune a small LM or classifier on domain text (e.g. synthetic "driving incident reports").

**Next:** [Lesson 10 — Generative models](10-generative-models.md)
