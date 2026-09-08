# PhoneCam 开发者指南

本文档面向希望参与 PhoneCam 开发、编译或调试的贡献者。

---

## 1. 仓库结构与架构入口

PhoneCam 采用模块化设计，核心代码划分为以下部分：

- `cpp/`：Windows 客户端桌面应用、DirectShow 虚拟摄像头驱动（`phonecam-virtualcam.dll`）以及 USB/ADB 自动配置工具（`phonecam-adb-setup.exe`）。基于 CMake（>= 3.25）、C++20、Qt 6 及 DirectShow。
- `phone_native/`：Android 原生客户端（`com.phonecam.nativeapp`）。基于 Kotlin、Camera2 API、MediaCodec（H.264 硬编）与前台推流 Service，目标环境为 compileSdk 34、minSdk 24。
- `installer/`：Windows 端 Inno Setup 安装包制作脚本及运行时依赖分发与校验工具（`prepare-dist.ps1`、`phonecam.iss`）。

### 核心文档索引

- [系统架构设计](current-architecture.md)：DirectShow 虚拟摄像头注册、共享内存与前后端协作架构。
- [PCP 传输协议](protocol.md)：PhoneCam 数据包头结构、H.264 NAL 传输与 UDP 设备发现协议。
- [用户使用手册](user-manual.md)：用户端安装使用与故障排查说明。
- [发布与排障门禁](release-troubleshooting.md)：正式签名要求、证书指纹基线与发布排障规范。

---

## 2. 本地开发与调试构建

新贡献者在本地进行功能开发、修复 bug 或体验构建时，**完全不需要配置任何维护者私钥或签名证书**。

### 2.1 Windows 端开发构建

#### 环境要求
- 操作系统：Windows 10/11 64 位
- 编译器：Visual Studio 2022（需勾选“使用 C++ 的桌面开发”工作负荷）
- 构建工具：CMake（>= 3.25）、Ninja
- 包管理器：vcpkg（需设置环境变量 `VCPKG_ROOT`，例如 `C:\vcpkg` 或 `D:\vcpkg`）

#### 本地构建步骤
```powershell
# 1. 进入 cpp 目录
cd cpp

# 2. 执行构建脚本（或直接使用 CMake / Visual Studio 打开工程进行调试）
.\build_release.bat
```
构建生成的二进制文件位于 `cpp\build_release\` 目录。

### 2.2 Android 端本地调试构建

#### 环境要求
- JDK：JDK 17
- Android SDK：compileSdk 34、minSdk 24
- 推荐使用 Android Studio 打开 `phone_native` 目录

#### JDK 17 路径配置说明
仓库 `phone_native/gradle.properties` 中默认配置了维护者环境的 JDK 路径（`org.gradle.java.home=C:\\Program Files\\Microsoft\\jdk-17.0.11.9-hotspot`）。贡献者若使用自己机器上的 JDK 17，**无需修改仓库中的配置文件**，只需在执行 Gradle 命令时通过命令行参数覆盖：

```powershell
cd phone_native
.\gradlew.bat assembleDebug "-Dorg.gradle.java.home=你的JDK17安装路径"
```
若使用 Android Studio，也可在 IDE 的 `Settings -> Build, Execution, Deployment -> Build Tools -> Gradle` 中直接选择本地 JDK 17。

#### 本地调试包生成物
构建生成的 APK 位于：
`phone_native/app/build/outputs/apk/debug/app-debug.apk`

#### 调试密钥与正式签名的区别
Debug 构建使用开发工具自动生成的本地调试密钥（Debug Keystore）签名，无需设置维护者专用的 `PHONECAM_*` 环境变量。

本地调试密钥与正式发布证书不同，同包名的 Debug APK 无法直接覆盖正式版。建议使用独立测试设备；卸载已有版本会删除该应用的数据。

---

## 3. 维护者正式发布与签名门禁

正式发布需要核对安装包来源、文件哈希和签名连续性。普通贡献者提交 PR 时无需运行此流程。

### 3.1 Windows 正式安装包
- 正式安装包通过 GitHub Actions 工作流（`.github/workflows/windows-release.yml`）在推送版本 Tag（如 `v2.0.3`）时自动在纯净 CI 环境中构建。
- 构建包含依赖预处理脚本 `installer/prepare-dist.ps1`，强制核验 DLL、Schannel TLS 后端与配套 APK 的哈希及数字签名，最后由 Inno Setup 输出可执行安装包。

### 3.2 Android 正式 Release 签名
- 正式 APK 必须使用维护者专属 keystore 进行签名，以维持版本升级指纹的一致性。
- 构建正式 APK 时需要设置以下四个环境变量：
  - `PHONECAM_STORE_FILE`（keystore 文件路径）
  - `PHONECAM_STORE_PASSWORD`（keystore 密码）
  - `PHONECAM_KEY_ALIAS`（密钥别名）
  - `PHONECAM_KEY_PASSWORD`（密钥密码）
- 维护者执行构建与签名核验：
  ```powershell
  powershell -NoProfile -ExecutionPolicy Bypass -File .\phone_native\build-signed-apk.ps1
  ```
- 脚本会调用 `verify-release-apk.ps1` 对输出的 Release APK 执行 `apksigner` 门禁，验证证书 SHA-256 与 `phone_native/release-signing-baseline.json` 基线完全一致。
- 详细门禁要求与发布故障处理请参见 [发布与排障门禁](release-troubleshooting.md)。

### 3.3 版本命名与组件版本解耦
- 公开发布的安装包统一采用发布版本命名：`PhoneCam-Windows-v<APP_VERSION>.exe` 与 `PhoneCam-Android-v<APP_VERSION>.apk`。
- 发布版本与组件内部版本可独立（例如当前发布套装为 v2.0.3，而配套 Android APK 内部版本仍为 0.2.9）；外部文件名改动不改签名与内容，在保证升级指纹连续性的同时为用户提供直观一致的套装体验。

---

## 4. 贡献规范与协议

- 遵循 KISS / YAGNI 原则，提交最小且必要的改动。
- 保持文档与实现一致，不扩大未经验证的兼容性承诺。
- 本项目遵循 [MIT 开源许可证](../LICENSE)。
