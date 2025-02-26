---
title: VsCode
description: for ide vscode
published: true
date: 2025-02-26T06:28:12.850Z
tags: ide, json
editor: markdown
dateCreated: 2024-02-08T11:01:25.815Z
---

# 离线安装扩展
- chrome 安装 [vscode-extension-download](https://chromewebstore.google.com/detail/vscode-extension-download/hkjdjlmpniknglhaobilgigaigleiebd?hl=zh-CN&utm_source=ext_sidebar) 扩展
- 去 https://marketplace.visualstudio.com/ 下载vsix文件
- 点击“Download Extension”按钮，将插件下载到你的计算机上。
- 找到你的下载目录，将 .vsix 文件复制到你要安装该插件的离线计算机上。
- 在离线计算机上启动 VS Code。打开“Extensions”视图，然后点击“...”按钮，在下拉菜单中选择“Install from VSIX”。
- 在文件选择对话框中，选择你刚刚复制的 .vsix 文件，然后点击“Install”按钮。插件应该已经安装成功，如果没有，请尝试重新启动 VS Code。

# 扩展推荐
- [Bookmarks](https://marketplace.visualstudio.com/items?itemName=alefragnani.Bookmarks) 书签
- sftp Natizyskunk版本
- hexdump for VSCode

# 快捷键
### 快速format json 格式
先```Ctrl+A```,``` Ctrl+K+F```后

# 配置
设置缩进4字符(可以试下不设plaintext)
```
{
    "editor.tabSize": 4,
    "editor.insertSpaces": true,
    "[plaintext]": {
        "editor.tabSize": 4,
        "editor.insertSpaces": true
    }
}
```