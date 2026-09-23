---
lab:
  title: 实验 03 - 身份验证与抗钓鱼 MFA 验证
  description: 在本实验中，您将体验 Microsoft Entra MFA 身份验证流程，验证密码泄露场景下的身份保护能力，并理解 Microsoft 推荐的 Phishing-resistant MFA（抗钓鱼 MFA）最佳实践。
  duration: 20 分钟
  level: 200
  islab: true
  primarytopics:
    - Microsoft Entra ID
    - Multi-Factor Authentication
    - Authentication Strength
    - Passwordless Authentication
    - Phishing-resistant MFA
    - Zero Trust
---

# 实验 03 - 身份验证与抗钓鱼 MFA 验证

## 实验背景

在前面的实验中，您已经了解：

```text
Identity
是 Zero Trust 的核心控制面
```

攻击者最常见的攻击方式之一：

```text
钓鱼邮件

↓

窃取账号密码

↓

登录企业系统
```

如果企业仅依赖：

```text
用户名
+
密码
```

进行身份验证，

攻击者一旦获得密码便有可能访问企业资源。

Microsoft Entra 通过：

- MFA
- Authentication Strength
- Passwordless Authentication
- Passkey
- Phishing-resistant MFA

等能力降低账号被盗风险。

---

## 实验目标

完成本实验后，您将能够：

✅ 理解密码泄露攻击场景

✅ 理解 Multi-Factor Authentication（MFA）

✅ 理解 Authentication Strength

✅ 完成 MFA 登录验证

✅ 验证密码泄露场景下的访问控制效果

✅ 理解 Microsoft 推荐的抗钓鱼 MFA

✅ 理解 Identity 在 Zero Trust 中的重要作用

---

# 实验场景

Contoso 公司已经部署：

- Microsoft 365
- Microsoft Teams
- SharePoint Online
- Microsoft 365 Copilot

安全团队发现：

某员工在钓鱼网站中输入了企业账号密码。

攻击者已经获得：

```text
用户名

密码
```

安全团队希望验证：

```text
即使密码已经泄露

攻击者是否还能进入企业系统？
```

---

# 任务 1 - 激活实验管理员角色

本实验需要使用：

```text
zta-adminXX
```

管理员账户。

---

## Step 1

打开：

```text
https://entra.microsoft.com
```

使用：

```text
zta-adminXX
```

登录。

---

## Step 2

进入：

```text
Identity Governance

↓

Privileged Identity Management

↓

My Roles

↓

Microsoft Entra Roles
```

---

## Step 3

在 Eligible Assignments 中找到：

```text
Authentication Administrator
```

中文：

```text
身份验证管理员
```

---

## Step 4

选择：

```text
Activate
```

---

## Step 5

完成 MFA。

---

## Step 6

填写理由：

```text
Lab03 - MFA Validation
```

---

## Step 7

提交激活。

---

## 验证结果

确认：

```text
Authentication Administrator

↓

Active
```

记录到期时间：

```text
____________________
```

---

# 任务 2 - 登录普通用户账户

使用：

```text
zta-userXX
```

普通用户账户。

---

## Step 1

打开：

```text
https://www.microsoft365.com
```

---

## Step 2

输入：

```text
zta-userXX
```

---

## Step 3

输入密码。

---

## Step 4

选择：

```text
登录
```

---

# 任务 3 - 完成 MFA 验证

根据租户配置，

系统可能要求：

### Microsoft Authenticator

或

### TOTP 动态验证码

或

### 号码匹配

或

### Passkey

实际方式以当前 Tenant 配置为准。

---

## Step 1

完成 MFA。

---

## Step 2

记录触发情况：

| 验证项 | 结果 |
|----------|----------|
| 是否要求 MFA | □ 是 □ 否 |
| 是否完成验证 | □ 是 □ 否 |
| 是否成功登录 | □ 是 □ 否 |

---

# 任务 4 - 模拟密码泄露

## 攻击场景

攻击者已经获得：

```text
用户名

密码
```

但攻击者不具备：

```text
Microsoft Authenticator

动态验证码

Passkey

FIDO2 Key
```

等第二因素。

---

## 问题

攻击者是否能够成功登录？

```text
□ 可以

□ 不可以
```

---

## 请说明原因

________________________________________________

________________________________________________

________________________________________________

---

# 任务 5 - 理解 Microsoft MFA

## 观察

企业仅使用：

```text
密码
```

时：

攻击者获得密码即可登录。

---

企业启用：

```text
密码

+

MFA
```

后：

攻击者除了密码之外，

还需要：

```text
第二验证因素
```

才能完成登录。

---

## 思考

MFA 带来的价值是什么？

________________________________________________

________________________________________________

________________________________________________

---

# 任务 6 - 理解 Authentication Strength

Microsoft Entra 提供：

```text
Authentication Strength
```

用于定义登录时允许使用的认证方式。

---

### 基础 MFA

例如：

```text
Password

+

SMS

或

Authenticator
```

---

### Passwordless MFA

例如：

```text
Microsoft Authenticator

Passkey

Windows Hello
```

---

### Phishing-resistant MFA

微软推荐：

```text
Passkey

Windows Hello for Business

FIDO2 Security Key

Certificate-based Authentication
```

---

## 思考题

以下哪些属于微软推荐的

Phishing-resistant MFA？

```text
□ SMS

□ Email OTP

□ Microsoft Authenticator Code

□ FIDO2 Security Key

□ Windows Hello for Business

□ Passkey
```

---

# 任务 7 - AI 时代身份安全

## 场景

企业已经部署：

```text
Microsoft 365 Copilot
```

---

如果账号被盗，

攻击者可能访问：

```text
邮件

文档

SharePoint 文件

Teams 内容

Copilot 可访问的数据
```

---

## 问题

为什么在 AI 时代必须强化身份验证？

________________________________________________

________________________________________________

________________________________________________

---

# Zero Trust 观点

传统模式：

```text
知道密码

=

可信用户
```

---

Zero Trust：

```text
知道密码

≠

可信用户
```

系统还需要持续验证：

```text
用户身份

设备状态

认证强度

访问风险

访问位置

访问行为
```

---

这就是：

```text
Never Trust

Always Verify
```

---

# Microsoft 推荐身份保护路线

传统方式：

```text
Password
```

↓

```text
Password + SMS
```

↓

```text
Password + OTP
```

---

现代方式：

```text
Passwordless Authentication
```

↓

```text
Passkey
```

↓

```text
Phishing-resistant MFA
```

---

# 实验验证

完成以下内容：

```text
□ 已激活 Authentication Administrator

□ 已完成 MFA 登录

□ 已验证密码泄露场景

□ 已理解 MFA 工作机制

□ 已理解 Authentication Strength

□ 已理解 Phishing-resistant MFA

□ 已理解 Zero Trust Identity
```

---

# 实验总结

本实验验证：

```text
密码

≠

身份
```

即使攻击者获得密码，

通常仍无法仅凭密码完成登录。

企业应逐步减少依赖：

- SMS
- Voice
- Email OTP

并逐步采用：

- Microsoft Authenticator
- Windows Hello for Business
- Passkey
- FIDO2 Security Key

等更强的身份验证方式。

Identity 是 Zero Trust 的第一道防线。

---

# 下一实验

➡ [实验 04 - 合规设备访问验证](../Lab04-Intune-Compliance-Validation/Lab04-Intune-Compliance-Validation.html)

下一实验将验证：

```text
正确用户

+

可信设备

=

允许访问企业资源
```

并体验：

```text
Conditional Access

+

Device Compliance
```

的实际效果。
``