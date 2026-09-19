# PhoneCam for Android and Windows

[简体中文](README.md) · English

Turn your Android phone into a webcam for a Windows PC over USB or Wi-Fi. PhoneCam is free and open-source software licensed under the MIT License.

[![GitHub Release](https://img.shields.io/github/v/release/Naokoisme/phonecam?style=flat-square)](https://github.com/Naokoisme/phonecam/releases/latest)
[![License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](LICENSE)

## Download

PhoneCam supports **Windows 10/11 (x64)** and **Android 7.0 or later**. The Windows and Android apps work together. The current release is **v2.0.3**.

| Install on | Download |
|---|---|
| Windows PC | [PhoneCam for Windows v2.0.3](https://github.com/Naokoisme/phonecam/releases/download/v2.0.3/PhoneCam-Windows-v2.0.3.exe) |
| Android phone | [PhoneCam for Android v2.0.3](https://github.com/Naokoisme/phonecam/releases/download/v2.0.3/PhoneCam-Android-v2.0.3.apk) |

The Windows installer includes a tool that can install the companion Android app. You only need to download the APK separately when installing it manually.

[Release notes](docs/releases/v2.0.3.md) · [All releases](https://github.com/Naokoisme/phonecam/releases)

## Quick start

1. **Install the Windows app.** Run the Windows installer. For USB mode, select **Enable USB connection** when prompted so the setup tool can prepare the required Android platform tools.
2. **Install the Android app.** Install the APK on your phone, or open **PhoneCam USB and Android Setup** from the Windows Start menu and choose the install/repair option. Allow camera access when Android asks.
3. **Connect the devices.** Open PhoneCam on both devices and tap the streaming button on the phone. When the preview appears on the PC, select **PhoneCam Camera** in your video application.

- **USB:** Connect the phone with a data-capable USB cable, enable Android USB debugging, and approve the computer on the phone.
- **Wi-Fi:** Connect the phone and PC to the same local network.

## Compatibility and limitations

- PhoneCam currently sends video only. Use the PC's built-in microphone or an external microphone for audio.
- Video output has been tested with Tencent Meeting. Other applications that accept a Windows virtual camera may work, but Zoom, OBS Studio, DingTalk, WeChat, and other applications have not yet been tested individually.
- Windows installation requires administrator privileges.
- Older test builds may cause an Android signing conflict. The repair tool explains the affected Android user or profile before offering removal. Removing an old build deletes that app's data.

See the [English FAQ](docs/faq.en.md), [Chinese user manual](docs/user-manual.md), and [known issues](docs/known-issues.md) for more information.

## Help and feedback

If PhoneCam cannot connect, shows no video, or you have a suggestion, [open an issue](https://github.com/Naokoisme/phonecam/issues). Include your phone model, Android version, Windows version, connection type, and the step where the problem occurred.

You can also email [23lqhu@stu.edu.cn](mailto:23lqhu@stu.edu.cn). PhoneCam is a personally maintained open-source project, and real-world compatibility reports are especially helpful.

## Development

[Build guide](docs/development.md) · [Architecture](docs/current-architecture.md) · [Protocol](docs/protocol.md) · [MIT License](LICENSE)
