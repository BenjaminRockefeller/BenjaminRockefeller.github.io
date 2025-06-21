---
layout: page
title: "Project 6｜Multimodal Content Generation and Publishing Platform"
description: "Causality-Aware and Controllable Generation System for Short Video Scripts, Image+Text Content, and Voice-Based Editing"
importance: 6
category: work
---

### ✅ Project 6｜Multimodal Content Generation and Publishing Platform  
(Causality-Aware and Controllable Generation System for Short Video Scripts, Image+Text Content, and Voice-Based Editing)

---

#### Project Overview  

This project introduces **ChatPPT**, a multimodal content automation platform designed to streamline the creative workflow for short video producers, MCN agencies, and e-commerce marketing teams. The platform enables end-to-end automation—from script writing to image-text pairing and voice-controlled publishing—optimized for platforms such as TikTok, Xiaohongshu, and Instagram. It supports natural language input, automated image-text generation, and voice-based real-time control, significantly enhancing both productivity and creative expression.

---

#### Project Contributions  

- Led the design and implementation of a full-stack multimodal content chain:  
  `Text Input → Image+Text Generation → Voice Control → Web Preview`,  
  enabling 0-to-1 structured content creation in a closed loop.

- Built a multimodal dataset to support the full generation pipeline:  
  - **Text**: ~20,000 short video scripts across marketing, lifestyle, and educational themes, generated via GPT + template collection.  
  - **Image**: 25,000 open-source images fetched via Pexels/Pixabay APIs; 15,000 text-image pairs selected using hybrid manual + BERTScore filtering.  
  - **Voice**: 8,000+ real user voice commands for operations such as "add page", "replace image", "regenerate content".

- Developed a text generation module powered by ChatGLM2.5, with three-stage prompt design:  
  `Script Theme → Plot Outline → Sectioned Output`.  
  Included stylistic and character-based control mechanisms.

- Built an image matching engine combining CLIP and BM25 retrieval.  
  Achieved **Top-1 accuracy of 89.3%**, ensuring semantic-visual alignment between text and visuals.

- Implemented a voice control module using Whisper for transcription and a 12-intent classification model for command execution.  
  Achieved **93.5% accuracy** in voice-to-action mapping.

- Deployed backend infrastructure using FastAPI + Redis (async task queue)  
  and Streamlit for the front-end interactive editing and preview interface.  
  Supported remote access and real-time content updates.

- Achieved generation time of **<90 seconds per full 5-page content unit**,  
  compared to **~3 hours per unit via manual workflows**, greatly reducing cost and turnaround time.

- Cost-optimized by deploying the prototype on Hugging Face Spaces (free tier).  
  Backend runs on a single A10 GPU with **marginal cost per content < $0.005**.

---

#### Future Roadmap (v2.0 Plan)  

- Introduce **causal graph modeling** for user behavior:  
  `Click Path → Conversion Outcome`, enabling real-time impact evaluation of generated content.  
- Support **cross-lingual style transfer**, adapting for Chinese, English, Japanese, Korean, and region-specific cultural nuances.  
- Integrate **content agent framework** for automatic content generation based on user profile + A/B testing loop.  
- Launch **Chrome extension and WeChat Mini Program** to complete cross-platform deployment.

---

#### Tech Stack  

ChatGLM2.5, CLIP, Whisper, BM25, BERTScore, FastAPI, Redis, Streamlit, LangChain, PPTX Generator, Pexels API, MongoDB, Docker, Hugging Face Spaces
