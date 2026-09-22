# GGEA 下载与发布

GGEA 是《SD高达G世纪 永恒》的 Windows 桌面辅助工具。本仓库用于分发已完成自动检查和人工验证的 Release 版本；程序源码不在此仓库中。

## 下载

前往 [Releases](https://github.com/GundamCC/GGEA-Release/releases)，在所需版本的 **Assets** 中下载 `GGEA-*.zip` 和同名的 `.zip.sha256`。GitHub 自动提供的 **Source code (zip/tar.gz)** 只是本分发仓库的文件，不能运行。

将 ZIP **完整解压**后启动 `GGEA.exe`。不要单独提取 EXE；程序还需要包内的 `config/`、`resources/`、`billing-runtime/` 和原生 DLL。完整包适用于 Windows 10/11 x64，不要求用户另装 .NET SDK、Python、NDK 或 JDK；需要 Android 模拟器和可用的 ADB。自动化画面要求 1920×1080 横屏。

首次运行请阅读包内 `使用说明.txt` 和 `RELEASE.txt`，先确认设备与截图，再在有人看护的情况下逐项启用任务。出现识别失败、错位或意外弹窗时应立即停止。不承诺无人值守或未经验证的模拟器、Android、游戏版本和语言环境兼容。

## 校验下载

在 PowerShell 中对下载的 ZIP 运行：

```powershell
(Get-FileHash -Algorithm SHA256 -LiteralPath '.\GGEA-v0.9.4.1-win-x64.zip').Hash.ToLowerInvariant()
```

结果应与同名 `.zip.sha256` 文件第一列完全相同。SHA-256 用于检查文件完整性，不能代替数字签名。包内 `build-info.json` 记录构建使用的完整源码提交、版本、构建参数及逐文件摘要；每次发布的说明也会列出对应提交。构建时的本地包名包含提交短号，GitHub Release 附件使用简洁版本名；两者的 ZIP 内容与摘要必须相同。

## 反馈

可在本仓库的 [Issues](https://github.com/GundamCC/GGEA-Release/issues) 报告下载、解压和运行问题。提供版本、系统环境、复现步骤及已脱敏的日志片段；请勿公开账号信息、Token、完整私人截图或未经脱敏的日志。

第三方组件许可文件随完整发布包提供于 `billing-runtime/licenses/`。
