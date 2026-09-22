# GGEA 下载与发布

GGEA 是《SD高达G世纪 永恒》的 Windows 桌面辅助工具。本仓库用于分发已完成自动检查和人工验证的 Release 版本；程序源码不在此仓库中。

## 下载

前往 [Releases](https://github.com/GundamCC/GGEA-Release/releases)，在所需版本的 **Assets** 中下载 `GGEA-*.zip` 和同名的 `.zip.sha256`。GitHub 自动提供的 **Source code (zip/tar.gz)** 只是本分发仓库的文件，不能运行。

将 ZIP **完整解压**后启动 `GGEA.exe`。不要单独提取 EXE；程序还需要包内的 `config/`、`resources/`、`billing-runtime/` 和原生 DLL。完整包适用于 Windows 10/11 x64，不要求用户另装 .NET SDK、Python、NDK 或 JDK；需要 Android 模拟器和可用的 ADB。自动化画面要求 1920×1080 横屏。

首次运行请阅读包内 `使用说明.txt` 和 `RELEASE.txt`，先确认设备与截图，再在有人看护的情况下逐项启用任务。出现识别失败、错位或意外弹窗时应立即停止。不承诺无人值守或未经验证的模拟器、Android、游戏版本和语言环境兼容。

## 使用的运行库

以下为当前 `v0.9.4.1` 发布包使用的主要运行库，版本以该包的构建配置为准：

| 运行库 | 用途与分发方式 | 项目地址 |
| --- | --- | --- |
| .NET 8 / WPF | Windows 桌面界面与托管运行时；自包含发布，随程序打包 | [.NET Runtime](https://github.com/dotnet/runtime)、[WPF](https://github.com/dotnet/wpf) |
| OpenCvSharp4 `4.13.0.20260627` / OpenCV | 截图解码和模板匹配；托管组件与 `OpenCvSharpExtern.dll` 随包提供 | [OpenCvSharp](https://github.com/shimat/opencvsharp)、[OpenCV](https://github.com/opencv/opencv) |
| LSPlant `6.4` | 可选 Billing 功能使用；随包提供 `billing-runtime/liblsplant.so` | [LSPlant](https://github.com/LSPosed/LSPlant) |
| xDL `2.4.0` | 可选 Billing 功能的 Android 动态库加载；随包提供 `billing-runtime/libxdl.so` | [xDL](https://github.com/hexhacking/xDL) |
| Dobby `1.2` | 可选 Billing 功能的原生 Hook；静态链接进 `libggea-billing.so` | [Dobby](https://github.com/jmpews/Dobby) |
| LLVM libc++ | Android 原生组件使用的 C++ 运行库；静态链接，不单独分发 | [LLVM libc++](https://github.com/llvm/llvm-project/tree/llvmorg-18.1.8/libcxx) |

`billing-runtime/` 仅用于可选的 Billing 功能，其第三方许可文件位于包内 `billing-runtime/licenses/`。程序通过 [Android Debug Bridge（ADB）](https://developer.android.com/tools/adb) 连接模拟器；ADB 需由用户在本机或模拟器中提供，不随 GGEA 分发。Python、JDK、Android NDK 和 D8 仅用于构建发布包，终端用户无需安装。

## 校验下载

在 PowerShell 中对下载的 ZIP 运行：

```powershell
(Get-FileHash -Algorithm SHA256 -LiteralPath '.\GGEA-v0.9.4.1-win-x64.zip').Hash.ToLowerInvariant()
```

结果应与同名 `.zip.sha256` 文件第一列完全相同。SHA-256 用于检查文件完整性，不能代替数字签名。包内 `build-info.json` 记录构建使用的完整源码提交、版本、构建参数及逐文件摘要；每次发布的说明也会列出对应提交。构建时的本地包名包含提交短号，GitHub Release 附件使用简洁版本名；两者的 ZIP 内容与摘要必须相同。

## 反馈

可在本仓库的 [Issues](https://github.com/GundamCC/GGEA-Release/issues) 报告下载、解压和运行问题。提供版本、系统环境、复现步骤及已脱敏的日志片段；请勿公开账号信息、Token、完整私人截图或未经脱敏的日志。
