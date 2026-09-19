# PhoneCam FAQ

This page answers common questions about **PhoneCam for Android and Windows**, an open-source tool that turns an Android phone into a Windows webcam over USB or Wi-Fi.

## What devices does PhoneCam support?

- A Windows 10 or Windows 11 PC with a 64-bit processor
- An Android phone running Android 7.0 or later

PhoneCam does not currently provide clients for iPhone, macOS, or Linux.

## Does PhoneCam work over USB and Wi-Fi?

Yes. USB mode uses Android USB debugging and is normally the more stable option. Wi-Fi mode requires the phone and PC to be on the same local network. Public or corporate Wi-Fi may prevent devices from communicating with each other.

## Why does USB mode require USB debugging?

PhoneCam uses Android Debug Bridge (ADB) port forwarding for its USB connection. The phone asks you to approve the connected computer the first time it is used.

## Does PhoneCam transmit audio?

No. The current version transmits video only. Use the PC's built-in microphone, a headset, or another external microphone for audio.

## Which Windows applications are supported?

PhoneCam creates a Windows virtual camera named **PhoneCam Camera**. Video output has been tested with Tencent Meeting. Applications that accept a Windows virtual camera may also work, but Zoom, OBS Studio, DingTalk, WeChat, and other applications have not yet been tested individually.

If you successfully use PhoneCam with another application, please share the application name and version in an issue.

## Why can the PC not find my phone in USB mode?

Check the following:

1. Use a USB cable that supports data transfer, not a charging-only cable.
2. Enable USB debugging in Android developer options.
3. Approve the computer when the authorization prompt appears on the phone.
4. Reconnect the cable and refresh the device list in PhoneCam.

## Why can the PC not find my phone over Wi-Fi?

Make sure both devices are on the same local network. Some public, university, and corporate networks isolate connected devices. If discovery fails, try manual connection with the address shown by the Android app, use a phone hotspot, or switch to USB mode.

## Why does Windows warn that it cannot verify the publisher?

The current Windows installer uses a self-signed certificate instead of a commercial code-signing certificate. The source code is public in this repository. Only download installers from the official [PhoneCam releases](https://github.com/Naokoisme/phonecam/releases).

## Why does Android report a signing conflict during an update?

An older test build may still be installed in an Android secondary user, cloned-app space, or work profile. The Windows repair tool can identify the affected profile and offers a separate confirmation before removal.

Removing the old package deletes its app data from all affected Android users or profiles. Cancel the operation if you need to preserve that data, and remove the old app manually from the relevant profile instead.

## How do I uninstall PhoneCam?

- **Windows:** Open Windows Settings, go to Apps, select PhoneCam, and choose Uninstall.
- **Android:** Long-press the PhoneCam app icon and choose Uninstall, or remove it from Android Settings.

## How do I report a problem?

[Open a GitHub issue](https://github.com/Naokoisme/phonecam/issues) and include:

1. Phone model and Android version
2. Windows version
3. USB or Wi-Fi connection
4. The step that failed
5. Exported PhoneCam logs, if you choose to share them

Do not publish logs before checking whether they contain information you consider private.
