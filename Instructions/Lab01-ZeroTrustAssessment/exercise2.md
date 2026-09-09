---
lab:
  title: 评估 Microsoft 365 租户安全性
  description: 在本练习中，您将安装 Microsoft Zero Trust Assessment，连接 Microsoft 365 租户，并生成安全成熟度评估报告。
  duration: 20 分钟
  level: 300
  islab: true
  primarytopics:
    - Microsoft Entra ID
    - Microsoft Security
    - Zero Trust
    - Microsoft 365
---

# Exercise 2 - 评估 Microsoft 365 租户安全性

## 概述

Microsoft Zero Trust Assessment 是微软官方提供的安全评估工具。

该工具可以自动检查 Microsoft 365 租户配置，并根据 Zero Trust 最佳实践生成安全评分和改进建议。

Assessment 将评估以下安全支柱：

- Identity（身份）
- Devices（设备）
- Data（数据）
- Network（网络）
- Infrastructure（基础设施）
- Security Operations（安全运营）
- AI（人工智能）

完成本练习后，您将获得一份完整的 Zero Trust Assessment 报告。

---

# 实验目标

完成本练习后，您将能够：

✅ 安装 Zero Trust Assessment

✅ 连接 Microsoft 365 租户

✅ 运行 Assessment 评估

✅ 生成 HTML 报告

✅ 查看 Assessment 结果

✅ 为后续风险分析实验提供数据基础

---

# 实验前提条件

在开始实验之前，请确认：

- 已安装 PowerShell 7 [安装指南](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell)
- 拥有 Microsoft 365 租户
- 具备讲师预先确认的管理员账号。首次连接和管理员同意所需权限时，可能需要特权角色；请按租户的最小权限和管理员同意流程执行，不要默认使用全局管理员。
- 运行评估所需的具体目录角色和服务权限取决于 Assessment 版本，请在实验前依据该版本的官方文档确认。
- 如果您已安装旧版本的 Zero Trust Assessment，请先卸载后再继续。

---

# Exercise 2.1 安装 Zero Trust Assessment

## Step 1

以管理员身份打开：

**PowerShell 7**

---

## Step 2

执行以下命令安装评估模块：

```powershell
Install-Module ZeroTrustAssessment -Scope CurrentUser
```

等待安装完成。

> [!NOTE]
>
> 如果系统提示信任 PSGallery，请输入：
>
> ```text
> Y
> ```

继续安装。

---

# Exercise 2.2 连接 Microsoft 365 租户

## Step 1

执行：

```powershell
Connect-ZtAssessment
```

---

## Step 2

根据提示登录 Microsoft 365 租户。

首次连接时可能需要由管理员同意 Assessment 请求的访问权限。

系统可能请求访问：

- Microsoft Graph
- Microsoft Entra ID
- Exchange Online
- SharePoint Online
- Azure 相关服务

等服务。

---

## Step 3

选择：

```text
Accept
```

完成授权。

---

## 验证成功

连接成功后应看到类似提示：

```text
Connected successfully
```

如果出现登录窗口，请使用讲师指定的管理员账号完成认证；普通学员账号不用于真实租户评估。

---

# Exercise 2.3 运行 Assessment

## Step 1

执行评估命令：

```powershell
Invoke-ZtAssessment
```

---

## Step 2

等待评估完成。

Assessment 将根据当前版本和已授予的权限收集租户配置并执行安全检查。检查数量和覆盖范围可能随版本变化。

---

## Assessment 内容

本练习使用的版本可能评估以下支柱；实际结果以报告中显示的支柱为准：

- Identity
- Devices
- Data
- Network
- Infrastructure
- Security Operations
- AI

七大 Zero Trust 安全支柱。

---

## Step 3

评估完成后，系统将生成结果文件。

确认输出成功：

```text
Assessment Complete
```

---

# Exercise 2.4 查看 Assessment 报告

## Step 1

打开生成的 Assessment 报告。

通常包括：

- HTML 报告
- JSON 数据文件

---

## Step 2

在浏览器中打开 HTML 报告。

查看：

### Assessment Overview

记录以下信息：

| 项目 | 结果 |
|--------|--------|
| Tenant Name | __________ |
| Assessment Date | __________ |

---

## Step 3

查看 Summary 页面。

记录评分：

| Security Pillar | Score |
|----------------|---------|
| Identity | ______ |
| Devices | ______ |
| Data | ______ |
| Network | ______ |
| Infrastructure | ______ |
| Security Operations | ______ |
| AI | ______ |

---

# Exercise 2.5 分析评估结果

## 查看 Recommendations

在报告中定位：

```text
Recommendations
```

区域。

Assessment 将根据检测结果提供整改建议。

---

## 查看 Gaps

在报告中查找：

```text
Failed Checks
```

或：

```text
Not Implemented
```

相关内容。

这些项目代表当前 Zero Trust 缺口。

---

## 记录发现

请记录三项最需要关注的问题：

### 问题 1

_________________________________

### 问题 2

_________________________________

### 问题 3

_________________________________

---

# Exercise 2.6 查看 AI 安全成熟度

## AI Security

定位：

```text
AI
```

安全支柱。

如果报告中显示 AI 支柱或 AI Readiness 检查项，则记录其结果；不同版本、租户和许可可能显示不同的 AI 检查范围。

---

## 思考

如果组织计划部署：

- Microsoft 365 Copilot
- AI Agent
- Enterprise Search

哪些 AI 安全项应该优先完成？

记录您的答案：

_________________________________

_________________________________

_________________________________

---

# 验证成功

如果您已完成以下任务，则本练习完成：

✅ 成功安装 Zero Trust Assessment

✅ 成功连接 Microsoft 365 租户

✅ 成功运行 Assessment

✅ 成功生成 Assessment 报告

✅ 成功查看安全评分

✅ 成功识别关键改进项

---

## 完成实验

返回：

➡ [零信任评估（Zero Trust Assessment）](./01-Zero-Trust-Assessment.html)

---

# 小结

在本练习中，您使用 Microsoft Zero Trust Assessment 对 Microsoft 365 租户进行了安全评估，并获得了：

- 当前安全成熟度评分
- Zero Trust 差距分析
- 安全改进建议
- AI 安全准备情况

在下一实验中，您将进一步分析 Assessment 输出结果，并完成风险报表分析。

---

## 后续实验

完成本实验后，请继续进行：

➡ [实验 02：风险报表分析（Risk Analysis）](../Lab02-RiskAnalysis/Lab02-RiskAnalysis.html)

在下一实验中，您将基于 Assessment 结果识别高风险问题，并制定安全改进计划。