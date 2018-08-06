<!-- TITLE: Qt -->
<!-- SUBTITLE: A quick summary of Qt -->

# 发布
## Windows下的依赖
参考：http://doc.qt.io/qt-5/windows-deployment.html

使用QTDIR/bin/windeployqt 工具来自动打包dll文件

如果为qml项目，则需要用--qmldir参数来指定qml目录

# 常见问题
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

## 编辑qml文件时提示错误 “module not found”
在pro文件中加入QML_IMPORT_PATH地址，改地址为对应qt编译器下的qml目录地址[^qml_import]

示例
>QML_IMPORT_PATH = D:\Qt\5.10.1\msvc2017_64\qml

[^paint_widget]:https://stackoverflow.com/questions/7276330/qt-stylesheet-for-custom-widget
 [^qml_import]:http://doc.qt.io/qtcreator/creator-qml-modules-with-plugins.html#importing-qml-modules