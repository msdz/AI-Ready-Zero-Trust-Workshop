---
title: 实验指导手册
permalink: index.html
layout: home
---

# AI Ready 安全先行

本实验手册对应：

**AI Ready 安全先行：安全拥抱 AI**
**零信任工作坊（Hands-on Lab）**

活动时间：2026年9月23日

## 实验目标

通过真实业务场景体验：

- Zero Trust Assessment
- 风险报表分析
- MFA 防钓鱼验证
- 合规设备访问
- ZTNA 网络访问
- AI 应用权限验证

---

## 实验列表

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Lab'" %}
{% assign labs = labs | sort: "lab.title" %}
{% for activity in labs  %}
- [{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }})
{% endfor %}