# AccessVQA — Explainable VQA for Visually Impaired Users

> Two-stage curriculum learning pipeline for long-form, explainable 
> Visual Question Answering targeting accessibility scenarios.

---

## Project Overview

This project builds and evaluates an Explainable VQA system designed 
to assist visually impaired users by generating detailed, faithful 
answers to visual questions.

**Pipeline:**
- Stage 1: Domain adaptation on VizWiz (short answers)
- Stage 2: Fine-tuning on VizWiz-LF (long-form explainable answers)

---

## Models

| Model | Architecture | Strategy |
|-------|-------------|----------|
| InstructBLIP | Vicuna-7B + Q-Former | 8-bit SFT |
| LLaVA-Projector | CLIP + Phi-3-mini + MLP | Projector-only training |
| Qwen3-VL-8B | Qwen3-VL + QLoRA | 4-bit NF4, q_proj & v_proj |

---

## Results

![Metrics Comparison](assets/nlg_metrics_comparison.png)

| Metric | InstructBLIP | LLaVA | Qwen3-VL |
|--------|:---:|:---:|:---:|
| VQA Accuracy | 0.757 | 0.751 | **0.789** |
| BLEU-4 | 0.748 | 0.710 | **0.751** |
| ROUGE-L | 0.761 | 0.741 | **0.769** |
| F1 | 0.757 | 0.727 | **0.763** |

**Qwen3-VL-8B (QLoRA) achieves best performance across all metrics.**

---

## Notebooks

| Notebook | Description |
|----------|-------------|
| `notebook_1_instructblip.ipynb` | InstructBLIP fine-tuning on VizWiz-LF |
| `notebook_2_llava_projector.ipynb` | LLaVA MLP projector training |
| `notebook_3_qwen3_qlora.ipynb` | Qwen3-VL-8B QLoRA single-stage SFT |
| `notebook_4_inference_evaluation.ipynb` | Inference, metrics & comparison plots |

---

## Environment

- Platform: Kaggle (Dual Tesla T4, 2×16GB VRAM)
- Framework: PyTorch 2.10 + HuggingFace Transformers
- Quantization: BitsAndBytes (4-bit NF4 / 8-bit)

---

## Dataset

- [VizWiz](https://vizwiz.org/) — Visual questions from blind users
- VizWiz-LF — Long-form answer extension with synthetic + expert answers

---

## HuggingFace Models

- InstructBLIP weights: `Abdullah-Khan-Niazi/instructblip-vizwiz-lf`
- LLaVA projector: `Abdullah-Khan-Niazi/vizwiz-lf-llava-projector`
- Qwen3-VL adapter: `Abdullah-Khan-Niazi/vizwiz-lf-qwen3vl`

---

## Roll No: 23F-0040