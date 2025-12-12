---
title: VsCode
description: for ide vscode
published: true
date: 2025-12-12T06:36:04.187Z
tags: ide, json
editor: markdown
dateCreated: 2024-02-08T11:01:25.815Z
---

# 离线安装扩展
- 去 https://open-vsx.org/ 下载vsix文件
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

# Remote SSH
## 安装
- 安装**Remote SSH**插件
- F1 连接到远程host（离线环境需要在有线环境下载好~/.vscode-server）
- 离线最好提前下好cpp等插件

百度云里路径：全部文件 >开发 >安装包与插件 >vscode
## 配置
std pretty-printing 需要先安装std dbg eg. ```libstdc++6-14-dbg```，launch.json 里的steupCommands 不一定有效，printer.py路径通过以下命令得到：
```
find /usr/share -name printers.py | grep libstdcxx
```

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Debug",
            "type": "cppdbg",
            "request": "launch",

            "program": "${workspaceFolder}/build/app",
            "cwd": "${workspaceFolder}",

            "MIMode": "gdb",
            "miDebuggerPath": "/usr/bin/gdb",

            "setupCommands": [
                {
                    "description": "Enable pretty-printing",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                },
                {
                    "description": "Load libstdc++ pretty-printers",
                    "text": "python exec(open('/usr/share/gcc-14/python/libstdcxx/v6/printers.py').read())"
                }
            ]
        }
    ]
}
```
