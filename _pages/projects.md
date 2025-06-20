---
layout: page
title: Projects
permalink: /projects/
description: >
  A showcase of applied AI systems: Large Language Models in Content Generation, Finance, and Education.
nav: true
nav_order: 2
display_categories: [work]
horizontal: false
---

## Projects

A curated selection of applied AI systems developed by Benjamin L. Rockefeller (Lai Jianming), focused on LLM alignment, financial reasoning, intelligent agent orchestration, and private deployment.

---

### 🧠 Featured Projects

#### 🚀 Financial Research Report Generation Platform  
*A Context-Aware RAG System with Private Deployment for U.S. Stock Analysis*  
> Integrates multi-stage retrieval, prompt injection, and hallucination suppression to generate structured, source-grounded equity research content.

---

#### 🤖 Intelligent Quantitative Strategy Generation Platform  
*Causal Modeling + RLHF for Explainable Backtesting Optimization*  
> Supports end-to-end strategy generation, multi-task knowledge distillation, and reinforcement learning-based feedback training in quantitative finance.

---

#### 🛡️ AI-Driven Financial Fraud Detection System  
*Multi-Agent Framework for High-Explainability Risk Control*  
> Solves false positives and process disconnects using LangGraph-based agents, GAT modeling, RLHF reward tuning, and prompt-layer defenses.

---

#### 🧩 Enterprise-Grade LLM Deployment Optimization Platform  
*Multi-Task Fine-Tuning with QLoRA and Efficient Inference for Private Use*  
> Implements LoRA-based parameter-efficient fine-tuning on sentiment classification and NER tasks, achieving fast, scalable, and low-cost private deployment.

---

#### ⚙️ High-Performance Multi-Model Inference Optimization Platform  
*Low-Latency Serving with Tensor Parallelism and INT8 Quantization*  
> Accelerates multi-model deployment using parallel computation frameworks and quantized models, enabling inference under real-time and resource-limited constraints.

---

#### 🧬 Multimodal Content Generation and Publishing Platform  
*Causality-Aware and Controllable AI for Short Video, Copywriting, and Voice-Guided Content*  
> Supports multimodal script generation, visual-text synthesis, and dynamic voice-driven prompt control with content layout automation.

---

<!-- Project Cards Section -->

<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}
{% else %}
  {% assign sorted_projects = site.projects | sort: "importance" %}
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
