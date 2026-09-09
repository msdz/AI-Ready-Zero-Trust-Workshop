---
lab:
  title: 实验 04 - 合规设备访问验证
  description: 在本实验中，您将验证 Microsoft Entra 条件访问策略，并体验合规设备与非合规设备访问企业资源时的差异。
  duration: 25 分钟
  level: 200
  islab: true
  primarytopics:
    - Microsoft Entra ID
    - Conditional Access
    - Device Compliance
    - Microsoft Intune
    - Zero Trust
---

# 实验 04 - 合规设备访问验证

## 概述

在实验 03 中，您已经验证：

```text
密码 ≠ 身份
```

即使密码已经泄露，

MFA 仍然可以保护企业账号。

然而，攻击者也可能使用：

- 受感染设备
- 未托管设备
- 个人设备

访问企业资源。

因此，Zero Trust 不仅验证用户身份，

还需要验证：

```text
设备是否可信
```

Microsoft Entra 条件访问（Conditional Access）结合 Microsoft Intune 合规性管理，可以确保：

```text
正确用户 + 可信设备 = 允许访问
```

在本实验中，您将体验同一个账号在不同设备上的访问结果。

---

## 实验目标

完成本实验后，您将能够：

✅ 理解 Conditional Access 工作原理

✅ 理解设备合规性（Device Compliance）

✅ 验证非托管设备访问限制

✅ 验证合规设备访问成功

✅ 理解用户身份与设备状态联合决策机制

✅ 理解 Zero Trust 设备信任模型

---

## 实验场景

Contoso 公司已部署：

- Microsoft Entra ID
- Microsoft Intune
- Conditional Access

企业规定：

```text
仅允许合规设备访问项目文档
```

即：

- 已注册设备
- Intune 托管设备
- 满足安全策略设备

才允许访问企业资源。

---

## 查看条件访问策略

### Step 1

讲师展示 Conditional Access 策略。

本实验至少需要两类控制：一条要求 MFA 的策略，以及一条针对 SharePoint Online 要求合规设备的策略。若租户将两项要求合并在同一策略中，请以讲师展示的实际配置为准。

示例规则如下：

```text
Users:
All Employees

Application:
SharePoint Online

Grant Access:
Require Compliant Device
```

---

### Step 2

记录策略要求：

□ 要求登录用户

□ 要求 MFA

□ 要求合规设备

---

### 思考

为什么企业需要同时验证：

```text
用户 + 设备
```

而不是仅验证账号密码？

记录答案：

________________________________________________

________________________________________________

---

## 使用个人电脑访问资源

### Step 1

使用实验账号登录：

```text
以实际实验账户为准。
```

完成 MFA 验证。

---

### Step 2

打开讲师在实验开始时提供的 SharePoint 地址，并将地址记录在下方：

```text
SharePoint Site URL：____________________________
```

---

### Step 3

尝试打开以下文件：

```text
Launch Readiness Plan.docx
```

或：

```text
Project Phoenix Overview.docx
```

---

### Step 4

观察系统返回结果。

记录：

□ 允许访问

□ 拒绝访问

□ 提示设备不符合要求

---

### 观察

记录系统返回信息：

________________________________________________

________________________________________________

---

## 使用合规设备访问资源

### Step 1

与同组学员前往演示设备区域。

本实验使用：

```text
受支持的 Windows 版本 + Microsoft Intune + Compliant Device
```

实验设备。

---

### Step 2

登录相同账号：

```text
以实际实验账户为准。
```

完成 MFA。

---

### Step 3

访问同一 SharePoint 地址。

打开：

```text
Launch Readiness Plan.docx
```

---

### Step 4

观察访问结果。

记录：

□ 成功访问

□ 无法访问

---

### Step 5

查看文件内容。

确认能够：

- 浏览文档
- 下载文件
- 编辑内容（如已授权）

---

## 对比结果

### 对比分析

填写下表：

| 访问场景 | 结果 |
|----------|----------|
| 个人电脑 | ______ |
| Intune 托管设备 | ______ |

---

### 思考

为什么同一个用户：

```text
以实际实验账户为准。
```

在不同设备上会得到不同结果？

记录答案：

________________________________________________

________________________________________________

________________________________________________

---

## Conditional Access 分析

### Zero Trust 决策逻辑

本次访问过程实际验证：

```text
IF

User = Valid

AND

MFA = Completed

AND

Device = Compliant

THEN

Allow Access
```

---

### 问题

如果员工使用：

□ 个人电脑

□ 未打补丁电脑

□ 被恶意软件感染设备

访问企业文档，

企业是否应该允许访问？

□ 是

□ 否

---

### 原因

_________________________________

_________________________________

---

## AI 时代的设备安全

Contoso 计划部署：

- Microsoft 365 Copilot
- Enterprise Search
- AI Agent

---

### 思考

如果攻击者通过非合规设备访问：

```text
Copilot
```

可能获得哪些信息？

请选择：

□ 邮件

□ Teams 消息

□ SharePoint 文档

□ 企业知识库

---

### 讨论

为什么 AI 部署前必须完成设备合规建设？

_________________________________

_________________________________

_________________________________

---

## 验证成功

如果您完成以下操作，则本实验完成：

✅ 完成 MFA 登录

✅ 使用个人电脑访问资源

✅ 使用合规设备访问资源

✅ 观察条件访问策略效果

✅ 理解 Device Compliance

✅ 理解 Conditional Access

---

## 实验总结

在本实验中，您验证了：

```text
正确用户
≠
自动允许访问
```

Zero Trust 要求同时验证：

```text
身份
+
设备
+
访问条件
```

只有满足全部条件，

系统才会允许访问企业资源。

这正是：

```text
Never Trust
Always Verify
```

原则在设备安全领域的体现。

---

## 下一实验

➡ [实验 05 - ZTNA 网络访问验证](../Lab05-ZTNA-Network-Access-Validation/Lab05-ZTNA-Network-Access-Validation.html)

在下一实验中，您将验证：

```text
可信用户
+
可信设备
+
可信网络路径
=
安全访问企业资源
```

进一步体验 Zero Trust 网络访问模型。