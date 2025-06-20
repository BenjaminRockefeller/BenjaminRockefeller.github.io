---
layout: page
title: "Project 2｜Intelligent Quantitative Strategy Generation Platform"
permalink: /projects/project2/
description: "Causality-Aware and RLHF-Based Backtesting Optimization System"
importance: 2
category: work
related_publications: false
---

## ✅ Project 2｜Intelligent Quantitative Strategy Generation Platform

### Causality-Aware and RLHF-Based Backtesting Optimization System  
*(Supporting Closed-Loop Strategy Generation, Multi-Task Distillation, and Reinforcement Learning with Backtest Feedback)*

---

#### Project Overview

This project tackles persistent pain points in quant strategy development: unverifiable outputs, missing causal structures, and high deployment cost. It proposes a closed-loop generation system unifying strategy generation, causal graph extraction, RLHF optimization, and backtesting feedback into a production-ready pipeline.

---

#### Project Contributions

- Constructed a high-quality multi-source corpus of 800K+ items, spanning:  
  1. 12,000 strategy summaries  
  2. 11,000 indicator chains  
  3. 9,000 causal market graphs

- Resolved noisy/heterogeneous inputs with rule-based extraction (spaCy + tree parser) and entity alignment via graph databases. Structural consistency improved from 71.2% → 94.6%.

- Designed a multi-task distillation system with LLaMA‑2‑7B (teacher); trained with soft-labels (T=2.0) and balanced 3 loss functions (0.4:0.4:0.2) to support generalization across tasks.

- Created a 3-dimensional reward function for RLHF:  
  1. **Causal Coverage**  
  2. **Contextual Coherence**  
  3. **Backtest Return Stability**  
     Implemented reward clipping, early baseline, and dynamic weighting to prevent collapse.

- Introduced a full backtest feedback loop:  
  - Generated strategies converted to Python scripts  
  - Simulated via Backtrader  
  - Return, Sharpe, Drawdown metrics used as third RLHF reward  
    → Forming a **generate → simulate → retrain** loop.

- Deployed on RTX 3090 with QLoRA + TensorRT INT4 compression (−65% size); latency = 270ms, throughput = 26 req/s.

---

#### Experimental Results

| Metric                        | Value     |
| ----------------------------- | --------- |
| BLEU Improvement              | +14.6%    |
| Redundancy Reduction          | −21.2%    |
| Causal Path Accuracy          | 85.4%     |
| Strategy Simulation Success   | 78.9%     |
| Expert Rating                 | 4.7 / 5.0 |
| RLHF Convergence Acceleration | +32%      |

---

#### Optimization & Future Directions

- **Ablation Study**: Built 3 variants (no causal / no RL / no backtest) to analyze contribution paths.  
- **Visualization Tools**: D3.js + Plotly visualizations of causal graphs, returns, prompt-generation flow.  
- **Model Portability**: Adapted to InternLM, Mistral-7B, Yi-6B with <2.7% consistency error.  
- **Self-Adaptive Loop**: Introduced Q-learning & R2D2 to rewrite prompts dynamically when return < threshold.

---

#### Tech Stack

LLaMA‑2‑7B, InternLM, QLoRA, LoRA Adapter, RLHF, Soft Label Distillation, Backtrader, GraphDB, Prompt Chain System, FastAPI, Docker, PyTorch Lightning, WandB, TensorRT INT4, JSON/XML/GraphML output, RTX 3090.

---
