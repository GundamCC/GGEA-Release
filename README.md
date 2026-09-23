# GGEA

《SD高达G世纪 永恒》的 Windows 桌面辅助工具。GGEA 连接 Android 模拟器，通过截图识别游戏画面，再用 ADB 完成你勾选的任务。本仓库提供安装包、更新说明和问题反馈入口。

[下载最新版本](https://github.com/GundamCC/GGEA-Release/releases/latest) · [反馈问题](https://github.com/GundamCC/GGEA-Release/issues)

## 功能简介

- **每日任务**：勾选任务并拖动调整顺序。目前包括基地战舰回收、商店免费培育包、开发与强化，以及强化关卡的可用略过。部分任务对模拟器有要求，界面会提示是否可用。
- **领取奖励**：领取礼物箱邮件和每日使命奖励，可放进每日任务队列。
- **AP 消耗**：按保存的作品与 HARD 关卡方案执行。首次使用、更换模拟器或游戏更新后，先核对关卡、模板和滑动位置。
- **模拟器与截图**：通过 ADB 发现设备、显示游戏截图；内置 MuMu、雷电、BlueStacks 和自定义模拟器适配。
- **模板维护**：从截图中框选并保存识别模板，也可以测试匹配结果，方便在游戏界面变化后调整。

## 快速开始

1. 从 [Releases](https://github.com/GundamCC/GGEA-Release/releases) 的 **Assets** 下载 `GGEA-v0.9.4.1-win-x64.zip`（或对应的新版本），完整解压到一个可写文件夹。不要选 GitHub 自动生成的 **Source code** 压缩包，也不要只提取 `GGEA.exe`。
2. 启动已安装游戏的 Android 模拟器，并开启 ADB 调试。运行解压目录里的 `GGEA.exe`，在右上角「设置」中选择 `adb.exe`；BlueStacks 用户选择 `HD-Adb.exe`，并在模拟器「设置 → 高级」中开启 Android Debug Bridge。
3. 回到主界面点击「刷新」，确认选中的设备正确，再点「截图」检查画面。自动任务需要模拟器输出 **1920×1080 横屏**截图。
4. 先手动确认游戏已登录并处于正常页面。第一次运行时只勾选一个任务，点击「任务开始」，观察识别和点击是否正确；确认无误后再增加其他任务。

更详细的设置和操作步骤在安装包的 `使用说明.txt` 中。

## 注意事项

- 支持 Windows 10/11 x64。安装包已包含 .NET 运行时，使用者不需要安装 .NET SDK、Python、JDK 或 Android NDK。ADB 需由本机或模拟器提供。
- 游戏页面、分辨率或模板变化都可能让识别失效。遇到点击错位、识别失败、付费页面或意外弹窗，请立即中止任务并手动检查；不要让程序无人看护地连续运行。
- 「修复主界面 Billing 查询卡顿」是可选功能，仅适用于开启 Root 的 x86_64 Android 模拟器。启用期间游戏内购与恢复购买不可用；要使用这些功能，先关闭该选项并重启游戏。
- 更新前备份自己的 `config/` 配置、AP 方案和自定义模板。建议将新版本解压到新目录，再按需迁移这些文件，不要直接用新包覆盖旧配置。

## 校验下载

Release 附件中还提供同名的 `.zip.sha256` 文件。例如校验 `v0.9.4.1`：

```powershell
(Get-FileHash -Algorithm SHA256 -LiteralPath '.\GGEA-v0.9.4.1-win-x64.zip').Hash.ToLowerInvariant()
```

输出应与 `.zip.sha256` 的第一列一致。包内 `build-info.json` 记录源码提交和文件摘要。SHA-256 用于检查下载是否完整，不是数字签名。

## 使用的项目

- [.NET Runtime](https://github.com/dotnet/runtime) 与 [WPF](https://github.com/dotnet/wpf)：Windows 程序和界面。发布包采用自包含构建。
- [OpenCvSharp](https://github.com/shimat/opencvsharp) `4.13.0.20260627` 与 [OpenCV](https://github.com/opencv/opencv)：截图解码和模板匹配；`OpenCvSharpExtern.dll` 随包提供。
- [LSPlant](https://github.com/LSPosed/LSPlant) `6.4`、[xDL](https://github.com/hexhacking/xDL) `2.4.0`、[Dobby](https://github.com/jmpews/Dobby) `1.2` 与 [LLVM libc++](https://github.com/llvm/llvm-project/tree/llvmorg-18.1.8/libcxx)：用于可选的 Billing 功能。LSPlant、xDL 随包提供；Dobby 和 libc++ 静态链接到原生组件中。相关许可文件位于 `billing-runtime/licenses/`。
- [Android Debug Bridge（ADB）](https://developer.android.com/tools/adb)：连接模拟器、截图和操作游戏；不包含在 GGEA 安装包里。

## 问题反馈

请在 [Issues](https://github.com/GundamCC/GGEA-Release/issues) 中写明 GGEA 版本、Windows 与模拟器环境、复现步骤，以及出问题前后的操作。日志位于解压目录的 `logs/`；上传日志或截图前，请先遮盖账号信息和其他私人内容。
