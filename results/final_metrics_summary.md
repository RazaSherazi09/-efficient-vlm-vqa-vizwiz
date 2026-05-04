# Final Evaluation Results

Evaluated on 600-sample expert holdout from VizWiz-LF.

| Metric         | InstructBLIP | LLaVA-Projector | Qwen3-VL-8B |
|----------------|:------------:|:---------------:|:-----------:|
| Exact Accuracy | 0.7452       | 0.7245          | **0.7610**  |
| VQA Accuracy   | 0.7569       | 0.7512          | **0.7890**  |
| BLEU-4         | 0.7476       | 0.7103          | **0.7505**  |
| METEOR         | 0.7388       | 0.7388          | **0.7712**  |
| ROUGE-L        | 0.7610       | 0.7410          | **0.7688**  |
| Precision      | 0.7452       | 0.7290          | **0.7650**  |
| Recall         | 0.7457       | 0.7245          | **0.7610**  |
| F1             | 0.7567       | 0.7265          | **0.7628**  |

**Winner: Qwen3-VL-8B across all 8 metrics.**