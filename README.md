# 🖥️ 七彩虹 B860M · OpenCore Hackintosh

**Intel Core Ultra 7 265K · AMD Radeon RX 6950 XT · Arrow Lake-S · B860 · macOS Sequoia 15 · OpenCore 1.0.x · OCLP**

<div align="center">

![CPU](https://img.shields.io/badge/CPU-Ultra_7_265K_Arrow_Lake-0071C5?style=flat-square)
![GPU](https://img.shields.io/badge/GPU-RX_6950_XT_Navi_21-ED1C24?style=flat-square)
![RAM](https://img.shields.io/badge/RAM-32_GB_DDR5-8B5CF6?style=flat-square)
![OpenCore](https://img.shields.io/badge/OpenCore-1.0.x-9cf?style=flat-square)
![Chipset](https://img.shields.io/badge/Chipset-B860-00A3E0?style=flat-square)
![macOS](https://img.shields.io/badge/macOS-Sequoia_15-0071BC?style=flat-square)
![Status](https://img.shields.io/badge/Status-Working-brightgreen?style=flat-square)

**[🖥️ 硬件配置](#-硬件配置) · [⚙️ BIOS 设置](#%EF%B8%8F-bios-设置) · [✅ 驱动状态](#-驱动状态) · [📦 EFI 配置](#-efi-配置) · [🚀 快速开始](#-快速开始)**

</div>

---

## 🖥️ 硬件配置

| 组件 | 型号 | 规格 | 驱动情况 |
|:-----|:-----|:-----|:--------:|
| **型号** | COLORFUL BATTLE-AX B860M-P WIFI | 七彩虹 B860M 主板 | ✅ |
| **主板** | COLORFUL B860M | B860 (Arrow Lake-S) | ✅ |
| **CPU** | Intel Core Ultra 7 265K | 20C/20T @ 3.90-5.50 GHz | ✅ |
| **独显** | AMD Radeon RX 6950 XT | 16 GB (Navi 21, 1002-73A5) | ⚠️ 需仿冒 |
| **内存** | DDR5 | 32 GB | ✅ |
| **系统盘** | SATA SSD | 1 TB | ✅ |
| **声卡** | Realtek ALC897 | HDA: 10EC-0897 | ✅ |
| **有线网卡** | Realtek RTL8168 | 10EC-8168 | ✅ |
| **Wi-Fi** | Intel Wi-Fi 6 AX101 | 8086-7F70 | ⚠️ 需 OCLP 补丁 |
| **显示器** | 27" 1080p | 1920×1080 @ HDMI | ✅ |

---

## ✅ 驱动状态

| 功能 | 状态 | 功能 | 状态 |
|:-----|:---:|:-----|:---:|
| **RX 6950 XT** | ⚠️ 需仿冒 | **Metal** | ✅ |
| **Realtek ALC897 声卡** | ✅ | **Realtek RTL8168 有线网卡** | ✅ |
| **USB 2.0/3.0** | ✅ | **SATA SSD** | ✅ |
| **HDMI 1920×1080** | ✅ | **睡眠/唤醒** | ✅ |
| **NVRAM** | ✅ | **Wi-Fi (Intel AX101)** | ⚠️ 需 OCLP |

> **注**：AMD RX 6950 XT (Navi 21) 在 macOS 中需通过 Device-id 仿冒为 RX 6900 XT 方可获得完整硬件加速支持。
> **Wi-Fi**：Intel AX101 需配合 OCLP (OpenCore Legacy Patcher) 打补丁启用。

---

## ⚙️ BIOS 设置

| 设置 | 值 | 说明 |
|:-----|:---:|:-----|
| **Secure Boot** | Disabled | macOS 不支持 |
| **Fast Boot** | Disabled | 避免启动问题 |
| **VT-x** | Enabled | 虚拟机支持 |
| **VT-d** | Disabled | 或添加 `dart=0` |
| **UEFI Boot** | Enabled | |
| **Above 4G Decoding** | Enabled | |
| **Resizable BAR** | Disabled | 兼容性考虑 |
| **SATA Mode** | AHCI | |

> 进入 BIOS 方法：开机按 Del

---

## 📦 EFI 配置

### Kexts 清单

> 完整 EFI 文件请从 [Releases](https://github.com/Sanqing678/Colorful-B860M-Arrow-Lake-Hackintosh/releases) 下载 v1.0.0 压缩包。

### SSDT 热补丁

> 完整 EFI 文件请从 [Releases](https://github.com/Sanqing678/Colorful-B860M-Arrow-Lake-Hackintosh/releases) 下载 v1.0.0 压缩包。

---

## 🚀 快速开始

### 1️⃣ BIOS 配置

1. 开机按 Del 进入 BIOS
2. 按上述表格配置
3. 保存退出

### 2️⃣ EFI 部署

```bash
diskutil list
sudo diskutil mount diskXs1
cp -R EFI /Volumes/EFI/
```

### 3️⃣ 生成三码（重要！）

使用 GenSMBIOS 或 OCAT 生成自己的 SMBIOS 序列号（建议 iMacPro1,1），不要直接使用本仓库的三码。

### 4️⃣ 安装 macOS Sequoia 15

1. 制作 macOS Sequoia 安装 U 盘
2. 替换 U 盘 EFI 分区中的 EFI 文件夹
3. 从 USB 启动 → 选择「Install macOS」
4. 按提示完成安装（约 2-3 次重启）

### 5️⃣ OCLP Wi-Fi 补丁

安装完成后，使用 **OpenCore Legacy Patcher** 对 Intel AX101 Wi-Fi 打补丁：

1. 下载 [OCLP](https://github.com/dortania/OpenCore-Legacy-Patcher)
2. 运行 → 点击 **Post-Install Root Patch**
3. 重启后 Wi-Fi 即可使用

---

## 🔧 注意事项

- **Arrow Lake-S (Ultra 7 265K)** 是最新架构，Hackintosh 兼容性仍在完善中
- **RX 6950 XT** (Navi 21) 需在 boot-args 中添加设备仿冒参数或通过 WhateverGreen 注入 Device-id
- **Intel AX101 Wi-Fi** 在 Sequoia 中无原生驱动，必须使用 **OCLP** 打补丁才能工作
- Realtek ALC897 声卡 layout-id 已配置
- 建议使用 **iMacPro1,1** SMBIOS
- ⚠️ **自行生成三码后再使用，不要直接使用本仓库的序列号**

---

## 📄 许可证

MIT License — 仅供学习和研究

> ⚠️ 在非 Apple 硬件上安装 macOS 可能违反 Apple EULA

---

<p align="center">
  <b>为 Hackintosh 社区贡献 ❤️</b><br/>
  <sub>七彩虹 B860M · OpenCore 1.0.x · macOS Sequoia 15</sub>
</p>
