# AccessVQA — Explainable VQA for Visually Impaired Users

<div align="center">
  
![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0%2B-ee4c2c?logo=pytorch&logoColor=white)
![HuggingFace](https://img.shields.io/badge/HuggingFace-Transformers-F9AB00?logo=huggingface&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success)

> **Two-stage curriculum learning pipeline for long-form, explainable Visual Question Answering targeting accessibility scenarios.**

</div>

---

## 📖 Project Overview

This project builds and evaluates an **Explainable Visual Question Answering (VQA)** system specifically designed to assist visually impaired users. By leveraging state-of-the-art Vision-Language Models (VLMs), the system generates detailed, faithful, and contextually rich answers to real-world visual questions.

### The Pipeline
Our approach utilizes a robust curriculum learning pipeline:
- **Stage 1:** Domain adaptation on the VizWiz dataset (focusing on short, highly accurate answers).
- **Stage 2:** Fine-tuning on the **VizWiz-LF** dataset to generate long-form, explainable, and descriptive answers tailored for enhanced accessibility.

---

## 🧠 Models & Strategies

We experimented with three distinct architectures, utilizing efficient fine-tuning strategies to maximize performance within limited compute constraints:

| Model | Architecture | Training Strategy |
|-------|-------------|----------|
| **InstructBLIP** | Vicuna-7B + Q-Former | 8-bit Supervised Fine-Tuning (SFT) |
| **LLaVA** | CLIP + Phi-3-mini + MLP | Projector-only training |
| **Qwen3-VL-8B** | Qwen3-VL + QLoRA | 4-bit NF4, targeting `q_proj` & `v_proj` |

---

## 📊 Quantitative Results

The models were evaluated on a 600-sample expert holdout from VizWiz-LF. As detailed below, **Qwen3-VL-8B** consistently outperformed the other models across all evaluated metrics.

<div align="center">
  <img src="assets/NLG%20Metrics%20-%20All%20Models.png" width="48%" alt="NLG Metrics Comparison">
  <img src="assets/Classification%20Metrics%20-%20All%20Models.png" width="48%" alt="Classification Metrics Comparison">
</div>

<br>

| Metric | InstructBLIP | LLaVA-Projector | Qwen3-VL-8B |
|--------|:---:|:---:|:---:|
| **Exact Accuracy** | 0.7452 | 0.7245 | **0.7610 🏆** |
| **VQA Accuracy** | 0.7569 | 0.7512 | **0.7890 🏆** |
| **BLEU-4** | 0.7476 | 0.7103 | **0.7505 🏆** |
| **METEOR** | 0.7388 | 0.7388 | **0.7712 🏆** |
| **ROUGE-L** | 0.7610 | 0.7410 | **0.7688 🏆** |
| **Precision** | 0.7452 | 0.7290 | **0.7650 🏆** |
| **Recall** | 0.7457 | 0.7245 | **0.7610 🏆** |
| **F1 Score** | 0.7567 | 0.7265 | **0.7628 🏆** |

*(Additional visualizations, including confusion matrices and training loss curves, are available in the [`assets/`](assets/) directory.)*

---

## 📂 Repository Structure

The core experimentation and training workflows are organized cleanly into Jupyter Notebooks:

| File | Description |
|----------|-------------|
| 📓 [`notebooks/VIZWIZ.ipynb`](notebooks/VIZWIZ.ipynb) | Exploratory Data Analysis & baseline setup. |
| 📓 [`notebooks/notebook#1_Instructblip.ipynb`](notebooks/notebook#1_Instructblip.ipynb) | InstructBLIP fine-tuning on VizWiz-LF. |
| 📓 [`notebooks/notebook#2_llava.ipynb`](notebooks/notebook#2_llava.ipynb) | LLaVA MLP projector training & evaluation. |
| 📓 [`notebooks/notebook#3_qwen3.ipynb`](notebooks/notebook#3_qwen3.ipynb) | Qwen3-VL-8B QLoRA single-stage SFT & evaluation. |

---

## 💾 Dataset

- **[VizWiz](https://vizwiz.org/)** — A dataset consisting of real-world visual questions sourced directly from blind individuals.
- **VizWiz-LF** — A long-form answer extension enriched with synthetic and expert annotations to facilitate high-quality explainability.

---

## 🛠️ Environment & Setup

### Hardware
- **Platform:** Kaggle
- **Compute:** Dual Tesla T4 (2×16GB VRAM)

### Requirements
Ensure you have the required dependencies installed to replicate the environment. Python 3.8+ is recommended.

```bash
pip install -r requirements.txt
```

Key libraries include:
- `torch >= 2.0.0`
- `transformers >= 4.40.0`
- `peft >= 0.10.0`
- `bitsandbytes >= 0.43.0`
- `accelerate >= 0.27.0`

---

## 📦 HuggingFace Checkpoints

Pre-trained weights and adapters from our best runs are publicly accessible on HuggingFace:

- **InstructBLIP weights:** [`Abdullah-Khan-Niazi/instructblip-vizwiz-lf`](https://huggingface.co/Abdullah-Khan-Niazi/instructblip-vizwiz-lf)
- **LLaVA projector:** [`Abdullah-Khan-Niazi/vizwiz-lf-llava-projector`](https://huggingface.co/Abdullah-Khan-Niazi/vizwiz-lf-llava-projector)
- **Qwen3-VL adapter:** [`Abdullah-Khan-Niazi/vizwiz-lf-qwen3vl`](https://huggingface.co/Abdullah-Khan-Niazi/vizwiz-lf-qwen3vl)

---

## 👨‍💻 Author

- **Roll No:** `23F-0040`