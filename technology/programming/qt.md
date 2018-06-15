<!-- TITLE: Qt -->
<!-- SUBTITLE: A quick summary of Qt -->

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

[^paint_widget]:https://stackoverflow.com/questions/7276330/qt-stylesheet-for-custom-widget
 