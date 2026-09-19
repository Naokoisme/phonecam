# PhoneCam for Android and Windows

简体中文 · [English](README.en.md)

把 Android 手机变成 Windows 电脑的摄像头，支持 USB 数据线和 Wi-Fi 连接。免费开源。

Turn your Android phone into a USB or Wi-Fi webcam for Windows. Free and open source.

[![GitHub Release](https://img.shields.io/github/v/release/Naokoisme/phonecam?style=flat-square)](https://github.com/Naokoisme/phonecam/releases/latest)
[![License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](LICENSE)

## 下载

支持 **Windows 10/11（x64）** 和 **Android 7.0 及以上**。两端配套使用，当前发布版本为 **v2.0.3**。

| 安装到哪里 | 下载 |
|---|---|
| Windows 电脑 | [下载电脑端 v2.0.3](https://github.com/Naokoisme/phonecam/releases/download/v2.0.3/PhoneCam-Windows-v2.0.3.exe) |
| Android 手机 | [下载手机端 v2.0.3](https://github.com/Naokoisme/phonecam/releases/download/v2.0.3/PhoneCam-Android-v2.0.3.apk) |

电脑安装包带有手机端安装工具。通过电脑向导装好手机端后，无需重复下载 APK；使用 Wi-Fi 时也可以在手机上手动安装。

[查看本版更新](docs/releases/v2.0.3.md) · [历史版本](https://github.com/Naokoisme/phonecam/releases)

## 快速开始

1. **安装电脑端。** 运行下载的 Windows 安装包。使用 USB 时，勾选“启用 USB 连接”，按向导提示准备连接组件。
2. **安装手机端。** 在手机上安装 APK，或通过 Windows 开始菜单中的“PhoneCam USB 与手机端设置”→“安装/修复手机端”安装。打开手机 App，允许使用摄像头。
3. **连接并显示画面。** 打开电脑和手机上的 PhoneCam，在手机端点击“开始推流”。电脑出现预览后，在会议软件的摄像头设置中选择 **PhoneCam Camera**。

- **USB 连接：** 使用数据线连接，开启手机的“USB 调试”，并在手机上允许电脑连接。
- **Wi-Fi 连接：** 手机和电脑连接同一局域网。

[查看完整安装与连接教程](docs/user-manual.md)

## 使用须知

- 当前仅传输视频，声音请使用电脑内置或外接麦克风。
- 已在腾讯会议验证出画面。其他软件和机型的兼容情况欢迎反馈；横屏显示占位图等限制见[已知问题](docs/known-issues.md)。
- Windows 安装需要管理员权限。旧测试版若发生手机端签名冲突，修复向导会提示是否卸载旧版；**确认卸载会删除旧应用数据**。

## 帮助与反馈

连接不上、没有画面或有使用建议，可先查看[用户手册](docs/user-manual.md)或[English FAQ](docs/faq.en.md)，也可以[提交 Issue](https://github.com/Naokoisme/phonecam/issues)或发邮件到 [23lqhu@stu.edu.cn](mailto:23lqhu@stu.edu.cn)。

请告诉我手机型号、Windows 版本，以及卡在哪一步。电脑端的“导出日志”可帮助排查，日志可由你选择附上。

PhoneCam 是个人维护的 vibe coding 开源项目，感谢每一份实际使用反馈。

## 参与开发

[开发与构建指南](docs/development.md) · [系统架构](docs/current-architecture.md) · [传输协议](docs/protocol.md) · [MIT 许可证](LICENSE)
