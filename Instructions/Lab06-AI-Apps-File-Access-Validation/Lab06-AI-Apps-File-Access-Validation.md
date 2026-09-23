---
lab:
  title: 实验 06 - AI 应用文件访问验证
  description: 验证 Microsoft 365 Copilot 与 SharePoint 权限模型的关系，理解 AI 应用不会突破用户现有授权边界。
  duration: 20 分钟
  level: 200
  islab: true
  primarytopics:
    - Microsoft 365 Copilot
    - SharePoint Online
    - Data Governance
    - Microsoft Purview
    - Zero Trust
---

# 实验 06 - AI 应用文件访问验证

## 实验目标

完成本实验后，您将能够：

✅ 激活 SharePoint Administrator

✅ 理解 Copilot 数据访问模型

✅ 理解 SharePoint 权限继承

✅ 验证 AI 不突破用户权限

✅ 理解数据治理原则

✅ 理解 AI Ready 安全架构

---

# 实验场景

Contoso 已部署：

- Microsoft 365
- SharePoint Online
- Microsoft 365 Copilot

企业希望验证：

```text
Copilot

是否会突破用户权限？
```

---

## 核心问题

如果用户无法访问某文件：

```text
Copilot

能否帮用户读取？
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
SharePoint Administrator
```

中文：

```text
SharePoint 管理员
```

选择：

```text
Activate
```

完成：

```text
MFA
```

填写理由：

```text
Lab06 - AI Apps File Access Validation
```

---

## 验证结果

确认：

```text
SharePoint Administrator

↓

Active
```

记录到期时间：

```text
____________________
```

---

# 任务2 查看实验站点

使用管理员账户进入：

```text
SharePoint Admin Center
```

查看讲师准备的实验站点。

观察：

```text
站点权限

成员权限

访客权限

文件权限
```

---

## 思考

权限决定什么？

```text
□ 用户是否可以访问文件

□ 用户是否可以查看文件

□ 用户是否可以编辑文件
```

---

# 任务3 使用普通用户访问文件

使用：

```text
zta-userXX
```

登录。

访问讲师提供的：

```text
实验 SharePoint 站点
```

---

观察以下资源：

```text
公开文档

受限文档

敏感文档
```

实际名称以讲师提供为准。

---

记录：

| 文件类型 | 能否访问 |
|----------|----------|
| 公开文档 | □ 是 □ 否 |
| 受限文档 | □ 是 □ 否 |
| 敏感文档 | □ 是 □ 否 |

---

# 任务4 验证 Copilot 访问行为

打开：

```text
Microsoft 365 Copilot Chat
```

如果现场环境未配置 Copilot License，则由讲师演示。

---

输入：

```text
请总结我有权限访问的项目文档。
```

观察：

```text
Copilot 是否返回内容
```

---

记录：

```text
□ 返回相关文件

□ 引用了可访问内容

□ 提供了来源引用
```

---

# 任务5 验证权限边界

尝试询问：

```text
请总结我无权访问的项目文档。
```

或：

```text
请显示财务预算文件内容。
```

其中目标文件应为：

```text
当前用户无权访问
```

的数据。

---

观察结果：

```text
□ Copilot 无法引用

□ Copilot 未返回文件内容

□ Copilot 无法突破权限
```

---

# 对比分析

| 验证项 | 已授权文件 | 未授权文件 |
|----------|----------|----------|
| 用户可以打开 | _____ | _____ |
| Copilot可以引用 | _____ | _____ |
| Copilot可以总结 | _____ | _____ |

---

## 结论

完成填写：

```text
Copilot 访问能力由

_____________________

决定。
```

---

# 任务6 数据保护演示

由讲师演示：

```text
敏感度标签

Sensitivity Labels
```

以及：

```text
文件加密
```

---

观察：

```text
已加密文件
```

下载后：

```text
是否仍受保护
```

---

记录：

```text
□ 文件离开SharePoint后仍受保护

□ 未授权用户无法打开

□ 未授权应用无法读取
```

---

# AI Ready 数据治理模型

## 第一层

### SharePoint 权限

决定：

```text
谁可以访问文件
```

---

## 第二层

### 敏感度标签 + 加密

决定：

```text
谁可以打开文件
```

---

## 第三层

### Microsoft Purview

决定：

```text
敏感内容如何使用
```

---

# 知识检查

## 问题1

Copilot 是否拥有独立权限？

```text
□ 是

□ 否
```

---

## 问题2

Copilot 能否读取用户无权限访问的文件？

```text
□ 是

□ 否
```

---

## 问题3

SharePoint 权限决定什么？

```text
□ 文件是否存在

□ 用户是否可以访问
```

---

## 问题4

敏感度标签主要作用是什么？

```text
□ 文件命名

□ 加密与访问控制
```

---

# AI Ready 安全模型

本次 Workshop 实际完成：

```text
Identity
↓
MFA
↓
PIM
↓
Device
↓
Network
↓
Data
↓
AI
```

---

# 实验验证

完成以下内容：

```text
□ 已激活 SharePoint Administrator

□ 已查看实验站点

□ 已验证文件权限

□ 已验证 Copilot 引用授权内容

□ 已验证 Copilot 不突破权限

□ 已观察敏感度标签保护

□ 已理解数据治理模型
```

---

# 实验总结

本实验验证：

```text
Copilot 能访问什么

=

用户能访问什么
```

---

```text
权限决定

Copilot 是否能引用数据
```

---

```text
敏感度标签 + 加密

决定谁能打开数据
```

---

```text
Purview

决定敏感数据如何治理
```

---

因此：

```text
Microsoft 365 Copilot

不是新的数据入口
```

而是建立在现有：

```text
身份

设备

网络

权限

数据治理
```

基础之上的 AI 能力。

---

# 工作坊完成

恭喜完成：

✅ Lab01 零信任评估

✅ Lab02 风险分析

✅ Lab03 身份验证与抗钓鱼 MFA

✅ Lab04 合规设备访问

✅ Lab05 Global Secure Access 与 ZTNA

✅ Lab06 AI 应用文件访问验证

---

您已经完整体验：

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

组成的 AI Ready Zero Trust 安全体系。
