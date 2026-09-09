---
lab:
  title: 零信任实验准备
  description: 在本准备中，您将完成实验所需的环境配置和工具安装。
  duration: 5 分钟
  level: 200
  islab: true
---

# 零信任实验准备

## 实验简介

本实验旨在确保您具备进行后续零信任评估实验所需的环境和工具。您将完成以下准备工作：

- 配置实验环境
- 安装必要的工具和软件
- 验证环境配置是否正确
- 确保您能够顺利进行后续实验

----

## 实验环境

### 学员设备

- Windows 或 macOS
- Microsoft Edge 或 Chrome 浏览器
- Internet 连接

----

### 实验账号

实验过程中将使用预配置账号：

| 账号类型 | 用途 |
|----------|----------|
| User | 普通用户体验 |
| Admin | 管理员演示（仅讲师使用） |

----

## 配置实验环境

1. 获取实验所需的 Microsoft 365 账户名和密码，并确保您能够登录到 Microsoft 365 管理中心。[Microsoft 365 管理中心](https://admin.microsoft.com/)
2. 确保您的浏览器已更新到最新版本，推荐使用 Microsoft Edge。
3. 确保您的网络连接稳定，并能够访问 Microsoft 365 服务。
4. 确保您的操作系统已更新到最新版本。
5. 安装必要的工具和软件，包括：
   - Microsoft Edge 浏览器
   - Visual Studio Code（可选，用于查看和编辑实验文件）
   - PowerShell（用于执行命令行操作）
   - 按后续实验需要安装对应的 PowerShell 模块。AzureAD 模块已弃用；除非讲师另行说明，不要安装或使用该模块。
   - 确保您已安装最新版本的 Microsoft 365 CLI（可选，用于命令行操作）。
6. 验证环境配置是否正确：
   - 打开浏览器，使用隐身窗口，新添加配置文件，或者访客模式，访问 Microsoft 365 管理中心，确保能够成功登录。
   - 打开 PowerShell，运行 `Get-Module -ListAvailable`，确认讲师要求的模块和版本已安装。若不参加真实租户评估，可跳过 Assessment PowerShell 模块。
