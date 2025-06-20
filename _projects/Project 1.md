---
layout: page
title: "Project 1｜Financial Research Report Generation Platform"
permalink: /projects/financial-rag/
importance: 1
category: work
---

## ✅ Project 1 | Financial Research Report Generation Platform

### RAG-Enhanced Contextual Reasoning with On-Premise Deployment (Tailored for U.S. Equity Market)

---

### 1. Project Overview

This project addresses major challenges in financial research report generation, including redundant content, hallucination-prone outputs, unstructured formatting, and low automation levels. We built a RAG-enhanced system capable of controllable generation, modular maintenance, and high-fidelity citation, with full support for on-premise deployment. The pipeline integrates financial corpus collection, multi-stage semantic retrieval, prompt injection, multi-model tuning, and optimized inference.

---

### 2. Motivation & Problem Statement

Based on interviews with over 30 private equity and research institutions, we identified the following pain points:

- High hallucination rates due to lack of authoritative sources in general-purpose LLMs.
- Expensive and uncontrollable external APIs, limiting suitability for private deployments.
- Repetitive manual writing and fragmented output structure, requiring modularized automation.

**Positioning**: End-to-end solution with 4 goals:  
RAG-enhancement · Local deployment · Module reusability · Faithful generation

---

### 3. System Architecture

**Pipeline**:  
Data Collection → BM25 → Dense Retrieval → Cross-Encoder → Prompt Injection → LLM Inference → Hallucination Filtering → On-Prem Deployment

- Collected 386,000 bilingual financial documents.
- BM25 recall@10: 82.3%, reranked Top-1: 80.1% via BERT Cross-Encoder.
- Models: ChatGLM2-6B, InternLM2, Yi-6B.

---

### 4. Evaluation Results

| Model                | Hallucination Rate | Consistency Score | Structural Integrity |
|---------------------|--------------------|-------------------|----------------------|
| ChatGLM2-6B         | 27.5%              | 3.6 / 5.0         | 71.4%                |
| RAG-Enhanced System | 12.8%              | 4.7 / 5.0         | 91.3%                |

---

### 5. Deployment & Performance

- Latency < 300ms, QPS = 52
- 48 GPU-hours, ~$65 cost
- Hardware: RTX A100

---

### 6. Expert Validation

- Reviewed by U.S. equity analysts
- Reported improvements in:
  - Terminology accuracy
  - Summary coherence
  - Citation traceability

---

### 7. Roadmap

- Chart-to-text generation
- Event-chain reasoning
- Preparing paper for ACL Industry or EMNLP Systems Demo

---

### 8. Tech Stack

ChatGLM2-6B, InternLM2, Yi-6B, BM25, Faiss-HNSW, Chinese-BERT Cross-Encoder,  
TruthfulQA, MMLU-Finance, Prompt Injection, LoRA, QLoRA, FastAPI, Docker, Redis, PyTorch Lightning, WandB
