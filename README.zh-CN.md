# CANmeleon PCAN Pro FD 兼容固件 — PCAN-View 与 PCAN-Basic

[English](README.md) · [简体中文](README.zh-CN.md)

CANmeleon PCAN Pro FD 固件让适用的 CANmeleon USB-CAN/CAN FD 硬件在 Windows 上接入 PCAN-View 与 PCAN-Basic。本仓库提供固件能力、硬件要求及安装说明。

[固件特性与性能参数](#固件特性与性能参数) · [下载与安装](#下载与安装) · [支持设备](https://canmeleon.com/zh/firmware/devices/) · [固件总览](https://github.com/CANmeleon/canmeleon-usb-can-firmware)

## 支持硬件

在 [CANmeleon 设备目录](https://canmeleon.com/zh/firmware/devices/)选择支持 **PCAN Pro FD** 的硬件。按所选模式配备 2 路物理 CAN 接口及对应授权。连接[设备管理器](https://github.com/CANmeleon/canmeleon-device-manager)核对完整型号及可安装固件。

以下参数适用于 **PCAN Pro FD 模式**，不作为 PCAN-USB 经典 CAN 或其他通道模式的参数。

<!-- firmware-parameters:start -->
## 固件特性与性能参数

PCAN Pro FD 模式；需配套具备 2 路 CAN 接口及对应模式授权的设备。

### 通信能力

| 参数 | 能力 / 数值 | 备注 |
| --- | --- | --- |
| CAN 通道 | 支持 2 路 CAN / CAN FD | 每通道支持发送和接收。 |
| 报文格式 | 11 / 29 位 ID；Classic CAN 0–8 B，CAN FD 最高 64 B | 支持 Classic RTR；CAN FD 支持 BRS 开启 / 关闭。 |
| Classic CAN 速率 | 最高 1 Mbit/s | 通过上位机设置总线速率。 |
| CAN FD 数据速率 | 最高 12 Mbit/s | 仲裁段与数据段独立配置；需配套支持相应速率的收发器和总线布线。 |

### 时间戳

| 参数 | 能力 / 数值 | 备注 |
| --- | --- | --- |
| 接收硬件时间戳 | 支持 | 通过 PCAN-Basic 接收接口读取报文时间戳。 |
| 发送完成硬件时间戳 | 支持 | 开启 PCAN_ALLOW_ECHO_FRAMES 后，从发送回显读取时间戳。 |
| 时间戳分辨率（PCAN-Basic） | 1 µs | 接收报文和发送完成回显的时间戳均以 1 µs 为步进。 |

### 典型通信性能

| 参数 | 能力 / 数值 | 备注 |
| --- | --- | --- |
| 64 字节报文传输帧率（短时） | 约 7,600 帧/秒 | CAN FD，启用 BRS；1 Mbit/s 仲裁 / 8 Mbit/s 数据；单条总线、请求与应答双向合计。 |
| 0 字节报文单向传输帧率 | 约 20,800 帧/秒 | PCAN-Basic；CAN FD 标准帧，启用 BRS；1 Mbit/s 仲裁 / 8 Mbit/s 数据；单条总线、单向。 |
| 8 字节报文单向传输帧率 | 约 19,300 帧/秒 | PCAN-Basic；CAN FD 标准帧，启用 BRS；1 Mbit/s 仲裁 / 8 Mbit/s 数据；单条总线、单向。 |
| 64 字节报文单向传输帧率 | 约 10,100 帧/秒 | PCAN-Basic；CAN FD 标准帧，启用 BRS；1 Mbit/s 仲裁 / 8 Mbit/s 数据；单条总线、单向。 |
| 64 字节报文单向有效数据吞吐 | 约 5.17 Mbit/s | PCAN-Basic；CAN FD 标准帧，启用 BRS；1 Mbit/s 仲裁 / 8 Mbit/s 数据；单条总线、单向。仅计算报文数据字段。 |

### 软件配套

| 参数 | 能力 / 数值 | 备注 |
| --- | --- | --- |
| 配套软件 | 支持 PCAN-View | 安装 PEAK PCAN 驱动。 |
| 开发接口 | 支持 Windows / PCAN-Basic | 用于 CAN / CAN FD 应用开发。 |

<!-- firmware-parameters:end -->

## 下载与安装

1. 安装 [Windows x64 设备管理器](https://canmeleon.com/zh/device-manager/#downloads)，连接设备并检查适用固件。
2. 从固件目录选择适用包，或从 [GitHub 固件 Releases](https://github.com/CANmeleon/canmeleon-usb-can-firmware/releases)下载完整包并使用“导入固件 ZIP”。已有下载渠道见 [Gitee Releases](https://gitee.com/sysmax/kpcfg4-canmeleon/releases)。按所选版本说明核对设备及管理器要求。
3. 选择 **PCAN Pro FD**，检查空间和待执行变更，确认安装；保持 USB 连接和供电稳定直至写入完成。
4. 重新连接并切换到所安装的固件，等待 USB 重新识别。
5. 安装 PEAK PCAN 驱动，选择 PCAN-USB Pro FD，在 PCAN-View 或 PCAN-Basic 中配置 CAN FD 仲裁段与数据段速率。 参阅[驱动下载页](https://www.peak-system.com/support/downloads/drivers/driver-packages/)及 [PCAN Pro FD 配置指南](https://canmeleon.com/zh/firmware/pcanfd/)。
6. 按总线配置设置各通道，确认能够正常发送和接收报文。

[固件管理](https://canmeleon.com/zh/device-manager/firmware-management/) · [更新与恢复](https://canmeleon.com/zh/device-manager/updates-and-recovery/)

## 常见问题

**固件安装到什么硬件？** 安装于设备目录和管理器列出的适用 CANmeleon 硬件。模式名称表示软件接口；第三方原厂硬件的升级固件由对应厂商提供。

**切换固件能增加物理通道吗？** 通道数由硬件和所选模式决定。四通道模式需要四路物理 CAN 接口及对应授权。

**性能数据适用于所有工况吗？** 按各行的速率、帧长、方向、模式和短时限定使用。可配置的数据段速率与典型报文吞吐是不同指标。

**固件源码在哪里？** 本仓库提供文档、参数数据和二进制下载入口，许可信息以对应组件或发布包为准。

## 问题与新需求反馈

固件相关的问题和新需求可在 [GitHub 固件主仓库提 Issue](https://github.com/CANmeleon/canmeleon-usb-can-firmware/issues)。请附设备型号、当前模式、固件与驱动版本、软件/API、总线配置及复现步骤。

[PCAN Pro FD 参数表](docs/parameters/pcanfd-pro-fd.zh-CN.md) · [参数 JSON](docs/parameters/pcanfd-pro-fd.json) · [设备管理器问题](https://github.com/CANmeleon/canmeleon-device-manager/issues)
