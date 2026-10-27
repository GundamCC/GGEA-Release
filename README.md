# GGEA 旧客户端兼容发行入口

[简体中文](README.md) | [日本語](README.ja.md)

GGEA 的源码、产品介绍、问题反馈和后续正式发布统一由 [GGEA 主仓库](https://github.com/GundamCC/GGEA)维护。

- [正式发布入口](https://github.com/GundamCC/GGEA/releases)
- [使用与下载说明](https://github.com/GundamCC/GGEA#快速开始)
- [问题反馈](https://github.com/GundamCC/GGEA/issues)
- [日文说明](https://github.com/GundamCC/GGEA/blob/main/README.ja.md)
- [旧版与过渡包下载](https://github.com/GundamCC/GGEA-Release/releases)
- [社区 QQ 群](https://qm.qq.com/q/zkxGhEiVQQ)

## 当前状态

[1.3.4.0 正式版](https://github.com/GundamCC/GGEA/releases/tag/v1.3.4.0)已在主仓库发布；本仓库已发布[同版本兼容过渡包](https://github.com/GundamCC/GGEA-Release/releases/tag/v1.3.4.0)，ZIP 与 SHA-256 文件和主仓库完全一致。新用户优先从主仓库下载，旧客户端可继续通过本仓库升级。已有发布记录与下载附件保持原位，历史下架记录不代表附件恢复可用。

## 兼容职责

旧客户端固定请求本仓库的最新正式 Release，并严格校验附件属于本仓库。因此，本仓库保留已有下载、必要的过渡 Release，以及根目录 `update-sources.json`。空来源列表是有效的 v1 配置，不是主发布地址重定向，也不会自动把旧客户端切换到新仓库。

本次已使用与主仓库完全相同的已验证过渡 ZIP 和 SHA-256 文件在此发布；旧客户端安装过渡包后，由新程序访问 GGEA 主仓库。不能只创建一条外链 Release，也不能把本仓库的附件 URL 改成新仓库 URL。

[发布与验证顺序](https://github.com/GundamCC/GGEA/blob/main/docs/release-migration.md)。过渡发布及旧客户端升级链路未经验证前，不能关闭兼容入口；之后也不删除已有下载或来源发现文件。本仓库不再独立维护完整产品介绍，后续常规版本在主仓库发布。

## 校验与历史说明

下载 ZIP 时同时下载同名 `.zip.sha256`，使用 PowerShell `Get-FileHash -Algorithm SHA256` 核对摘要。SHA-256 用于完整性检查，不是数字签名；包内 `build-info.json` 记录源码提交及文件摘要。

历史版本说明保留在 `releases/`，以对应包内容为准。当前主程序的[许可范围](https://github.com/GundamCC/GGEA/blob/main/LICENSE_SCOPE.md)与[第三方声明](https://github.com/GundamCC/GGEA/blob/main/resources/common/licenses/NOTICE.txt)不能替代旧包自己的许可文件；可选插件说明在 [GGEA-Extensions](https://github.com/GundamCC/GGEA-Extensions)。
