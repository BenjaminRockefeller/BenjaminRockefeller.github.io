---
layout: page
title: "Project 2｜Intelligent Quantitative Strategy Generation Platform"
permalink: /projects/project2/
importance: 2
category: work
---

<style>
  /* --- local style overrides to make the page more readable & visually striking --- */
  h1.project-title {
    font-size: 32px;
    font-weight: 800;
    margin-bottom: 0.6em;
  }
  h2.project-subtitle {
    font-size: 24px;
    font-weight: 700;
    margin-top: 0.8em;
    margin-bottom: 0.5em;
  }
  h3 {
    font-size: 21px;
    font-weight: 600;
    margin-top: 0.9em;
    margin-bottom: 0.4em;
  }
  p, li {
    font-size: 17px;
    line-height: 1.7em;
  }
  table {
    font-size: 16px;
  }
  .highlight {
    color: #1a73e8;
    font-weight: 700;
  }
</style>

# <span class="project-title">📈 Project 2｜Intelligent Quantitative Strategy Generation Platform</span>

## <span class="project-subtitle">Causality‑Aware RLHF Optimization with Backtest Feedback Loop</span>

### 1. Project Overview

This platform solves long‑standing issues in quant strategy development—**unverifiable outputs, missing causal structure, and high deployment cost**—by integrating strategy generation, causal graph refinement, RLHF optimization, and back‑test feedback into a single closed loop.

### 2. Key Contributions

- **Rich Multi‑Source Dataset** (> 800 K items)
  - 12 K strategy abstracts, 11 K indicator chains, 9 K causal market graphs
  - Sources: private‑fund docs, causal event DBs, Tushare logs
- **Causal Graph Alignment** → structural consistency ↑ from 71.2 % to 94.6 %
  - spaCy + regex tree extraction; custom GraphDB entity merge; 5‑round human QA
- **Multi‑Task Distillation** with **LLaMA‑2‑7B teacher**
  - Soft‑label (T = 2.0), structure‑aware prompts, loss weights 0.4 / 0.4 / 0.2
- **Custom RLHF Reward (3‑Dimensional)**
  1. Causal Coverage   2. Coherence Score   3. Back‑test Return & Stability
  - Uses reward clipping + early baseline → avoids collapse
- **Back‑test Feedback Loop**
  - Autogenerates Backtrader scripts → collects Sharpe/return/drawdown
  - Feeds metrics back into PPO; enables *generate → simulate → retrain* cycle
- **Deployment Optimisation**
  - QLoRA (rank = 8) + TensorRT INT4 ⇒ model ↓ 65 %; latency 270 ms; 26 req/s on RTX 3090

### 3. Experimental Results

| Metric | Improvement |
|--------|-------------|
| BLEU | **+14.6 %** |
| Redundancy | **‑21.2 %** |
| Causal Matching Acc. | **85.4 %** |
| Strategy Simulation Success | **78.9 %** |
| Avg. Human Rating | **4.7 / 5.0** |
| Convergence Speed | **+32 %** (RLHF + back‑test reward) |

### 4. Future Roadmap

- **Ablation Studies** (no‑causal / no‑reward / generic‑RLHF)
- **Interactive Visualisation** (D3 + Plotly for causal graphs & ROI curves)
- **Cross‑Model Portability** (InternLM, Mistral‑7B, Yi‑6B, < 2.7 % error)
- **Advanced RL Fusion** (Q‑learning / R2D2 auto‑rewrite when ROI ↓)

### 5. Tech Stack

LLaMA‑2‑7B · QLoRA · Custom RLHF · Soft‑Label Distillation · Backtrader · GraphDB · spaCy · Prompt Chain · PyTorch Lightning · FastAPI · TensorRT INT4 · Docker · WandB · RTX 3090
