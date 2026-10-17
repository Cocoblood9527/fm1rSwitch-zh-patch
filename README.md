# 前线任务 1st Remake 中文补丁工具（Switch）

下载 [Releases](https://github.com/Cocoblood9527/fm1rSwitch-zh-patch/releases/latest) 中的 `FM1R-Patcher-0.3.0-windows-x64.zip`，完整解压后运行 `FM1RPatcher.exe`。无需另装 Python 或 .NET。

## 使用

1. 加入游戏本体和 3.0.1 更新文件，支持拖入 NSP、NSZ、XCI、XCZ。
2. 默认使用工具内置译文。需要自定义时，可选择自己的 CSV（包含 `key`、`zh` 列）。
3. 选择输出目录，点击「生成补丁」。如未自动找到密钥，在「密钥设置」中选择本机 `prod.keys`。
4. 生成完成后点击「打开结果」，按下面对应设备的步骤安装。

## 生成的文件

```text
结果目录/
├── FM1R-ZH-Custom/       模拟器使用
│   └── romfs/Data/sharedassets0.assets
├── Switch安装包.zip     Switch 真机使用
├── 安装说明.txt
└── 生成报告.json
```

## 模拟器安装（Astris / Ryujinx）

1. 确认模拟器中已启用本游戏的 3.0.1 更新，然后完全退出正在运行的游戏。
2. 在游戏列表中右键本游戏，选择「打开模组目录」（Open Mods Directory，名称可能随版本不同）。
3. 将结果目录中的整个 `FM1R-ZH-Custom` 文件夹复制进去。不要复制整个结果目录，也不要只复制里面的资源文件。
4. 若模拟器提供模组管理或勾选项，确认本补丁已启用。重新启动游戏，在游戏内将语言设为「繁體中文」。

正确层级：

```text
<该游戏的模组目录>/
└── FM1R-ZH-Custom/
    └── romfs/
        └── Data/
            └── sharedassets0.assets
```

更换补丁前退出游戏，将旧模组及其备份移到模组目录之外，再放入新模组。仅改名为 `.bak` 或 `.previous` 仍可能被加载；目录中只保留一份本补丁。

## Switch 真机安装（Atmosphère）

需要能运行 Atmosphère 并加载 RomFS 覆盖模组的主机；原厂系统不能直接加载本补丁。主机上的游戏也需安装 3.0.1 更新。以下为安装方法，目前尚未经过本项目的真机验证。

1. 完全退出游戏；如需取出 SD 卡，先关闭主机。
2. 将结果目录中的 `Switch安装包.zip` 解压到 SD 卡根目录，将其中的 `atmosphere` 文件夹与卡上同名文件夹合并。SD 卡根目录指打开卡后直接看到 `atmosphere` 的位置，不要再套一层「Switch安装包」文件夹。
3. 检查 SD 卡上的文件路径是否与下面一致。文件夹使用本体 ID `0100F200178F4000`，不是更新 ID。
4. 安全弹出 SD 卡并装回主机，进入 Atmosphère 后启动游戏，在游戏内将语言设为「繁體中文」。

```text
sd:/atmosphere/contents/0100F200178F4000/romfs/Data/sharedassets0.assets
```

如果目标文件已存在，先备份到补丁目录之外，再替换。不要同时使用其他覆盖 `sharedassets0.assets` 的模组。

## 卸载与排查

- 模拟器：退出游戏，将 `FM1R-ZH-Custom` 文件夹移出该游戏的模组目录，再启动游戏。
- Switch：退出游戏，移走上面路径中的 `sharedassets0.assets`；若安装前备份过同名文件，恢复备份。保留其他模组的文件。
- 没有生效：检查实际运行的是 3.0.1、游戏语言为「繁體中文」、文件夹没有多套一层，以及补丁已启用，然后完全退出并重新启动游戏。
- 仍显示旧译文：检查模组目录内是否还有旧补丁或改名后的备份。
- 显示异常或无法启动：暂时移走本补丁确认是否恢复，并检查是否存在覆盖同一资源的其他模组。反馈时附上 `生成报告.json` 和问题画面。

## 支持范围

- Windows 10 / 11 x64。
- 游戏 ID：`0100F200178F4000`。
- 本体 + 3.0.1 更新（更新 ID `0100F200178F4800`，版本 `v458752`）。其他版本会被资源校验拒绝。
- 自动检查字符覆盖，并从用户本机游戏资源中的字体生成缺失字形；不支持的字符会阻止生成并给出提示。
- 本工具生成模拟器 / Atmosphère 模组，不重打包游戏为 NSP 或 XCI。

## 0.3.0

采用 2026-10-17 修订译文：8,198 条记录，7,973 条非空译文。只集成补丁所需的 key 和中文译文，不集成参考表里的日文、英文列。用户可使用自己的 CSV。

内置译文与 [fm1r-zh-patch](https://github.com/Cocoblood9527/fm1r-zh-patch) 最新版本的 [`data/zh.csv`](https://github.com/Cocoblood9527/fm1r-zh-patch/blob/main/data/zh.csv) 同步。

本仓库发布工具成品与说明，不发布私有译文表和应用核心源码。发布包不含游戏 ROM、更新包、密钥、固件或从游戏提取的资源。

## 验证与限制

第三方组件许可及对应源码地址见包内 `第三方组件.txt` 和 `_internal/patcher/resources/licenses/`。
