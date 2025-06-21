---
layout: page
title: "Project 3 | Breaking False Positives and Process Disruptions: Multi-Agent Financial Fraud Detection System"
description: "Based on LangGraph + GAT + RLHF + Prompt Injection Defense"
importance: 3
category: work
---
#### 1. Project Overview

This project targets critical issues in financial fraud detection systems: high false positive rates, broken decision chains, delayed responses, and vulnerability to prompt attacks. We developed an enterprise-level multi-agent fraud detection system, combining LangGraph-based task routing, Graph Attention Networks (GAT), RLHF fine-tuning, and multi-layered prompt injection defense. The platform handles both structured transaction data and unstructured behavioral intent, suitable for credit approval, risk profiling, and compliance auditing.

---

#### 2. Motivation & Problem Statement

Pain points from financial institutions:

- Broken workflows in manual–rule–ML hybrid systems causing alert leakage or delays.
- Poor generalization in traditional fraud models under unseen attacker behavior.
- Vulnerability of LLM-based agents to adversarial prompt manipulation.

**Positioning**: A secure and explainable agent-based system with graph learning, RLHF safety tuning, and end-to-end observability.

---

#### 3. System Architecture

**Agent Chain Design**:  
`Transaction → Risk Identification Agent → Rule Evaluation Agent → Manual Review Agent → Final Decision`

**3.1 Multi-Agent Routing (LangGraph)**

- Implemented AgentNode + AgentState logic to maintain synchronized context.
- Dynamic rerouting based on agent feedback and intermediate risk confidence.
- Resolved task interruption and alert propagation issues.

**3.2 GAT-Based Behavior Graph**

- 42,000 real-world records modeled as heterogeneous graphs:
  - **Nodes**: transaction ID, user ID, device fingerprint  
  - **Edges**: transfer amount spikes, shared IP or MAC patterns  
- Results:
  - F1 = 0.918 (val), F1 = 0.911 (test), outperforming GraphSAGE/LightGBM

**3.3 Prompt Defense & RLHF Alignment**

- Collected 36 prompt attack types: role hijack, jailbreaks, denial-of-safety triggers
- Reward structure:
  - 50% Instruction Completion
  - 30% Output Consistency
  - 20% Detoxify-based Safety Score  
- Jailbreak rate ↓ from 31.2% → 9.6%, Toxicity ↓ from 0.23 → 0.07

---

#### 4. Evaluation & Safety Ablation

- Ablation variants tested:
  - No defense + generic RLHF
  - Defense without reward signal
  - Full defense + custom safety agent
- Full version results:
  - F1 ↑ 3.4%
  - Attack bypass ↓ 19.8%
  - Convergence speed ↑ 24%

- Expert validation by fintech compliance engineers confirmed:  
  - Safety modules met audit traceability requirements  
  - Agent routing paths observable via LangSmith  

---

#### 5. Deployment & Monitoring

- Backend: FastAPI + Redis task queue  
- Containerization: Docker Compose  
- Monitoring: Prometheus + Grafana  
- Performance:
  - Latency < 450ms  
  - QPS: 50  
  - Single-machine deployment using RTX 3090

---

#### 6. Key Metrics

| Metric                  | Value         | Description                          |
| ----------------------- | ------------- | ------------------------------------ |
| F1 (GAT val/test)       | 0.918 / 0.911 | Structured behavior graph modeling   |
| Jailbreak Rate          | ↓ 69.2%       | With prompt defense                  |
| Prompt Toxicity Score   | ↓ 0.23 → 0.07 | Evaluated via Detoxify               |
| Bias Trigger Rate       | ↓ 42.5%       | Reduction in gender/race prompt bias |
| Attack Bypass Reduction | –19.8%        | After defense system deployment      |
| Auditability            | √             | Agent logs tracked via LangSmith     |

---

#### 7. Use Cases & Extensions

- Credit risk scoring engines (banking)
- Transaction auditing (e-commerce, Web3 wallets)
- Insurance fraud detection (claim abuse)

---

#### 8. Technology Stack

ChatGLM3‑6B, QLoRA, RLHF (GPT-3.5 reward model), LangGraph, GAT (DGL),  
Prompt Injection Defense, Detoxify, FastAPI, Redis, Docker Compose,  
LangSmith, SMOTE, Z-Score, Isolation Forest, Prometheus, Grafana,  
Scikit-learn, PyTorch, Pandas, WandB

---
