# 前线任务 1st Remake 中文补丁工具（Switch）

下载 [Releases](https://github.com/Cocoblood9527/fm1rSwitch-zh-patch/releases/latest) 中的 `FM1R-Patcher-0.3.0-windows-x64.zip`，完整解压后运行 `FM1RPatcher.exe`。无需另装 Python 或 .NET。

## 使用

1. 加入游戏本体和 3.0.1 更新文件，支持拖入 NSP、NSZ、XCI、XCZ。
2. 默认使用工具内置译文。需要自定义时，可选择自己的 CSV（包含 `key`、`zh` 列）。
3. 选择输出目录，点击「生成补丁」。如未自动找到密钥，在「密钥设置」中选择本机 `prod.keys`。
4. 按结果目录中的安装说明，将生成的模组放入模拟器模组目录，或将 `Switch安装包.zip` 解压到 SD 卡根目录。游戏语言选择「繁體中文」。

更换补丁前退出游戏，将旧模组及其备份移到模组目录之外；仅改名为 `.bak` 或 `.previous` 仍可能被加载。

## 支持范围

- Windows 10 / 11 x64。
- 游戏 ID：`0100F200178F4000`。
- 本体 + 3.0.1 更新（更新 ID `0100F200178F4800`，版本 `v458752`）。其他版本会被资源校验拒绝。
- 自动检查字符覆盖，并从用户本机游戏资源中的字体生成缺失字形；不支持的字符会阻止生成并给出提示。
- 本工具生成模拟器 / Atmosphère 模组，不重打包游戏为 NSP 或 XCI。

## 0.3.0

采用 2026-10-17 修订译文：8,198 条记录，7,973 条非空译文。只集成补丁所需的 key 和中文译文，不集成参考表里的日文、英文列。内置表不提供 CSV 文件或导出入口；用户仍可使用自己的 CSV。

内置译文与 [fm1r-zh-patch](https://github.com/Cocoblood9527/fm1r-zh-patch) 最新版本的 [`data/zh.csv`](https://github.com/Cocoblood9527/fm1r-zh-patch/blob/main/data/zh.csv) 同步。内置译文随工具版本更新。

应用核心和内置译文模块编译为 Windows 原生扩展，译文以加密压缩数据集成并在内存中读取。这样可以提高直接解包、查看 Python 字节码的难度，但不能保证程序无法被逆向分析；生成后的游戏文本也可被提取。

本仓库发布工具成品与说明，不发布私有译文表和应用核心源码。发布包不含游戏 ROM、更新包、密钥、固件或从游戏提取的资源。所有处理在本机完成，源游戏文件和用户 CSV 不会被修改。

## 验证与限制

Windows 成品在 macOS CrossOver 中完成验证；尚未在原生 Windows 和 Switch 实机上验证。逐条文本回读及资源对象校验不能代替完整剧情、战斗、长文本排版的游戏测试。

工具未做代码签名。完整解压 ZIP 并保留 `_internal` 文件夹，不能只复制 EXE。第三方组件许可及对应源码地址见包内 `第三方组件.txt` 和 `_internal/patcher/resources/licenses/`。
