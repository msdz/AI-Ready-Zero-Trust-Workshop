---
lab:
  title: 实验 05 - Global Secure Access 与 ZTNA 验证
  description: 体验 Microsoft Global Secure Access 提供的 Zero Trust Network Access（ZTNA）能力，验证身份、设备和访问策略如何共同保护企业资源。
  duration: 20 分钟
  level: 200
  islab: true
  primarytopics:
    - Microsoft Entra ID
    - Global Secure Access
    - Zero Trust Network Access
    - Conditional Access
    - Network Security
---

# 实验 05 - Global Secure Access 与 ZTNA 验证

## 实验目标

完成本实验后，您将能够：

✅ 激活 Global Secure Access Administrator

✅ 了解 Global Secure Access 架构

✅ 理解传统 VPN 与 ZTNA 的区别

✅ 验证基于身份和设备的访问控制

✅ 查看访问日志

✅ 理解 Zero Trust 网络访问原则

---

# 实验场景

Contoso 公司正在建设 Zero Trust 网络架构。

企业希望：

```text
不依赖传统 VPN

而是基于：

用户身份
设备状态
访问策略

控制企业资源访问
```

因此部署：

```text
Microsoft Global Secure Access
```

实现：

```text
Zero Trust Network Access（ZTNA）
```

---

# 任务1 激活实验角色

使用：

```text
zta-adminXX
```

登录：

```text
https://entra.microsoft.com
```

进入：

```text
Identity Governance
↓
Privileged Identity Management
↓
My Roles
```

找到：

```text
Global Secure Access Administrator
```

中文：

```text
全局安全访问管理员
```

点击：

```text
Activate
```

完成：

```text
MFA
```

输入理由：

```text
Lab05 - ZTNA Validation
```

提交激活。

---

## 验证结果

确认：

```text
Global Secure Access Administrator

↓

Active
```

记录到期时间：

```text
____________________
```

---

# 任务2 查看 Global Secure Access

使用管理员账户进入：

```text
Global Secure Access
```

查看：

```text
Dashboard
```

观察：

```text
Internet Access

Private Access

Secure Web Gateway
```

记录看到的服务：

```text
________________________________

________________________________
```

---

# 任务3 查看访问策略

讲师展示实验环境配置。

观察：

```text
条件访问策略

Global Secure Access策略

应用访问策略
```

记录：

```text
□ Require MFA

□ Require Compliant Device

□ 指定用户组

□ 指定应用访问
```

---

# 任务4 使用普通用户访问资源

使用：

```text
zta-userXX
```

登录。

在：

```text
Intune 合规设备
```

上访问讲师提供的实验资源。

示例：

```text
SharePoint

Web App

Private App

测试站点
```

实际资源以讲师提供为准。

---

记录：

```text
□ 成功访问

□ 被阻止访问
```

---

# 任务5 查看访问日志

使用管理员账户进入：

```text
Global Secure Access
```

查看：

```text
Traffic Logs
```

或：

```text
Activity Logs
```

---

记录：

| 项目 | 内容 |
|--------|--------|
| User | __________ |
| Application | __________ |
| Device | __________ |
| Access Result | __________ |

---

## 思考

日志记录了哪些内容？

________________________________

________________________________

________________________________

---

# 任务6 验证访问控制

讲师演示：

```text
非合规设备

或

未授权设备

访问同一资源
```

观察结果。

---

记录：

| 场景 | 结果 |
|--------|--------|
| 合规设备 | __________ |
| 非合规设备 | __________ |

---

## 思考

为什么相同用户：

```text
zta-userXX
```

在不同设备上可能得到不同结果？

________________________________

________________________________

________________________________

---

# VPN 与 ZTNA 对比

## 传统 VPN

```text
连接网络

↓

获得网络访问能力

↓

持续信任
```

---

## ZTNA

```text
验证身份

↓

验证 MFA

↓

验证设备

↓

验证授权资源

↓

允许访问
```

---

## 对比分析

| 项目 | 传统 VPN | ZTNA |
|--------|--------|--------|
| 用户验证 | 登录时验证 | 持续验证 |
| MFA | 可选 | 推荐 |
| 设备验证 | 通常较弱 | 核心要求 |
| 应用级控制 | 较少 | 支持 |
| 条件访问 | 较少 | 深度集成 |
| Zero Trust | 有限 | 原生支持 |

---

# Zero Trust 网络原则

本实验验证：

```text
IF

User = Valid

AND

MFA = Success

AND

Device = Compliant

AND

Application = Authorized

THEN

Allow Access
```

---

不是：

```text
连接网络

=

自动获得信任
```

---

# AI 时代的网络安全

Contoso 正在部署：

- Microsoft 365 Copilot
- Enterprise Search
- AI Agent

---

## 思考

如果攻击者通过：

```text
未授权设备

或

非合规设备
```

访问企业资源，

可能获得：

```text
□ 邮件

□ Teams 信息

□ SharePoint 文件

□ 企业知识库

□ Copilot 相关数据
```

---

## 讨论

为什么部署 AI 之前需要完成：

```text
身份治理

+

设备治理

+

ZTNA
```

建设？

________________________________

________________________________

________________________________

---

# 实验验证

完成以下任务：

```text
□ 已激活 Global Secure Access Administrator

□ 已查看 Global Secure Access 服务

□ 已查看访问策略

□ 已使用普通用户访问实验资源

□ 已查看访问日志

□ 已理解 VPN 与 ZTNA 的区别

□ 已理解 Global Secure Access 架构

□ 已理解 Zero Trust 网络原则
```

---

# 实验总结

本实验验证：

```text
可信身份

+

可信设备

+

授权应用

=

允许访问
```

而不是：

```text
连接网络

=

获得信任
```

Global Secure Access 实现了：

```text
Never Trust

Always Verify
```

在网络访问层面的落地。

---

## 下一实验

➡ [实验 06 - AI Apps 文件访问验证](../Lab06-AI-Apps-File-Access-Validation/Lab06-AI-Apps-File-Access-Validation.html)

在下一实验中，您将验证：

```text
AI 是否会绕过权限控制？
```

理解 AI Security 与 Zero Trust 的关系。