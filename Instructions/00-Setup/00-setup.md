---
lab:
  title: 零信任实验准备
  description: 完成实验账户、PIM权限、浏览器环境以及Intune合规设备验证，为后续Lab01-Lab06做好准备。
  duration: 15分钟
  level: 200
  islab: true
---

# Lab00 - 零信任实验准备

## 实验目标

完成本实验后，您将能够：

- 登录实验租户
- 使用实验管理员账户访问 Microsoft Entra
- 查看 PIM 角色分配
- 登录普通用户账户
- 完成浏览器环境隔离
- 验证 Intune 合规设备
- 熟悉后续实验所需角色

---

# 实验资源

每个实验组将获得以下资源：

| 实验资源 | 数量 | 用途 |
|----------|----------|----------|
| PIM特权管理员账户 | 1个 | 激活实验角色 |
| 普通用户验证账户 | 1个 | 访问验证 |
| Intune合规Windows 11 PC | 1台（轮换） | 合规设备验证 |
| 学员自带设备 | 1台 | 非合规设备验证 |

---

# 实验账户说明

## PIM特权管理员账户

格式：

```text
zta-adminXX
```

示例：

```text
zta-admin01
```

管理员账户用于：

- Microsoft Entra
- PIM
- Intune
- SharePoint
- Global Secure Access

管理员权限通过PIM按需激活：

```text
Eligible
    ↓
Activate
    ↓
MFA
    ↓
Justification
    ↓
Active
```

默认：

```text
无活动管理员权限
```

---

## 普通用户验证账户

格式：

```text
zta-userXX
```

示例：

```text
zta-user01
```

普通用户用于：

- Microsoft 365 登录
- MFA验证
- 条件访问验证
- SharePoint访问
- AI应用访问
- ZTNA访问验证

普通用户：

```text
不具备任何管理员权限
```

---

## 实验账号对应关系

| 实验组 | 管理员账户 | 普通用户账户 |
|----------|----------|----------|
| Group01 | zta-admin01 | zta-user01 |
| Group02 | zta-admin02 | zta-user02 |
| Group03 | zta-admin03 | zta-user03 |

规则：

```text
zta-admin01

只管理

zta-user01
```

```text
zta-admin02

只管理

zta-user02
```

不要操作其他实验组账户。

---

# Intune合规设备

实验现场提供Windows 11设备。

设备已预先完成：

- Microsoft Entra Join
- Microsoft Intune注册
- 设备合规配置
- Edge配置
- GSA Client配置

主要用于：

```text
Lab04
Lab05
Lab06
```

请勿：

- Reset PC
- Remove Device
- Leave Organization
- 删除工作账户
- 卸载Company Portal
- 卸载GSA Client

---

# PIM角色对应关系

| 英文名称 | 中文名称 | 对应实验 |
|----------|----------|----------|
| Global Reader | 全局读取者 | Lab01 |
| Security Reader | 安全读取者 | Lab01、Lab02 |
| Authentication Administrator | 身份验证管理员 | Lab03 |
| Intune Administrator | Intune管理员 | Lab04 |
| Global Secure Access Administrator | 全局安全访问管理员 | Lab05 |
| SharePoint Administrator | SharePoint管理员 | Lab06 |

统一设置：

```text
Require MFA                : Yes
Require Justification      : Yes
Require Approval           : No
Require Ticket Information : No
Maximum Duration           : 1 Hour
```

---

# 任务1 获取实验资源

从讲师获取：

```text
实验组编号
管理员账户
普通用户账户
密码或TAP
实验Tenant
设备编号
```

记录：

```text
实验组: __________________

Tenant: __________________

管理员账户: __________________

普通用户账户: __________________

设备编号: __________________
```

---

# 任务2 登录管理员账户

打开 Microsoft Edge

创建新的配置文件：

```text
ZT-Admin
```

访问：

```text
https://entra.microsoft.com
```

使用：

```text
zta-adminXX
```

登录。

---

# 任务3 检查PIM角色

进入：

```text
Identity Governance
↓
Privileged Identity Management
↓
My Roles
↓
Microsoft Entra Roles
↓
Eligible Assignments
```

检查以下角色：

```text
□ Global Reader

□ Security Reader

□ Authentication Administrator

□ Intune Administrator

□ Global Secure Access Administrator

□ SharePoint Administrator
```

预期结果：

```text
看到Eligible Assignment

没有Active Assignment
```

---

# 任务4 登录普通用户

创建第二个Edge配置文件：

```text
ZT-User
```

访问：

```text
https://www.microsoft365.com
```

使用：

```text
zta-userXX
```

登录。

预期结果：

```text
成功登录Microsoft 365
```

---

# 任务5 验证会话隔离

确认：

```text
ZT-Admin
↓
zta-adminXX
```

```text
ZT-User
↓
zta-userXX
```

检查：

```text
□ 两个浏览器配置文件独立

□ 两个账号不会互相切换

□ 管理员账户不用于用户验证

□ 普通用户不用于管理员操作
```

---

# 任务6 检查Intune设备

检查：

```text
□ 设备正常启动

□ 正常联网

□ 可以打开Edge

□ 已连接工作账户

□ 无需重新注册

□ GSA Client正常
```

记录设备编号：

```text
____________________
```

---

# 任务7 验证基础访问

确认可访问：

```text
□ Microsoft 365

□ Microsoft Entra

□ Microsoft Intune

□ Microsoft Defender
```

---

# 后续实验角色激活

## Lab01

激活：

```text
Global Reader
```

或

```text
Security Reader
```

激活理由：

```text
Lab01 - Zero Trust Assessment
```

---

## Lab02

激活：

```text
Security Reader
```

激活理由：

```text
Lab02 - Risk Report Analysis
```

---

## Lab03

激活：

```text
Authentication Administrator
```

激活理由：

```text
Lab03 - MFA Validation
```

---

## Lab04

激活：

```text
Intune Administrator
```

激活理由：

```text
Lab04 - Intune Compliance Validation
```

---

## Lab05

激活：

```text
Global Secure Access Administrator
```

激活理由：

```text
Lab05 - ZTNA Validation
```

---

## Lab06

激活：

```text
SharePoint Administrator
```

激活理由：

```text
Lab06 - AI Apps File Access Validation
```

---

# 实验规则

必须遵守：

1. 只使用本组账户
2. 不操作其他实验组用户
3. 不共享密码和TAP
4. 每个Lab只激活当前需要角色
5. 不同时激活全部角色
6. 完成实验后停用角色
7. 不修改Intune设备注册状态
8. 不使用客户真实数据

---

# Setup检查表

## 账户

```text
□ 已获得管理员账户

□ 已获得普通用户账户

□ 已确认Tenant

□ 已确认实验组
```

## PIM

```text
□ 成功打开PIM

□ 可以看到Eligible角色

□ 当前无Active角色
```

## 浏览器

```text
□ 已建立ZT-Admin

□ 已建立ZT-User

□ 两个会话独立
```

## Intune设备

```text
□ 设备正常

□ 网络正常

□ Edge正常

□ GSA Client正常
```

## 实验准备

```text
□ 已了解Lab01角色

□ 已了解Lab02角色

□ 已了解Lab03角色

□ 已了解Lab04角色

□ 已了解Lab05角色

□ 已了解Lab06角色
```

---

# 完成标准

完成本实验后：

```text
管理员账户
✓ 可以登录Entra
✓ 可以查看PIM角色
✓ 默认无活动权限

普通用户
✓ 可以登录Microsoft 365
✓ 无管理员权限

Intune设备
✓ 正常工作
✓ 保持托管状态

浏览器
✓ 管理员和用户会话隔离
```

准备完成后，进入：

```text
Lab01 - 零信任评估
```