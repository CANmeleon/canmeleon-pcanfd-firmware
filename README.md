# CANmeleon PCAN Pro FD-Compatible Firmware — PCAN-View and PCAN-Basic

[English](README.md) · [简体中文](README.zh-CN.md)

CANmeleon PCAN FD-compatible firmware connects supported USB-CAN/CAN FD hardware to PCAN-View and PCAN-Basic on Windows. This guide focuses on two-channel PCAN Pro FD mode, with hardware requirements, CAN/CAN FD parameters, firmware downloads and driver setup.

[Features and performance](#features-and-performance) · [Download and install](#download-and-install) · [Supported devices](https://canmeleon.com/en/firmware/devices/) · [Firmware catalog](https://github.com/CANmeleon/canmeleon-usb-can-firmware)

## When to choose PCAN FD firmware

- View and send CAN/CAN FD frames in PCAN-View.
- Build a Windows CAN/CAN FD application with PCAN-Basic.
- Choose PCAN Pro FD for a supported two-channel device. Compare [other PCAN FD modes](https://github.com/CANmeleon/canmeleon-usb-can-firmware/blob/main/docs/parameters/README.md) when your project requires a different channel count.

## Supported hardware

Choose a device listed for **PCAN Pro FD** in the [CANmeleon device catalog](https://canmeleon.com/en/firmware/devices/). This mode requires 2 physical CAN channels as applicable, and a license for the selected mode. Connect the device in [CANmeleon Device Manager](https://github.com/CANmeleon/canmeleon-device-manager) to check its exact model and available firmware.

The parameter table below applies to **PCAN Pro FD mode**. Select the matching firmware mode; the figures do not describe PCAN-USB Classic CAN or other channel modes.

<!-- firmware-parameters:start -->
## Features and performance

PCAN Pro FD mode; requires a device with 2 CAN interfaces and a license for this mode.

### Communication capabilities

| Parameter | Capability / value | Notes |
| --- | --- | --- |
| CAN channels | 2 CAN / CAN FD channels supported | Each channel supports transmission and reception. |
| Frame formats | 11 / 29-bit IDs; Classic CAN 0–8 B, CAN FD up to 64 B | Classic RTR supported; CAN FD supports BRS enabled or disabled. |
| Classic CAN bit rate | Up to 1 Mbit/s | Configure the bus bit rate in the host software. |
| CAN FD data-phase bit rate | Up to 12 Mbit/s | Configure arbitration and data phases independently; use transceivers and bus wiring suitable for the selected rates. |

### Timestamps

| Parameter | Capability / value | Notes |
| --- | --- | --- |
| Hardware receive timestamps | Supported | Read frame timestamps through the PCAN-Basic receive API. |
| Hardware transmit-completion timestamps | Supported | Enable PCAN_ALLOW_ECHO_FRAMES to read timestamps from transmit echo frames. |
| Timestamp resolution (PCAN-Basic) | 1 µs | Received frames and transmit-completion echo frames both have timestamps in 1 µs steps. |

### Typical communication performance

| Parameter | Capability / value | Notes |
| --- | --- | --- |
| 64-byte frame rate (short-duration) | approximately 7,600 frames/s | CAN FD with BRS; 1 Mbit/s arbitration / 8 Mbit/s data; one bus, combined request and response traffic in both directions. |
| 0-byte frame rate, one direction | approximately 20,800 frames/s | PCAN-Basic; standard-ID CAN FD frames with BRS; 1 Mbit/s arbitration / 8 Mbit/s data; one bus, one direction. |
| 8-byte frame rate, one direction | approximately 19,300 frames/s | PCAN-Basic; standard-ID CAN FD frames with BRS; 1 Mbit/s arbitration / 8 Mbit/s data; one bus, one direction. |
| 64-byte frame rate, one direction | approximately 10,100 frames/s | PCAN-Basic; standard-ID CAN FD frames with BRS; 1 Mbit/s arbitration / 8 Mbit/s data; one bus, one direction. |
| 64-byte frame payload throughput, one direction | approximately 5.17 Mbit/s | PCAN-Basic; standard-ID CAN FD frames with BRS; 1 Mbit/s arbitration / 8 Mbit/s data; one bus, one direction. Counts only frame data fields. |

### Software and APIs

| Parameter | Capability / value | Notes |
| --- | --- | --- |
| Software | PCAN-View supported | Install the PEAK PCAN driver. |
| Development API | Windows / PCAN-Basic supported | For developing CAN / CAN FD applications. |

<!-- firmware-parameters:end -->

## Download and install

1. Install [CANmeleon Device Manager for Windows x64](https://canmeleon.com/en/device-manager/#downloads), connect the device and check the available firmware.
2. Choose an applicable package in **Firmware Catalog**, or download a complete package from the [GitHub firmware Releases](https://github.com/CANmeleon/canmeleon-usb-can-firmware/releases) and use **Import firmware ZIP**. [Gitee releases](https://gitee.com/sysmax/kpcfg4-canmeleon/releases) provide the existing download channel. Follow the chosen release's device and manager requirements.
3. Select **PCAN Pro FD**, review storage and pending changes, and confirm installation. Keep the USB connection and power stable until writing finishes.
4. Reconnect and switch to the installed firmware. Wait for USB re-enumeration.
5. Install the PEAK PCAN driver, select PCAN-USB Pro FD, and configure the CAN FD arbitration and data bit rates in PCAN-View or PCAN-Basic. Use the [driver download page](https://www.peak-system.com/support/downloads/drivers/driver-packages/) and the [PCAN Pro FD setup guide](https://canmeleon.com/en/firmware/pcanfd/).
6. Configure each channel for your bus, then verify frame transmission and reception.

[Firmware management](https://canmeleon.com/en/device-manager/firmware-management/) · [Updates and recovery](https://canmeleon.com/en/device-manager/updates-and-recovery/)

## Frequently asked questions

**Which hardware receives this firmware?** Install it on compatible CANmeleon devices selected through the catalog and Device Manager. The mode name identifies the software interface; firmware updates for third-party-manufactured devices come from their manufacturers.

**Which PCAN mode do these parameters describe?** The tables describe two-channel PCAN Pro FD mode. Select PCAN-USB Pro FD in the host software; use the firmware catalog for other PCAN modes.

**How do I read the performance table?** Match the bus rates, frame length, direction and mode to your workload. Configurable bit rate describes the bus setting; frame throughput describes transmitted or received frames per second.

**Where is the source code?** This repository contains documentation, parameter data and binary-download links. Refer to the component or release for its license.

## Feedback and related resources

Firmware problems and new feature requests can be submitted as [Issues in the CANmeleon firmware main repository](https://github.com/CANmeleon/canmeleon-usb-can-firmware/issues). Include the device model, active mode, firmware and driver versions, software/API, bus configuration and steps to reproduce.

[PCAN Pro FD parameter table](docs/parameters/pcanfd-pro-fd.md) · [Parameter JSON (Chinese)](docs/parameters/pcanfd-pro-fd.json) · [Device Manager issues](https://github.com/CANmeleon/canmeleon-device-manager/issues)

## Ecosystem participation and commercial services

CANmeleon works with hardware makers, chip vendors and developers. For software/firmware integration, CANmeleon firmware porting and maintenance on your chip platform, or custom firmware development, contact [len2slaw@foxmail.com](mailto:len2slaw@foxmail.com). Include your board/MCU, target API, required features and schedule.

[Open-source hardware and free adaptation program](https://github.com/CANmeleon#open-source-development-and-free-firmware-adaptations) · [Request an open-source board adaptation](https://github.com/CANmeleon/canmeleon-usb-can-firmware/issues/new?template=open_hardware_adaptation.md)
