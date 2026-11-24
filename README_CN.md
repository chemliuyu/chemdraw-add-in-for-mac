[English](README.md) | 简体中文

<div align="center">

![ChemDraw Add-in for Mac，绘制、粘贴、继续编辑。](assets/banner.svg)

# ChemDraw Add-in for Mac

[下载 2.0.1](https://github.com/BoeingART/chemdraw-add-in-for-mac/releases/tag/2.0.1) · [安装指南](docs/installation.md) · [更新记录](CHANGELOG.md) · [快速入门与常见问题](docs/editable-chemdraw-office-mac_CN.md)

</div>

**在 Mac 版 Microsoft Word、PowerPoint 和 Excel 中粘贴、打开并继续编辑 ChemDraw 化学结构。**

在 ChemDraw 中复制化学结构，即可将可编辑的绘图粘贴到 Office，双击后继续编辑。也可以在 Mac ChemDraw 中打开已有的 Windows ChemDraw OLE 对象，保存后将修改同步回原 Office 文档，并保持编辑窗口打开。每个绘图都保留可编辑的源数据和预览图。

## 2.0.1 版本

**2.0.1 是 2.0 系列的首个正式版**，于 2026 年 11 月 11 日发布。代码和文档已同步到 [`main` 分支](https://github.com/BoeingART/chemdraw-add-in-for-mac/tree/main)，[`2.0.1` 标签](https://github.com/BoeingART/chemdraw-add-in-for-mac/tree/2.0.1)对应发布时的代码。

- **原生 ChemDraw OLE**　在 Word、PowerPoint 和 Excel 中将 CDX 结构粘贴为原生 OLE 对象，并编辑已有的嵌入式 ChemDraw 结构。CDXML 和旧版绘图使用矢量载体兼容流程。
- **保存后继续编辑**　按 ⌘S 或使用菜单“保存”，将已保存的结构和预览同步回原 Office 文档。支持新建且未保存的文档，同步期间保留后续输入；切换文档或另存为后，修改仍回到原编辑目标。
- **PowerPoint**　支持编辑组合中的结构，保留同组图片、裁剪、文字和叠放顺序。修复相同对象复制粘贴后无法打开的问题，每个副本可独立编辑，保存时只更新选中的副本。
- **Word**　在原位置回写结构，通过隐藏的暂存文档处理保存，修复临时窗口闪现、对象重复和版式跳动。保存与恢复检查包含开启修订模式的场景。
- **应用内更新**　修复安装更新时错误判断处理器架构的问题，使应用能够完成替换并自动重新打开。

Word 和 PowerPoint 已有粘贴、打开与保存的实机验证记录。Excel 的原生 OLE 实现已通过文件格式和事务检查，安装 Excel 后的实机测试仍待完成。详见 [Word 与 Excel 验证记录](docs/word-excel-native-ole-results.md)、[Word 保存验证记录](docs/word-ole-in-place-results.md)和 [PowerPoint OLE 验证记录](docs/ole-save-performance-results.md)。

## 功能演示

![ChemDraw Add-in for Mac 功能演示](assets/demo.gif)

## 安装与配置

需要 **macOS 12 或更高版本**，以及已单独安装并激活的 **ChemDraw** 和 **Office for Mac**。支持 Word、PowerPoint 和 Excel。

1. 从 [2.0.1 发布页](https://github.com/BoeingART/chemdraw-add-in-for-mac/releases/tag/2.0.1)下载通用 DMG，打开后将应用拖到旁边的 **Applications** 文件夹。安装包适用于 Apple 芯片和 Intel Mac。从旧版迁移时，先完成当前结构编辑并退出插件，再替换应用。
2. 首次打开应用，“**设置加载项**”会分别检查 Word、PowerPoint、Excel 文件访问、辅助功能及助手就绪状态，只配置已安装的 Office 应用。
3. 按系统提示确认授权。程序会自动注册加载项、验证目录写入与读回并启动助手，检查通过后点击“**完成**”。
4. 后续在菜单栏选择“**检查更新**”，确认后会自动下载、替换应用并重新打开，保留已有授权、连接证书和草稿。正在编辑的结构会等待编辑结束后再更新。如果旧版在安装更新时提示架构错误，请手动安装 2.0.1 DMG。
5. 首次启用 Excel 时，按提示授予 Excel 文件访问及自动化权限。已有 Office 授权缺失时，可打开设置或选择“**修复加载项**”。

关闭窗口后，助手会继续在菜单栏运行。如果隐藏了菜单栏图标，可从“应用程序”重新打开本应用以恢复图标。菜单中会显示当前版本。更新时会显示下载进度，并可取消下载；安装完成后，应用会自动重新打开。

## 粘贴与编辑

1. 打开新建或已有的 Word 文档、PowerPoint 演示文稿或 Excel 工作簿。
2. 在 ChemDraw 中选中结构，按 **⌘C** 复制。
3. 在 Office 中按 **⌘V**、右键选择“**粘贴**”，或点击面板中的“**粘贴可编辑绘图 / Paste editable drawing**”按钮。
4. 双击绘图，在 ChemDraw 中编辑。按 **⌘S** 或选择“**保存**”，即可更新原 Office 图片并继续编辑。关闭该 ChemDraw 文档后，会返回原 Office 文档。
5. 由你决定何时保存 Office 文档。新建且尚未保存的文档也支持直接粘贴、打开和回写化学结构。

编辑期间再次粘贴，会创建独立的绘图。切换窗口或另存为后，原编辑仍对应原来的 Office 文档和 ChemDraw 编辑目标。面板和设置窗口会显示操作进度、具体失败原因及下一步操作。

## 常见问题

### Mac 上 ChemDraw 粘贴到 Word 后怎么继续编辑

通过本加载项粘贴结构后，双击绘图即可在 ChemDraw 中编辑。按 ⌘S 或使用菜单“保存”，原 Office 图片会同步更新。PowerPoint 和 Excel 使用相同流程，具体步骤见[快速上手](docs/editable-chemdraw-office-mac_CN.md)。

### 新建的 Office 文档需要先保存吗

新建且尚未保存的 Word、PowerPoint 和 Excel 文档也支持粘贴、打开和回写。Office 文档由你决定何时保存。

### 已有的 Windows ChemDraw OLE 对象怎么处理

2.0.1 支持双击已有的 Windows ChemDraw OLE 对象，在 Mac ChemDraw 中编辑后保存回原 Office 文档。Word 和 PowerPoint 已有实机验证记录；Excel 已通过文件格式和事务检查，实机测试仍待完成。详见[版本说明](#201-版本)。

### 遇到问题在哪里反馈

面板和设置窗口会显示具体失败步骤及下一步操作。可在 [GitHub Issues](https://github.com/BoeingART/chemdraw-add-in-for-mac/issues/new)反馈，附上 macOS、ChemDraw、Office 和加载项版本，写清复现步骤及错误文字。

## 本地数据与恢复

证书、捕获的化学结构和编辑草稿保存在 `~/Library/Application Support/ChemOffice/work`，升级时会保留。各 Office 应用通过各自的沙盒缓存目录交换预览图。

关闭原 Word、PowerPoint 或 Excel 文档时，会保留最新的本地草稿，并关闭对应的 ChemDraw 编辑窗口。双击原绘图可继续中断的编辑。开始另一项编辑时，已关闭的草稿会保留在 `recovery` 目录中。

助手在执行粘贴操作时捕获剪贴板中的化学结构数据，编辑过程在本地完成。可选的 Office 面板连接本地 HTTPS 服务，其 Office.js 库从微软 CDN 加载。

## 构建与验证

从源码构建需要 Apple 命令行工具及 Swift 5.7 或更高版本。运行 `zsh scripts/build.sh` 可为当前架构构建；运行 `zsh scripts/build.sh --universal` 可同时为 Apple Silicon 和 Intel 构建。安装包制作与签名配置见[安装指南](docs/installation.md)。

构建后可使用 PowerPoint OLE 命令行工具。

```sh
build/chemoffice ole-extract input.pptx output.cdx
build/chemoffice ole-export input.pptx edited.cdx new-copy.pptx
build/chemoffice ole-new source.cdx new-presentation.pptx
```

以上命令依次用于提取首个 ChemDraw 对象、导出修改后的演示文稿副本，以及创建含原生 OLE 对象的演示文稿。输出请使用新文件名。运行 `zsh scripts/test-ole.sh` 可检查 Word、PowerPoint 和 Excel 的 OLE 传输格式，并编译 PowerPoint 适配脚本。

已完成的检查记录见[安装就绪检查](docs/installation-readiness-results.md)和[未保存 Office 文档检查](docs/unsaved-office-results.md)。练习文档见[示例](examples/README.md)。

版权所有 © 2026 ChemDraw Add-in for Mac 贡献者。根据 [Apache License 2.0](LICENSE) 发布。
