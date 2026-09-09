---
lab:
  title: 零信任评估（Zero Trust Assessment）
  description: 在本实验中，您将了解 Microsoft Zero Trust Assessment 的核心功能，查看企业安全成熟度评估结果，并识别 Zero Trust 建设过程中的关键改进方向。
  duration: 15 分钟
  level: 200
  islab: true
  primarytopics:
    - Microsoft Security
    - Microsoft Entra
    - Zero Trust
    - AI Security
---

# 零信任评估（Zero Trust Assessment）

## 实验简介

随着 AI 应用逐步融入企业运营和业务创新，企业在提升生产力的同时，也面临新的安全与治理挑战。

在 AI 时代，企业需要确保：

- 身份可信
- 设备可信
- 网络可信
- 数据受保护
- AI 访问受到治理

微软 Zero Trust（零信任）安全模型通过“永不信任，持续验证（Never Trust, Always Verify）”的理念，帮助组织构建覆盖身份、设备、应用、网络与数据的统一安全体系。

Microsoft Zero Trust Assessment 是微软官方提供的安全评估工具，用于帮助组织快速了解当前安全成熟度，并发现与 Zero Trust 最佳实践之间的差距。

---

## 实验场景

Contoso 公司正在推进企业级 AI 战略。

企业计划陆续部署：

- Microsoft 365 Copilot
- 企业知识助手
- AI Agent
- 智能搜索平台

在正式推广 AI 之前，安全团队希望回答以下问题：

- 当前身份保护是否足够？
- 设备是否符合安全要求？
- 条件访问是否覆盖关键场景？
- 企业是否具备 AI 安全基础能力？
- 哪些领域需要优先整改？

为此，安全团队决定使用 Microsoft Zero Trust Assessment 对租户进行全面评估。

---

## 学习目标

完成本实验后，您将能够：

✅ 理解 Zero Trust Assessment 的用途

✅ 了解企业当前安全成熟度

✅ 查看各安全支柱（Pillar）评分

✅ 识别关键风险领域

✅ 理解 Zero Trust 与 AI Ready 的关系

✅ 为后续风险分析实验做好准备

---

## Assessment 覆盖范围

当前版本的 Microsoft Zero Trust Assessment 支持以下安全领域评估：

| 安全支柱 | 说明 |
| ---------- | ---------- |
| Identity | 身份与访问控制 |
| Devices | 设备管理与合规 |
| Data | 数据保护 |
| Network | 网络安全 |
| Infrastructure | 基础设施安全 |
| Security Operations | 安全运营 |
| Artificial Intelligence | AI 安全治理 |

---

## 实验方式

本实验提供两种体验方式。

### 方式一：查看官方 Demo 报告（推荐）

适用于：

- Workshop 活动
- 培训实验
- 快速体验

学员将使用 Microsoft 官方演示报告进行分析, 最新版本参考：[Microsoft Zero Trust Assessment](https://aka.ms/ZeroTrust/Demo)。

[练习1：官方 Demo 报告](./exercise1.html)

---

### 方式二：评估真实租户（讲师演示）

适用于：

- 企业 PoC
- 生产环境评估
- 安全基线检查

讲师将演示如何连接 Microsoft 365 租户并运行 Assessment。 

[练习2：评估真实租户](./exercise2.html)


## 实验成果

完成本实验后，您将获得：

- 企业安全成熟度基线
- 风险识别结果
- 优先整改建议
- Zero Trust 建设路线图输入

这些结果将在下一章节《风险报表分析》中继续使用。
---

## 完成实验

返回：

➡ [手册首页](../../index.html)

---

## 后续实验

完成本实验后，请继续进行：

➡ [实验 02：风险报表分析（Risk Analysis）](../Lab02-RiskAnalysis/Lab02-RiskAnalysis.html)

在下一实验中，您将基于 Assessment 结果识别高风险问题，并制定安全改进计划。
