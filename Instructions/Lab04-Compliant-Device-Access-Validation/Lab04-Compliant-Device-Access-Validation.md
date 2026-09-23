---
lab:
  title: 实验 04 - 合规设备访问验证
  description: 验证 Microsoft Entra 条件访问和 Intune 合规设备策略，体验同一用户在不同设备上的访问差异。
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

## 实验目标

完成本实验后，您将能够：

✅ 激活 Intune Administrator

✅ 查看 Intune 设备状态

✅ 理解 Device Compliance

✅ 理解 Conditional Access

✅ 验证合规设备访问

✅ 验证非合规设备访问限制

✅ 理解 Zero Trust 设备信任模型

---

# 实验场景

Contoso 已部署：

- Microsoft Entra
- Microsoft Intune
- Conditional Access

企业规定：

```text
仅允许合规设备访问企业文档
```

访问条件：

```text
用户身份有效

+
完成 MFA

+
设备合规

=

允许访问
```

---

# 任务1 激活 Intune Administrator

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

在 Eligible Assignments 中找到：

```text
Intune Administrator
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
Lab04 - Intune Compliance Validation
```

提交激活。

---

## 验证

确认：

```text
Intune Administrator

↓

Active
```

记录到期时间：

```text
____________________
```

---

# 任务2 查看设备状态

管理员账户进入：

```text
https://intune.microsoft.com
```

进入：

```text
Devices
↓
All Devices
```

找到实验用设备。

记录：

| 项目 | 结果 |
|--------|--------|
| Device Name | __________ |
| Managed | □ Yes □ No |
| Compliant | □ Yes □ No |
| Ownership | __________ |

---

# 任务3 查看条件访问策略

讲师展示实验策略。

观察内容：

```text
Users
```

```text
Applications
```

```text
Grant Controls
```

确认是否包含：

```text
□ Require MFA

□ Require compliant device
```

---

# 任务4 使用个人电脑访问资源

使用：

```text
zta-userXX
```

登录。

使用：

```text
学员自带设备
```

访问讲师提供的：

```text
SharePoint 站点
```

尝试打开：

```text
讲师指定实验文件
```

记录结果：

```text
□ 成功访问

□ 被阻止

□ 要求设备合规
```

记录错误信息：

________________________________

________________________________

---

# 任务5 使用 Intune 合规设备访问资源

在实验区使用：

```text
Intune 合规 Windows 11 PC
```

使用同一个：

```text
zta-userXX
```

登录。

访问相同：

```text
SharePoint 站点
```

打开相同实验文件。

记录结果：

```text
□ 成功访问

□ 被阻止
```

---

# 对比分析

填写：

| 场景 | 结果 |
|--------|--------|
| 学员自带设备 | __________ |
| Intune合规设备 | __________ |

---

## 思考

为什么同一个用户：

```text
zta-userXX
```

在不同设备上会得到不同结果？

_________________________________

_________________________________

_________________________________

---

# Conditional Access 决策逻辑

本实验实际验证：

```text
IF

User = Valid

AND

MFA = Success

AND

Device = Compliant

THEN

Allow Access
```

---

# AI 时代的设备安全

如果攻击者获得：

```text
正确用户名
正确密码
```

甚至完成：

```text
MFA
```

但使用：

```text
非合规设备
```

系统仍然可以阻止访问。

---

## 思考

如果攻击者通过非合规设备访问：

```text
Copilot

SharePoint

Teams

Enterprise Search
```

可能获得哪些数据？

```text
□ 邮件

□ Teams消息

□ SharePoint文档

□ 企业知识库
```

---

# 实验验证

完成以下内容：

```text
□ 已激活 Intune Administrator

□ 已查看设备状态

□ 已查看条件访问策略

□ 已使用个人设备访问资源

□ 已使用合规设备访问资源

□ 已验证不同访问结果

□ 已理解 Device Compliance

□ 已理解 Conditional Access
```

---

# 实验总结

本实验验证：

```text
正确用户

≠

自动允许访问
```

Zero Trust 需要同时验证：

```text
身份

+

MFA

+

设备状态

+

访问策略
```

只有全部满足条件，

系统才允许访问企业资源。

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