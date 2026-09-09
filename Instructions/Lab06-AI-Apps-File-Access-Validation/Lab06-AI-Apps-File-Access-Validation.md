---
lab:
  title: 实验 06 - AI 应用文件访问验证
  description: 在本实验中，您将验证 Microsoft 365 Copilot 如何遵循现有权限模型和数据保护策略，理解 AI 数据访问边界与企业治理机制。
  duration: 25 分钟
  level: 200
  islab: true
  primarytopics:
    - Microsoft 365 Copilot
    - Microsoft Purview
    - Data Governance
    - Information Protection
    - SharePoint Online
    - Zero Trust
---

# 实验 06 - AI 应用文件访问验证

## 概述

在前面的实验中，您已经验证：

✅ 用户身份可信

✅ 设备可信

✅ 网络访问可信

当企业部署 Microsoft 365 Copilot 后，

客户最关心的问题通常是：

- Copilot 会不会看到不该看的文件？

- Copilot 是否会绕过权限控制？

- Copilot 是否会忽略数据保护策略？

微软 Copilot 基于现有 Microsoft 365 安全模型运行。

Copilot 不应自动扩大用户权限，也不应绕过现有的数据保护控制。实验结果还会受到许可证、内容索引、权限同步和租户策略影响。

---

## 学习目标

完成本实验后，您将能够：

✅ 理解 Copilot 数据访问模型

✅ 理解 Copilot 与 SharePoint 权限的关系

✅ 验证 Copilot 不会突破现有权限

✅ 理解敏感度标签与加密的作用

✅ 理解 DLP 与权限模型的区别

✅ 理解 AI Ready 场景下的数据治理体系

---

## AI Ready 数据访问模型

在 Microsoft 365 中：

```text
用户
        ↓
MFA
        ↓
设备验证
        ↓
SharePoint权限
        ↓
信息保护
        ↓
Copilot
```

Copilot 能够使用的数据范围取决于：

```text
用户本身能够访问的数据
```

而不是：

```text
Copilot 自己拥有额外权限
```

Microsoft 365 Copilot 继承 Microsoft 365 的安全边界和权限体系，但实验结果仍取决于许可证、内容索引、权限同步和租户策略。

---

## 实验场景

Contoso 为 Copilot 准备了三份测试文件。

| 文件 | 权限 |
|--------|--------|
| 01_Public_Launch_Overview.docx | 全体用户 |
| 02_Executive_Strategy_2027.docx | User01、User02 |
| 03_Confidential_Budget.xlsx | User01、User02 + 敏感度标签 |

---

## 实验 1：验证 Copilot 可以访问用户有权限的数据

### Step 1

使用讲师分配的实验账号登录 Microsoft 365。

打开：

```text
Microsoft 365 Copilot Chat
```

---

### Step 2

打开文件：

```text
01_Public_Launch_Overview.docx
```

确认能够正常访问。

---

### Step 3

返回 Copilot Chat。

输入：

```text
请总结文件
“01_Public_Launch_Overview.docx”。

请列出：

1. 三个关键发布目标
2. 发布日期
3. 项目代号

并说明信息来源。
```

---

### Step 4

观察结果。

记录：

| 验证项 | 结果 |
|----------|----------|
| 可以打开文件 | □ 是 □ 否 |
| Copilot找到文件 | □ 是 □ 否 |
| Copilot生成总结 | □ 是 □ 否 |
| 返回文件关键内容 | □ 是 □ 否 |

---

### 思考

为什么 Copilot 能够总结该文件？

_________________________________

_________________________________

---

## 实验 2：验证 Copilot 不突破权限

### 场景 A：授权用户

#### Step 1

使用：

```text
User01
```

登录。

---

#### Step 2

打开：

```text
02_Executive_Strategy_2027.docx
```

确认能够访问。

---

#### Step 3

在 Copilot 中输入：

```text
请总结文件

02_Executive_Strategy_2027.docx

列出：

1. 战略目标
2. 项目代号
3. 核心计划
```

---

#### Step 4

记录结果：

□ Copilot 成功引用文件

□ Copilot 返回文件内容

---

## 场景 B：未授权用户

#### Step 1

使用：

```text
User03
```

登录。

---

#### Step 2

尝试打开：

```text
02_Executive_Strategy_2027.docx
```

---

#### Step 3

记录结果：

□ 无法访问

□ 要求申请权限

□ 文件不存在

---

#### Step 4

打开 Copilot Chat。

输入与前面相同提示：

```text
请总结文件

02_Executive_Strategy_2027.docx

列出：

1. 战略目标
2. 项目代号
3. 核心计划
```

---

#### Step 5

观察结果。

记录：

□ Copilot 无法引用文件

□ Copilot 未返回文件内容

□ Copilot 未返回文件中的唯一信息

---

### 对比分析

| 验证项 | User01 | User03 |
|----------|----------|----------|
| 打开文件 | ______ | ______ |
| Copilot找到文件 | ______ | ______ |
| Copilot总结文件 | ______ | ______ |

---

### 结论

完成以下内容：

```text
Copilot 并不会自动扩大用户权限。

Copilot 能访问的数据范围由：

________________________

决定。
```

---

## 实验 3：验证数据保护持续生效

### 背景

文件：

```text
03_Confidential_Budget.xlsx
```

已经应用：

```text
高度机密
+
加密保护
```

---

### Step 1

观察讲师演示。

讲师使用：

```text
User01
```

打开文件。

确认文件能够正常访问。

---

### Step 2

讲师下载文件到本地设备。

---

### Step 3

讲师使用未授权身份或未授权应用尝试打开文件。

观察结果。

记录：

□ 无法读取内容

□ 要求授权账号

□ 无法解密文件

---

### Step 4

回答以下问题。

#### 问题 1

在文件已成功应用加密敏感度标签的前提下，文件下载后保护是否仍然存在？

□ 是

□ 否

---

#### 问题 2

控制文件能否被打开的关键机制是什么？

□ 文件扩展名

□ 敏感度标签与加密授权

□ 文件所在目录

□ 文件名称

---

#### 问题 3

如果文件离开 SharePoint，

是否仍受保护？

□ 是

□ 否

---

### 思考

为什么企业需要：

```text
数据跟着权限走

而不是

权限跟着存储位置走
```

_________________________________

_________________________________

---

## AI Ready 数据治理模型

### 第一层

#### SharePoint / OneDrive 权限

决定：

```text
用户是否可以访问文件
```

---

### 第二层

#### 敏感度标签 + 加密

决定：

```text
谁可以打开文件
```

即使文件离开 Microsoft 365，

如果标签加密已成功写入文件，并且使用的应用支持该保护，即使文件离开 Microsoft 365，保护仍可能存在。

---

### 第三层

#### Microsoft Purview DLP

决定：

```text
Copilot 是否允许处理某些内容
```

例如：

- 敏感数据
- 财务数据
- 身份证号码
- 信用卡号码

DLP 属于治理控制层。

并不负责决定用户是否拥有文件权限。

---

## 知识检查

### 问题 1

Copilot 是否拥有独立于用户的文件访问权限？

□ 是

□ 否

---

### 问题 2

Copilot 是否能够读取用户无权访问的 SharePoint 文件？

□ 是

□ 否

---

### 问题 3

敏感度标签最主要用于：

□ 给文件改名

□ 控制谁可以访问和使用内容

□ 控制浏览器缓存

□ 控制网络连接

---

### 问题 4

DLP 最主要用于：

□ 授予用户权限

□ 创建 SharePoint 网站

□ 控制敏感数据的使用和流转

□ 创建 Microsoft 365 用户

---

### 参考答案

1. 否

2. 否

3. 控制谁可以访问和使用内容

4. 控制敏感数据的使用和流转

---

## 实验总结

在本实验中，您验证了：

```text
Copilot 能访问什么数据
=
用户能访问什么数据
```

---

```text
权限控制
决定 Copilot 能否看到文件
```

---

```text
敏感度标签 + 加密
决定谁能够打开文件
```

---

```text
DLP
决定 Copilot 是否允许处理敏感内容
```

---

因此：

```text
Microsoft 365 Copilot
不是新的数据入口

而是建立在 Microsoft 365
权限和治理体系之上的 AI 能力
```

这也是企业实现：

```text
安全拥抱AI
```

的核心基础。

---

## 完成工作坊

恭喜完成：

✅ Zero Trust Assessment

✅ 风险分析

✅ MFA 身份验证

✅ 合规设备访问

✅ ZTNA 网络访问

✅ AI 数据访问验证

您已经完整体验了：

```text
Identity
↓
Device
↓
Network
↓
Data
↓
AI
```

组成的 AI Ready 安全框架。