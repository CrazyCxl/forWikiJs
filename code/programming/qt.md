---
title: Qt
description: A quick summary of Qt
published: true
date: 2024-06-04T01:33:28.791Z
tags: 
editor: markdown
dateCreated: 2024-02-08T11:01:51.252Z
---

# 环境
## 安装
太慢使用其他源：
./qt-unified-linux-x64-XXX-online.run --mirror https://mirrors.tuna.tsinghua.edu.cn/qt

### 常见问题
#### cdb 未找到
- vs安装sdk
- 在应用和功能中查找```Windows Software Development Kit```
- 右键修改，然后勾选```Debugging Tools for Windows```

#### windows cmake编译时Ninja报错
改变生成器 
>Select your Kit. Go to "CMake Generator" -> "Change...". Change the "Generator" entry there.

## linguist
### cmake中使用lupdate更新
```
set(TS_FILES resource/translations/infrared_zh_CN.ts)
find_program(LUPDATE_EXECUTABLE lupdate)
add_custom_target(update_ts
    COMMAND ${LUPDATE_EXECUTABLE} ${QML_SOURCES} -ts ${CMAKE_SOURCE_DIR}/${TS_FILES}
    COMMENT "Updating translation files"
)
add_dependencies(infrared update_ts)
```

## 转vs项目
### cmake
```
mkdir build
cd build
cmake .. -G "Visual Studio 16 2019" -DCMAKE_PREFIX_PATH="H:\Qt\5.15.2\msvc2019_64"
```

# 发布
## 库生成配置
### disables the lib prefix
没有lib前缀
CONFIG += no_plugin_name_prefix
### disable symlinks & versioning
没有软连接
CONFIG += plugin

## Windows下的依赖
参考：http://doc.qt.io/qt-5/windows-deployment.html

使用QTDIR/bin/windeployqt 工具来自动打包dll文件

如果为qml项目，则需要用--qmldir参数来指定qml目录

## 打包包含WebEngine项目后无法运行的问题
解决方法：
>将QtWebEngine的import放在最前

参考：https://forum.qt.io/topic/81587/qt-5-9-5-9-1-qtwebengine-not-installed-after-qtwindeploy

# QML
## 编辑qml文件时提示错误 “module not found”
在pro文件中加入QML_IMPORT_PATH地址，改地址为对应qt编译器下的qml目录地址[^qml_import]

示例
>QML_IMPORT_PATH = D:\Qt\5.10.1\msvc2017_64\qml

## MouseArea事件向父层传递[^mouse_area]
示例代码：
```
RowLayout {
    TextEdit { text: "Hi" }
    Slider {}
    CheckBox { text: "CheckBox"}

    MouseArea {
        anchors.fill: parent
        propagateComposedEvents: true

        onClicked: mouse.accepted = false;
        onPressed: mouse.accepted = false;
        onReleased: mouse.accepted = false;
        onDoubleClicked: mouse.accepted = false;
        onPositionChanged: mouse.accepted = false;
        onPressAndHold: mouse.accepted = false;
    }
}
```
## 嵌入式控件
```
default property alias _contentChildren: content.data
```
# Widget
## 自定义控件的stylesheet未生效
### 解决方案一
在控件类的内部调用setStylesheet方法

### 解决方案二[^paint_widget]
重写绘制方法，加入以下内容：

```c++
 void CustomWidget::paintEvent(QPaintEvent *)
 {
     QStyleOption opt;
     opt.init(this);
     QPainter p(this);
     style()->drawPrimitive(QStyle::PE_Widget, &opt, &p, this);
 }
 ```

# 常见问题
## cmake构建MSVC项目失败
可能是jom命令找不到
将jom目录添加到系统或项目path环境变量

## qdatabase 驱动无法加载
手动设置 QT_PLUGIN_PATH C:\Qt\4.8.6\plugins

## 色表支持
参考：https://stackoverflow.com/questions/41744654/is-there-a-default-color-table-colormap-available-in-qt
色表下载：http://www.kennethmoreland.com/color-advice/
初始化 QImage::Format_Indexed8 使用 QImage::setColorTable()
```c++
QVector<QRgb> ctable;

QFile file("black-body-table-byte-0128.csv");
if(!file.open(QIODevice::ReadOnly))
{
    QMessageBox::information(0, "error", file.errorString());
}

QTextStream in(&file);

while(!in.atEnd())
{
    QString line = in.readLine();    
    QStringList values = line.split(",");
    ctable.append(qRgb(values[1].toInt(), values[2].toInt(), values[3].toInt()));
}

file.close();
```

[^paint_widget]:https://stackoverflow.com/questions/7276330/qt-stylesheet-for-custom-widget
[^qml_import]:http://doc.qt.io/qtcreator/creator-qml-modules-with-plugins.html#importing-qml-modules
[^mouse_area]:https://stackoverflow.com/questions/16183408/mousearea-stole-qml-elements-mouse-events