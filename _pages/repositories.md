---
layout: page
permalink: /repositories/
title: 项目仓库展示
description: 展示本人在 GitHub 上的核心 AI 项目与公开代码，涵盖 RAG 系统、LoRA 微调、智能体编排等方向。
nav: true
nav_order: 4
---

# 🚀 GitHub 项目仓库展示

欢迎访问我的 GitHub 项目集！本页展示我在人工智能领域中的公开项目，涵盖以下方向：

- 🔧 大语言模型（LLM）微调与部署优化
- 📚 知识增强生成系统（RAG）
- 🤖 多智能体协同与任务执行
- ⚙️ 私有化推理优化与多框架集成

目前项目持续建设中，所有代码开源发布，欢迎关注、交流或合作。

---

{% if site.data.repositories.github_users %}
## 👤 用户仓库总览

展示以下 GitHub 用户下的所有公开项目：

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for user in site.data.repositories.github_users %}
    {% include repository/repo_user.liquid username=user %}
  {% endfor %}
</div>
{% endif %}

---

{% if site.repo_trophies.enabled %}
{% for user in site.data.repositories.github_users %}
{% if site.data.repositories.github_users.size > 1 %}
  <h4>{{ user }}</h4>
{% endif %}
  <div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
    {% include repository/repo_trophies.liquid username=user %}
  </div>
{% endfor %}
{% endif %}

---

{% if site.data.repositories.github_repos %}
## 📦 精选项目展示

以下是我当前重点维护与展示的核心项目：

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for repo in site.data.repositories.github_repos %}
    {% include repository/repo.liquid repository=repo %}
  {% endfor %}
</div>
{% endif %}
