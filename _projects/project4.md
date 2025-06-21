---
layout: page
title: "Project 4｜Enterprise-Grade LLM Fine-Tuning and Deployment Optimization Platform"
description: "Focused on Sentiment Classification and Named Entity Recognition Tasks"
importance: 4
category: work
---

### ✅ Project 4｜Enterprise-Grade LLM Fine-Tuning and Deployment Optimization Platform  
(Focused on Sentiment Classification and Named Entity Recognition Tasks)

---

#### Project Overview  

To address key challenges in enterprise-level large language model deployment—namely high fine-tuning cost, low inference efficiency, and poor cross-task generalization—we built a lightweight fine-tuning platform tailored for sentiment analysis and named entity recognition (NER). The system integrates QLoRA-based parameter-efficient tuning with RLHF-based instruction alignment, supports multi-task adaptation, enables stable training, and delivers fast, high-throughput inference in private environments. The solution is applicable to government, finance, and e-commerce sectors.

---

#### Project Contributions  

- Led the design and implementation of a QLoRA-based lightweight fine-tuning pipeline.  
  - Backbone: ChatGLM2-6B  
  - Fine-tuning: LoRA Adapter only (rank=8)  
  - Result: GPU memory usage reduced from 24 GB to 7.2 GB; training cost decreased by ~60%, significantly lowering the deployment barrier for enterprises.

- Constructed a unified multi-task dataset:  
  - 5,000 manually curated sentiment classification samples (positive/negative)  
  - ~120,000 characters of annotated NER data (People’s Daily corpus)  
  - Unified prompt template and label alignment mechanism ensured cross-task consistency and transferability.

- Designed a two-stage RLHF reward strategy:  
  - Stage 1: GPT-3.5 used to score instruction execution quality  
  - Stage 2: Weighted PPO optimization with metrics:  
    - Sentiment F1  
    - NER Recall  
    - Instruction score  
  - Dynamic reward ratio: 0.5 : 0.3 : 0.2  
  - Solved early-stage instability and improved generation consistency by ~12%.

- Built a complete RLHF training loop with Huggingface TRL (PPO)  
  - Tuned reward clipping and dynamic baseline strategies  
  - Mitigated gradient explosion and stabilized training

- Remotely conducted cost-efficient training using Magicoder (¥7–15/h) and Paperspace ($1.25/h) A100 GPU instances  
  - Total training time > 40 hours  
  - Cost controlled within $50–60—significantly lower than traditional full-parameter tuning

- Implemented a distributed, fault-tolerant training framework using PyTorch Lightning + DistributedDataParallel  
  - Supported resume-from-checkpoint, error recovery, and real-time monitoring for long-duration jobs

- Integrated vLLM inference engine with TensorRT INT4 quantization  
  - Achieved <350ms average inference latency  
  - Sustained 50 req/s throughput on private servers  
  - Suitable for mid-sized enterprise on-premise applications

- Conducted benchmark experiments comparing performance improvements:  
  - QLoRA + RLHF vs. full-parameter baseline  
  - Sentiment F1: 88.1% → 92.3%  
  - NER Recall: 83.5% → 90.2%  
  - Achieved superior performance and deployment efficiency

- Completed full private deployment pipeline  
  - Exported LoRA weights and conformed to OpenAI Chat API interface  
  - Successfully tested and integrated in government, financial, and e-commerce customer service scenarios  
  - Verified transferability and generalization

---

#### Tech Stack  

ChatGLM2‑6B, QLoRA, LoRA Adapter, PyTorch Lightning, DistributedDataParallel, Unified Prompting, Huggingface TRL, PPO, GPT-3.5 Reward Model, vLLM, TensorRT INT4, FastAPI, Docker, WandB, Magicoder.ai, Paperspace
