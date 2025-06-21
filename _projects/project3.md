---
layout: page
title: "Project 3｜Multi-Agent Financial Fraud Detection System: LangGraph + GAT + RLHF + Prompt Defense"
permalink: /projects/project3/
importance: 1
category: work
---

### 🔍 Project Overview

This system tackles key pain points in financial risk control: delayed fraud detection, high false-positive rates, broken decision pipelines, and vulnerability to prompt attacks. By integrating Graph Attention Networks (GAT), a multi-agent task scheduling mechanism (LangGraph), RLHF reward optimization, and a security-focused prompt defense module, this enterprise-grade system enables joint modeling of structured behavior data and unstructured intent signals. It has been tested in real-world loan approval and risk scoring scenarios.

---

### 🧭 Motivation & Problem Statement

Financial risk control traditionally suffers from:

- ⚠️ **Broken process flow** due to rigid rule-based systems
- ❌ **High false-positive rates** with outdated ML baselines
- 🛡️ **Susceptibility to prompt injection & adversarial attacks**

Our solution ensures robust, interpretable, and high-precision fraud detection across the full pipeline: transaction modeling → intent classification → adversarial defense → human audit traceability.

---

### 🧠 Architecture & Core Modules

#### 🧩 Multi-Agent Chain via LangGraph
- Designed 3-stage Agent chain: `Risk ID Agent → Rule Judge Agent → Manual Review Agent`
- Used `AgentNode + AgentState` for dynamic task routing & context sharing
- Unblocked fragmented workflows in traditional systems

#### 📊 GAT-Based Behavior Graph Modeling
- Built a heterogeneous graph on 42,000 transactions
- Node features: frequency, device fingerprints; Edge: amount shifts, address link strength
- F1 = 0.918 (validation), 0.911 (test), outperforming GraphSAGE & LightGBM

#### 📘 Unstructured Intent Modeling via RLHF
- Fine-tuned ChatGLM3-6B on 11,000 labeled samples across 14 intent types
- Used GPT-3.5 as Reward Model for RLHF alignment → consistency +11.3%

#### 🛡️ Prompt Injection Defense Module
- Collected 36 attack patterns (e.g., role spoofing, denial triggers)
- Integrated Detoxify & added reward fusion:  
  `R_total = 0.5 * Task Fidelity + 0.3 * Output Consistency + 0.2 * Safety Score`
- Reduced Jailbreak Success Rate: **31.2% → 9.6%**
- Toxicity Score: **0.23 → 0.07**; Bias Trigger ↓42.5%

#### 🧪 Adversarial Ablation Experiment
| Configuration | F1 ↑ | Attack Bypass ↓ | Convergence Speed ↑ |
|---------------|------|------------------|----------------------|
| No Defense + Generic RLHF | - | - | - |
| + Defense (No Reward Fusion) | +1.7% | ↓9.4% | ↑11% |
| ✅ Full Defense (with Reward Fusion) | **+3.4%** | **↓19.8%** | **↑24%** |

#### ⚖️ Hybrid-Rule Engine
- Combined GAT model output with 17 business rules
- Boosted compatibility and real-world adaptability

#### 🧾 Agent Traceability & Audit Logging
- Integrated LangSmith for step-by-step trace recording
- Enables audit compliance in banking-grade applications

---

### 🚀 Deployment & Performance
- Inference latency < 450ms
- Concurrent QPS = 50+ (single node)
- Stack: `FastAPI + Redis + Docker Compose + Prometheus`

---

### 💼 Future Business Use Cases
- ✅ Loan approvals
- ✅ Risk assessment platforms
- ✅ Expandable to insurance, e-commerce, Web3, etc.

---

### 🧰 Tech Stack
ChatGLM3‑6B, QLoRA, RLHF, GPT-3.5 Reward Model, LangGraph, LangChain, LangSmith, GAT (DGL + PyTorch), Prompt Injection Eval, Detoxify, Hybrid Rules Engine, FastAPI, Redis, Docker Compose, Prometheus, Grafana, SMOTE, Z-Score, Isolation Forest, Sklearn, Pandas, WandB, Kaggle Dataset
