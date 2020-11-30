---
title: Qt
description: A quick summary of Qt
published: true
date: 2020-11-30T07:40:36.186Z
tags: 
---

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

## MouseArea事件向下层传递[^mouse_area]
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

```
 void CustomWidget::paintEvent(QPaintEvent *)
 {
     QStyleOption opt;
     opt.init(this);
     QPainter p(this);
     style()->drawPrimitive(QStyle::PE_Widget, &opt, &p, this);
 }
 ```

# 常见问题
qdatabase 驱动无法加载
手动设置 QT_PLUGIN_PATH C:\Qt\4.8.6\plugins

[^paint_widget]:https://stackoverflow.com/questions/7276330/qt-stylesheet-for-custom-widget
[^qml_import]:http://doc.qt.io/qtcreator/creator-qml-modules-with-plugins.html#importing-qml-modules
[^mouse_area]:https://stackoverflow.com/questions/16183408/mousearea-stole-qml-elements-mouse-events