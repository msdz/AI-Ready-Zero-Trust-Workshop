---
  title: Lab06 - AI Apps File Access Validation (Instructor Guide)
  description: Microsoft 365 Copilot 数据访问与数据治理验证实验环境准备手册
  audience: Instructor
  published: false
---

# Lab06 - AI Apps File Access Validation

# 实验目标

本实验用于帮助学员理解：

```text
Copilot 能访问什么数据
=
用户能访问什么数据
```

并验证以下三个核心问题：

### 问题 1

Copilot 是否会突破 SharePoint 权限？

### 问题 2

文件下载到本地后是否仍然受到保护？

### 问题 3

企业是否可以进一步限制 Copilot 处理敏感内容？

---

# Microsoft 365 Copilot 数据访问模型

讲师需要向学员解释：

```text
用户身份
        ↓
文件权限
        ↓
敏感度标签
        ↓
加密与授权
        ↓
Copilot Grounding
        ↓
生成回答
```

Copilot 不会自动扩大用户权限。

Copilot 只能引用用户有权访问的内容；实际结果还取决于许可证、索引和租户策略。

---

# 实验账号准备

准备以下实验账号：

```text
User01
User02
User03
User04
User05
```

账号要求：

| 配置项 | 要求 |
|----------|----------|
| Microsoft 365 License | 已分配 |
| Microsoft 365 Copilot License | 已分配 |
| MFA | 已完成 |
| 可登录 Microsoft 365 | 是 |

---

# SharePoint 实验站点准备

## Step 1

创建 SharePoint Site：

```text
AI Ready Security Lab
```

建议 Site URL：

```text
https://<tenant>.sharepoint.com/sites/AIReadySecurityLab
```

---

## Step 2

创建文档库：

```text
AI-Ready-Security-Lab
```

---

# 实验文件准备

## 文件 1

文件名：

```text
01_Public_Launch_Overview.docx
```

用途：

```text
验证 Copilot 能访问公开内容
```

建议内容：

```text
项目名称：
Product Launch 2027

项目代号：
LaunchOne

发布日期：
2027-03-18

目标市场：
中国区制造业客户
```

---

### 权限配置

授予：

```text
User01
User02
User03
User04
User05
```

验证：

```text
User03 能打开文件
```

---

## 文件 2

文件名：

```text
02_Executive_Strategy_2027.docx
```

用途：

```text
验证 Copilot 不突破权限
```

建议内容：

```text
项目代号：
Phoenix-2027

审批预算：
8750万元

战略负责人：
Executive Team

计划完成时间：
2027年6月
```

---

### SharePoint 权限配置

停止继承权限：

```text
Manage Access
→ Advanced
→ Stop Inheriting Permissions
```

---

仅授予：

```text
User01
User02
```

读取权限。

---

确认以下账号无权限：

```text
User03
User04
User05
```

---

### 权限验证

使用：

```text
User01
```

访问：

```text
02_Executive_Strategy_2027.docx
```

预期：

```text
成功
```

---

使用：

```text
User03
```

访问同一链接。

预期：

```text
拒绝访问
```

或者：

```text
Request Access
```

---

> [!IMPORTANT]
>
> 如果 User03 可以打开文件：
>
> 不要开始实验。
>
> 请检查：
>
> - Microsoft 365 Group
> - SharePoint Group
> - Teams Membership
> - Document Sharing Link
> - Site Permissions

---

## 文件 3

文件名：

```text
03_Confidential_Budget.xlsx
```

用途：

```text
验证数据离开 SharePoint 后仍然受到保护
```

建议内容：

```text
项目名称：
Project Falcon

总预算：
12亿元

审批状态：
董事会审批中

目标完成日期：
2027-09-30
```

---

# Microsoft Purview 标签准备

## Step 1

进入：

```text
Microsoft Purview Portal
```

---

## Step 2

导航：

```text
Solutions
→ Information Protection
→ Sensitivity Labels
```

---

## Step 3

创建标签：

```text
高度机密 - 指定用户
```

---

### 标签配置建议

范围：

```text
Files and Emails
```

---

启用：

```text
Encryption
```

---

配置权限：

允许：

```text
User01
User02
```

---

拒绝：

```text
User03
User04
User05
```

---

## Step 4

发布标签。

等待同步。

---

## Step 5

使用 User01 打开：

```text
03_Confidential_Budget.xlsx
```

应用标签：

```text
高度机密 - 指定用户
```

并保存。

---

### 验证

| 用户 | 结果 |
|----------|----------|
| User01 | 可以打开 |
| User02 | 可以打开 |
| User03 | 无法打开 |
| User04 | 无法打开 |
| User05 | 无法打开 |

---

# 第三方应用验证准备

目的：

```text
验证保护跟随文件
```

而不是：

```text
保护跟随SharePoint
```

---

## Step 1

使用 User01 下载：

```text
03_Confidential_Budget.xlsx
```

---

## Step 2

使用：

```text
Excel + User01
```

打开。

预期：

```text
成功
```

---

## Step 3

使用：

```text
未授权身份
```

或者：

```text
未授权应用会话
```

打开。

预期：

```text
无法读取内容
```

或：

```text
需要授权账号登录
```

---

> [!NOTE]
>
> 这里验证的是：
>
> ```text
> 敏感度标签
> +
> 加密授权
> ```
>
> 不是 DLP。
>
> 在标签加密成功写入文件且应用支持该保护时，数据保护可以随文件保留。

---

# 可选高级演示

## Microsoft Purview DLP

本部分不属于学员实验主线。

仅用于高级演示。

---

目标：

```text
用户有权限

≠

Copilot 一定允许处理内容
```

---

创建或启用租户当前版本中用于限制 Copilot 处理敏感内容的 DLP 策略。策略名称和菜单位置请以现场 Purview 门户为准。

```text
限制 Copilot 处理敏感内容的策略（名称和菜单位置以当前 Purview 门户为准）
```

---

条件：

```text
Content Contains Sensitivity Label
```

标签：

```text
高度机密 - 指定用户
```

---

位置：

```text
Microsoft 365 Copilot
Copilot Chat
```

---

操作：

```text
Restrict Processing
```

---

验证：

### User01

```text
能打开文件
```

结果：

✅

---

Copilot：

```text
请总结
03_Confidential_Budget.xlsx
```

结果：

❌

---

说明：

```text
权限控制
决定访问

DLP
决定AI处理
```

---

# 现场演示顺序

## Demo 1

User03：

```text
请总结

01_Public_Launch_Overview.docx
```

成功。

---

讲师说明：

```text
Copilot 可以访问
用户已经有权限访问的数据
```

---

## Demo 2（最重要）

User01：

```text
请总结

02_Executive_Strategy_2027.docx
```

成功。

返回：

```text
Phoenix-2027
8750万元
```

---

切换：

```text
User03
```

执行相同提示。

失败。

不会返回：

```text
Phoenix-2027
```

---

讲师说明：

```text
Copilot 不突破权限
```

---

## Demo 3

User01：

打开：

```text
03_Confidential_Budget.xlsx
```

成功。

---

下载文件。

---

切换：

```text
User03
```

尝试打开。

失败。

---

讲师说明：

```text
数据离开 SharePoint
仍然受到保护
```

---

## Demo 4（可选）

启用 DLP。

---

User01：

```text
打开文件
```

成功。

---

Copilot：

```text
请总结文件
```

失败。

---

讲师说明：

```text
权限决定是否访问

DLP决定是否允许AI处理
```

---

# 讲师最终检查表

活动开始前确认：

- [ ] User01~User05 可登录
- [ ] User01~User05 可使用 Copilot
- [ ] 文件1所有人可访问
- [ ] 文件2仅 User01、User02 可访问
- [ ] User03 无法访问文件2
- [ ] 文件3应用敏感度标签
- [ ] 文件3已加密
- [ ] User03 无法打开文件3
- [ ] Copilot 已完成预测试
- [ ] Phoenix-2027 等唯一验证信息已确认

---

# 收尾话术

通过本实验，学员已经验证：

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

完整链路。

对于 Copilot：

```text
Copilot 不突破权限
```

对于数据：

```text
数据离开 SharePoint
仍然受到保护
```

对于治理：

```text
Purview 可以限制 AI 如何处理敏感内容
```

这就是 AI Ready 企业安全架构的核心原则：

```text
安全拥抱 AI
而不是限制 AI
```
