---
lab:
  title: 实验 05 - ZTNA 网络访问验证
  description: 在本实验中，您将体验 Microsoft Global Secure Access 提供的 Zero Trust Network Access（ZTNA）能力，并验证用户、设备与网络访问控制如何共同保护企业资源。
  duration: 25 分钟
  level: 200
  islab: true
  primarytopics:
    - Microsoft Entra ID
    - Global Secure Access
    - Zero Trust Network Access
    - Conditional Access
    - Network Security
---

# 实验 05 - ZTNA 网络访问验证

## 概述

在前面的实验中，您已经验证：

✅ 用户身份可信（MFA）

✅ 设备可信（Compliant Device）

但是传统网络访问可能存在一个问题：

```text
VPN 连接成功可能获得较宽的网络级访问范围；实际风险取决于网络分段、路由、防火墙和访问策略。
```

攻击者一旦获取 VPN 访问权限，且网络缺少细粒度隔离，

往往可以横向移动（Lateral Movement），访问更多内部系统。

Zero Trust Network Access（ZTNA）采用：

```text
每次访问都验证
```

的原则。

只有同时满足：

- 用户可信
- 设备可信
- 网络策略允许

访问请求才会被放行。

---

## 实验目标

完成本实验后，您将能够：

✅ 理解传统 VPN 与 ZTNA 的区别

✅ 理解 Global Secure Access 架构

✅ 验证内部应用访问控制

✅ 查看 ZTNA 审计日志

✅ 理解 Zero Trust Network 原则

---

# 实验场景

Contoso 公司拥有多个内部业务系统：

- ERP 系统
- CRM 系统
- HR 系统

这些系统部署在企业内部网络中。

企业希望：

```text
不向公网直接暴露应用，并按用户、设备和应用授权访问
```

因此采用：**Microsoft Global Secure Access（GSA）** 构建 Zero Trust 网络访问架构。学员设备仍需按讲师要求安装并登录 Global Secure Access 客户端，具体客户端和许可要求以现场环境为准。

---

# 讲师环境说明

> [!IMPORTANT]
>
> 以下内容由讲师提前准备。
>
> 学员无需执行。

---

## 服务器环境

实验环境包含：

| 资源 | 说明 |
|--------|--------|
| Server01 | ERP Portal |
| Server02 | CRM Portal |
| Server03 | HR Portal |

服务器仅开放内网访问。

公网无法直接连接。

---

## Entra Private Access Connector

服务器网段部署：

```text
Microsoft Entra Private Access Connector
```

负责建立：

```text
内部网络 ↔ Global Secure Access
```

安全通道。

---

## 身份认证

访问控制基于：

```text
Microsoft Entra ID
```

验证：

- 用户身份
- MFA状态
- 设备状态

---

## 条件访问策略

访问内部应用时要求：

```text
Require MFA  
AND 
Require Compliant Device
```

---

## 网络架构

```text
User
 ↓
Entra ID
 ↓
MFA
 ↓
Compliance Check
 ↓
Global Secure Access
 ↓
Private Access Connector
 ↓
Internal Application
```

---

# 登录实验设备

## Step 1

使用实验账号：

```text
以实际实验账户为准。
```

登录实验设备。

---

## Step 2

完成 MFA 验证。

确保登录成功。

---

# 访问企业应用

## Step 1

打开浏览器。

访问：

```text
ERP Portal
```

实验地址由讲师在实验开始时提供，请记录：

```text
ERP Portal URL：____________________________
```

---

## Step 2

观察系统行为。

记录结果：

□ 成功访问

□ 被拒绝访问

---

## Step 3

打开：

```text
CRM Portal
```

实验地址由讲师在实验开始时提供，请记录：

```text
CRM Portal URL：____________________________
```

---

## Step 4

验证页面是否能够正常打开。

记录：

□ 成功

□ 失败

---

# 验证 HR Portal（如本次环境已部署）

打开讲师提供的 HR Portal 地址，记录成功或失败结果。若本次 Workshop 未部署 HR Portal，讲师应在开始前明确说明，本步骤跳过。

---

# 验证访问控制

## Step 1

讲师演示：

使用未授权设备访问同一资源。

观察结果。

---

## Step 2

记录现象：

| 场景 | 结果 |
|--------|--------|
| 合规设备 | ______ |
| 非合规设备 | ______ |

---

## 分析

为什么同一个账号：

```text
以实际实验账户为准。
```

在不同设备上得到不同结果？

____________________________________

____________________________________

---

# 查看访问日志

## Step 1

讲师打开：

```text
Global Secure Access
```

控制台。

---

## Step 2

查看：

```text
Traffic Logs
```

或：

```text
Activity Logs
```

---

## Step 3

观察以下信息：

| 项目 | 内容 |
|--------|--------|
| User | ______ |
| Application | ______ |
| Device | ______ |
| Access Result | ______ |

---

## 思考

为什么 Zero Trust 需要记录每一次访问？

__________________________________

__________________________________

---

# VPN 与 ZTNA 对比

## 传统 VPN

```text
连接网络
↓
获得内网访问权限
↓
持续信任
```

---

## ZTNA

```text
验证身份
↓
验证MFA
↓
验证设备
↓
验证应用权限
↓
允许访问
```

---

## 比较

请填写：

| 项目 | VPN | ZTNA |
|--------|--------|--------|
| 身份验证 | ______ | ______ |
| 设备验证 | ______ | ______ |
| 应用级控制 | ______ | ______ |
| 持续验证 | ______ | ______ |

---

# Zero Trust 网络原则

本实验实际验证：

```text
可信身份
+
可信设备
+
授权应用
=
允许访问
```

不是：

```text
连接网络
=
获得信任
```

---

# 验证成功

如果您已完成以下任务，则本实验完成：

✅ 成功访问 ERP Portal

✅ 成功访问 CRM Portal

✅ 观察条件访问效果

✅ 查看访问日志

✅ 理解 VPN 与 ZTNA 差异

✅ 理解 Global Secure Access 架构

---

# 实验总结

在本实验中，您体验了：

```text
Zero Trust Network Access（ZTNA）
```

访问过程。

访问企业资源时，

系统持续验证：

- 用户身份
- MFA状态
- 设备状态
- 应用权限

从而实现：

```text
Never Trust
Always Verify
```

在网络访问层面的落地。

---

# 下一实验

➡ [实验 06 - AI Apps 文件访问验证](../Lab06-AI-Apps-File-Access-Validation/Lab06-AI-Apps-File-Access-Validation.html)

在下一实验中，您将验证：

```text
AI 是否会绕过权限控制？
```

理解 AI Security 与 Zero Trust 的关系。