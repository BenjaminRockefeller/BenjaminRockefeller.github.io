---
layout: page
title: "Project 5｜High-Performance Multi-Model Inference Optimization Platform"
description: "Integrating Tensor Parallelism and INT8 Quantization for Low-Latency Deployment"
importance: 5
category: work
---

### ✅ Project 5｜High-Performance Multi-Model Inference Optimization Platform  
(Integrating Tensor Parallelism and INT8 Quantization for Low-Latency Deployment)

---

#### Project Overview  

To tackle key challenges in enterprise-level LLM inference—including high memory consumption, long response latency, and limited multi-terminal compatibility—we built a high-performance deployment platform that integrates tensor parallelism, pipeline parallelism, and low-precision quantization. This platform supports multi-modal tasks, LoRA hot-swapping, and heterogeneous device scheduling. It is optimized for deployment in finance, government, manufacturing, and other latency-sensitive production environments.

---

#### Project Contributions  

- Designed and implemented a distributed inference architecture using Huggingface Transformers + DeepSpeed, enabling **Tensor Parallel + Pipeline Parallel** execution.  
  - Optimized context window up to 128K  
  - Integrated with `vLLM` engine  
  - Achieved a **3.7× improvement** in QPS  
  - Stable for multi-turn dialogue tasks

- Built a hybrid **INT8 + FP16 quantization path**:  
  - Applied Quantization-Aware Training (QAT) on ChatGLM2-6B  
  - Deployed with `OpenVINO` for CPU inference acceleration  
  - Reduced memory usage by **~53%**  
  - Cut average response latency to **<2.8s**

- Developed a **unified inference API** using FastAPI + JSON-RPC:  
  - Supported prompt batching, auto-routing by task type, and concurrent request management  
  - Increased interface success rate from **92.6% → 99.3%**

- Built a containerized deployment system with Docker Compose:  
  - Integrated `Nginx` for load balancing, token authentication, and SSL encryption  
  - Enabled automatic switching between GPU/CPU for hybrid scheduling and secure intranet access

- Implemented **hot-pluggable model update modules**:  
  - Compatible with self-trained LoRA/QLoRA weight formats  
  - Enabled dynamic model switching without restart  
  - Average switch time: **<1.3s**

- Curated a **multi-task inference dataset (21,000 samples)**:  
  - Sourced from enterprise support logs, research prompts, and customer service tickets  
  - Applied regex-based cleaning + instruction template transformation  
  - Covered tasks: generation, summarization, classification, and NER

- Resolved GPU scheduling conflicts between vLLM and pipeline parallelism:  
  - Tuned `tensor_parallel_size` and `async_batching` configurations  
  - Stably supported 8-GPU distributed inference  
  - Increased task throughput by **~2.4×**

- Performance benchmarking showed over **30% improvement** compared to baseline across:  
  - Inference throughput  
  - API response rate  
  - Model switch efficiency  
    Platform has been successfully deployed in quantitative research, government Q&A, and internal CRM systems.

---

#### Tech Stack  

ChatGLM2‑6B, DeepSpeed, vLLM, Tensor Parallelism, Pipeline Parallelism, INT8 QAT, OpenVINO, FastAPI, JSON-RPC, LoRA / QLoRA, Docker Compose, Nginx, SSL, Token Auth, WandB
