<div align="center">
  <h1 align="center">
    <br/>
    GGEA
  </h1>
</div>

<br/>

<div align="center">
🌟 GGEA SD高达G世纪永恒小助手 🌟
</div>

## 功能简介

- **每日任务**：包含回收战舰、商店购买每日免费礼包、开发&强化一次、略过每日强化培育关卡、消耗AP及领取奖励，以上任务可通过拖拽排序改变执行顺序。
- **领取奖励**：可领取邮件奖励及每日使命奖励，通过配置项可在其他每日任务完成后领取最终的每日使命奖励。
- **AP 消耗**：可自定义顺序及HARD关卡的主线作品略过，支持保存自定义配置。
- **自动刷本**：自动周回对应的关卡，支持调节刷取次数与特殊情况出击。

## 快速开始
### 下载方式
#### 方式一：GitHub Releases（推荐）
前往 [Releases](https://github.com/GundamCC/GGEA-Release/releases) 下载最新版本:
#### 方式二：QQ群组文件下载
GGEA官方群：[1002150086](https://qm.qq.com/q/zkxGhEiVQQ)  

### 使用方式
启动已安装游戏的 Android 模拟器（分辨率 1920 x 1080），并开启 ADB 调试。解压并运行程序文件夹里的 `GGEA.exe`，在右上角「设置」中选择模拟器对应的 `adb.exe`；BlueStacks 用户选择 `HD-Adb.exe`。
<br/>
回到主界面点击「刷新」并选择具体使用的模拟器。
<br/>
勾选任务并在非战斗界面点击「任务开始」。

## 注意事项
- 推荐使用 mumu 模拟器12，获得最佳的使用体验。
- 支持 Windows 10/11 x64。安装包已包含 .NET 运行时，使用者不需要安装。
- GGEA 支持多模拟器切换。
- 目前仅支持 1920 x 1080 分辨率及游戏的简体中文模式，更多的分辨率及语言支持会在日后添加。
- 「修复主界面 Billing 查询卡顿」是可选功能，仅适用于开启 Root 的 x86_64 Android 模拟器。启用期间游戏内购与恢复购买不可用；要使用这些功能，先关闭该选项并重启游戏。
- `config\ap_consumption_profiles.json` 文件保存了当前的AP消耗方案配置。

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

请在 [Issues](https://github.com/GundamCC/GGEA-Release/issues) 中写明 GGEA 版本、Windows 与模拟器环境、复现步骤，以及出问题前后的操作。日志位于解压目录的 `logs/`。
<br/>
或通过GGEA官方群：[1002150086](https://qm.qq.com/q/zkxGhEiVQQ)  进行BUG反馈、功能建议。
