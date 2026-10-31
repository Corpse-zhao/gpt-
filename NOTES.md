# wxkb_plugin — 文件说明

给分析者（GPT）的上下文：

| 项 | 值 |
| --- | --- |
| 文件名 | `wxkb_plugin`（原始无扩展名） |
| 大小 | 56,914,144 字节（约 54.3 MiB） |
| 格式 | Mach-O 64-bit executable（magic `cffaedfe`，filetype = MH_EXECUTE） |
| 架构 | CPU `0x0100000c` = **arm64e**（iOS 真机 / 越狱环境常见） |
| 语言 | Swift + Objective-C（依赖大量 `/usr/lib/swift/*.dylib`、`libobjc`、`libc++`） |
| 来源 | 微信文件传输收到，无配套源码、无 dSYM/符号表 |

分析建议方向：

1. 用 `otool -l` / `jtool2 -l` 看 `LC_BUILD_VERSION`（最低 iOS 版本、SDK）、`LC_LOAD_DYLIB` 完整依赖列表。
2. 关注是否链接越狱相关库（Substrate / Substitute / ellekit / libhooker），以及 `__cstring` 中的 tweak 名字。
3. `codesign -dvvv` 看签名状态（是否 ad-hoc / 是否重签）。
4. 若需符号级分析，可用 `nm -a` 或 `swift-demangle` 还原 Swift 类名。

下载地址（Release 附件）：
https://github.com/Corpse-zhao/gpt-/releases/download/wxkb_plugin-v1/wxkb_plugin
