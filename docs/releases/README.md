# PhoneCam 版本发布说明

本目录存放 PhoneCam 各版本的用户发布说明（Release Notes）。
发布工作流（`.github/workflows/windows-release.yml`）会在构建前检查并自动读取对应版本的说明文件（`docs/releases/v<版本号>.md`），直接通过 `--notes-file` 作为 GitHub Release 的发布正文。

## 版本列表

- [v2.0.3 (当前版本)](v2.0.3.md) — 修复 USB 连接组件下载失败、新增手机端安装/修复功能。

## 编写规范

- **面向普通用户**：以通俗中文为主，简洁清晰，避免堆砌底层代码或架构术语。
- **正文链接规范**：由于 GitHub Release 正文直接展示在发布页面，**所有文档和仓库链接必须使用绝对 URL**（如 `https://github.com/Naokoisme/phonecam/blob/master/docs/...`），避免相对路径在发布页上下文解析错误。
- **免去重复 H1 标题**：Release 页面已有版本标题，正文直接从一句话简介开始。
- **直接下载直链在前**：简介后立即提供 Windows 与 Android 安装文件的直链下载表格与简短说明。
- **突出可感知改进**：仅列出普通用户真正可感知的实际改动（2-3 项）与真实使用须知，不作夸大承诺。
- **提供反馈渠道**：保留公开邮箱与 GitHub Issues 链接。
