# NUC8ixBEx-Hackintosh-macOS26
本 EFI 适用于 NUC8i3BEK、NUC8i3BEH、NUC8i5BEK、NUC8i5BEH、NUC8i7BEK、NUC8i7BEH 的白苹果网卡设备，网卡首推 BCM94360CS2 和 BCM943602CS，支持以下两种白果网卡情况：
1. 通过硬改主板读卡器 IC 芯片加装白苹果无线网卡。
2. 使用 Nvme M.2 接口转接卡使用白苹果无线网卡。

## 当前版本（Version）
* OpenCore：1.0.7
* 当前引导支持系统：macOS 26 Tahoe
* ⚠️注意：升级 EFI 版本建议使用 Hackintool 或进入 OC 启动菜单执行 Reset Nvram（Reset NVRAM 为隐藏功能，可在 OpenCore 引导界面敲击一下空格，即可出现）

## 配置（Specification）
- **Motherboard**: NUC8BEH
- **Simulation model**: iMac 2020
- **Processor**: Intel Core Intel i3-8109U/i5-8259U/i7-8559U
- **IGPU**: Intel Iris Plus 655 (独立显存 128MB + 共享显存 1536MB)
- **Wi-Fi/Bluetooth**: BCM94360CS2 or BCM943602CS
- **Ethernet**: Intel I219-V
- **Audio**: Realtek ALC235

## 工作情况（Work Situation）
- DP/HDMI 4K 60hz 视频输出+音频输出（可双屏 4K 60hHz）
- 全部 USB3 / USB2 接口驱动
- 雷电3（支持 DP 1.2、USB 3.1 Gen2、雷雳3 40GB/s、仅雷电协议不支持热插拔、PD 供电仅支持 15W 输出不支持输入、支持 5K 雷雳显示器）
- Nvme SSD（PCIe x 4）
- 2.5 寸 SATA
- 3.5mm 耳机孔（开关机有爆音问题）
- 有线网卡
- 无线 Wi-Fi（2.4GHz 会和蓝牙干扰，建议只用5GHz）
- 蓝牙（键鼠、妙控板、耳机、音箱）
- App Store / iCloud
- 自动休眠
- 深睡键鼠唤醒（有线/无线/蓝牙键鼠均可）
- 蓝牙键鼠操作 BIOS，以及 OpenCore 下的功能选择
- Airdrop 隔空投送
- Continuity 接力
- Apple Watch 解锁
- AirPlay 隔空播放
- Sidecar 随航

## BIOS 设置（BIOS Settings）
豆子峡谷（NUC8ixBEx）开机时，连续点按 F2 进入 BIOS，为了避免之前有其他不合适的改动，建议先按 F9 重置 BIOS 默认设置，BIOS 内的选项启用为勾选，禁用为不勾选。

- Boot->Boot Priority->Legacy Boot Priority-> « Legacy Boot » ：禁用
- Boot->Boot Configuration->UEFI Boot->« Fast Boot »： 禁用
- UEFI Boot->« Boot USB Devices First » ： 启用
- UEFI Boot->« Boot Network Devices Last » ：启用
- Boot Devices->«Network Boot» ：设置为 « Disable »
- Boot->Secure Boot-> « Secure Boot » ：禁用
- Security->Security Features-> « Inter VT for directed I/VO (VT-d) » ： 禁用
- Power->Secondary Power Settings-> « Wake on LAN from S4/S5 » ： 设置为 « Stay Off »
- Devices->Onboard Devices-> « WLAN » 和 « Bluetooth » ：禁用


## 使用教程 (Using Tutorials)
1. 使用本 EFI 进行 macOS 系统的安装。
2. 安装系统进入桌面后，下载 [OCLP-Mod](https://github.com/laobamac/OCLP-Mod/releases) 进行驱动的安装（博通网卡驱动补丁及音频补丁）。
3. 如需登陆 Apple ID，请手动摇三码放到 EFI/OC 的 config.plist 文件对应位置。
4. 清空并重新排序网络设备，以便顺利使用 Apple ID 登录 App Store 及系统各项云服务，命令：sudo rm -rf /Library/Preferences/SystemConfiguration/NetworkInterfaces.plist*
5. 开启任意来源，命令：sudo spctl --master-disable

## 更新日志（Change Log）

### 2026-05-09，本次更新内容：
1. 基于 OpenCore 1.0.7 正式版进行制作
2. 支持 macOS 26.0 到 macOS 26.4.1 正式版
3. Kexts 驱动信息
	- AMFIPass（v1.4.1）
	- AppleALC（v1.9.7）
	- BlueToolFixup（v2.7.1）
	- CPUFriend（v1.3.0）
	- FeatureUnlock（v1.1.8）
	- IntelMausi（v1.0.8）
	- IO80211FamilyLegacy（v1200.12.2b1）
	- IOSkywalkFamily（v1.2.0）
	- Lilu（v1.7.2）
	- RestrictEvents（v1.1.6）
	- VirtualSMC（v1.3.7）
	- WhateverGreen（v1.7.0）
