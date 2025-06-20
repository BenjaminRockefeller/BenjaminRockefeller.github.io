---
layout: page
title: project 1
description: with background image
img: assets/img/12.jpg
importance: 1
category: work
related_publications: false
---

## ✅ Project 1 | Financial Research Report Generation Platform

### RAG-Enhanced Contextual Reasoning with On-Premise Deployment (Tailored for U.S. Equity Market)

------

### 1. Project Overview

This project addresses major challenges in financial research report generation, including redundant content, hallucination-prone outputs, unstructured formatting, and low automation levels. We built a RAG-enhanced system capable of controllable generation, modular maintenance, and high-fidelity citation, with full support for on-premise deployment. The pipeline integrates financial corpus collection, multi-stage semantic retrieval, prompt injection, multi-model tuning, and optimized inference.

------

### 2. Motivation & Problem Statement

Based on interviews with over 30 private equity and research institutions, we identified the following pain points:

- High hallucination rates due to lack of authoritative sources in general-purpose LLMs.
- Expensive and uncontrollable external APIs, limiting suitability for private deployments.
- Repetitive manual writing and fragmented output structure, requiring modularized automation.

**Positioning**: End-to-end solution with 4 goals:
 RAG-enhancement · Local deployment · Module reusability · Faithful generation

------

### 3. System Architecture

**Overall Pipeline**:
 `Data Collection → BM25 → Dense Retrieval → Cross-Encoder → Prompt Injection → LLM Inference → Hallucination Filtering → On-Prem Deployment`

#### 3.1 Data Pipeline & Preprocessing

- Collected 386,000 bilingual financial documents from Yahoo Finance, CNBC, EDGAR, WallStreetCN
- Used `Unstructured` to parse financial PDFs, reconstructed tables manually
- Final structured segments: 243,000+

#### 3.2 Multi-Stage Semantic Retrieval

- Stage 1: BM25 (Recall@10 = 82.3%)
- Stage 2: Faiss-HNSW vector retrieval (384d)
- Stage 3: BERT Cross-Encoder (Top-1 ↑ from 60.2% → 80.1%)
- Prompt assembly: chunking + topic aggregation + positional embedding

#### 3.3 Prompt Engineering & LLM Optimization

- Template: `Task Description + Retrieved Evidence + User Instruction`
- Models: ChatGLM2-6B, InternLM2, Yi-6B
- Structured generation enforced via guiding objectives + anti-redundancy strategies

------

### 4. Hallucination Evaluation

#### Evaluation Setup

- Custom TruthfulQA-Finance (30 QA)
- MMLU-Finance summarization benchmark (20 samples)
- Review method: 5 human raters + GPT-4 consistency check

#### Evaluation Results

| Model Variant          | Hallucination Rate | Consistency Score | Structural Integrity |
| ---------------------- | ------------------ | ----------------- | -------------------- |
| ChatGLM2-6B (baseline) | 27.5%              | 3.6 / 5.0         | 71.4%                |
| RAG-Enhanced System    | 12.8%              | 4.7 / 5.0         | 91.3%                |

**Example Q**: *What was the Fed rate hike in March 2023?*

- **ChatGLM2-6B**: “50bp” ❌
- **Ours**: “25bp” ✅ (Cited EDGAR source)

------

### 5. Deployment & Performance

- Backend: FastAPI + Redis (async queue)
- Deployment: Docker container + RTX A100 (7.6 GB VRAM)
- Throughput: QPS = 52, latency < 300ms
- Cost: 48 GPU-hours ($65), hardware ~$8,000
- API Compatibility: Unified internal NLP APIs + Chat-compatible endpoint

------

### 6. Key Performance Metrics

| Metric                  | Value     | Description                       |
| ----------------------- | --------- | --------------------------------- |
| Recall@10 (BM25)        | 82.3%     | Initial retrieval                 |
| Top-1 Accuracy (rerank) | 80.1%     | After BERT re-ranking             |
| BLEU Score Gain         | +25.2%    | Compared to base ChatGLM2-6B      |
| Hallucination Reduction | –14.7%    | TruthfulQA subset                 |
| Consistency Score       | 4.7 / 5.0 | Human review average              |
| Inference Latency       | <300 ms   | In private deployment environment |

------

### 7. Expert Validation

- Tested by 3 U.S. equity research analysts
- Reported improvements in:
  - Terminology accuracy
  - Financial summary coherence
  - Traceability of cited evidence
- Recommended future directions:
  - Chart-to-text generation
  - Event-chain causal reasoning

------

### 8. Roadmap & Research Directions

- **Feature Expansion**: Incorporate PDF table parsing, chart understanding, and event summarization
- **Academic Output**: Preparing paper for ACL Industry or EMNLP Systems Demo titled:
   *"RAG-Augmented Systems for Hallucination Mitigation in Financial NLP"*
- **Industry Pilot**: Currently being integrated into SaaS platforms for PE firms and research institutions

------

### 9. Technology Stack

ChatGLM2-6B, InternLM2, Yi-6B, BM25, Faiss-HNSW, Chinese-BERT Cross-Encoder,
 TruthfulQA, MMLU-Finance, Prompt Injection, LoRA, QLoRA,
 FastAPI, Docker, MongoDB, Redis, PyTorch Lightning, TensorBoard,
 WandB, Pandas, Unstructured, Hugging Face Transformers, Streamlit
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/1.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/3.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Caption photos easily. On the left, a road goes through a tunnel. Middle, leaves artistically fall in a hipster photoshoot. Right, in another hipster photoshoot, a lumberjack grasps a handful of pine needles.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

You can also put regular text between your rows of images, even citations {% cite einstein1950meaning %}.
Say you wanted to write a bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, _bled_ for your project, and then... you reveal its glory in the next row of images.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>

The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}

```html
<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
```

{% endraw %}
