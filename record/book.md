---
title: Book
description: 书源编辑记录
published: true
date: 2024-04-08T03:10:10.074Z
tags: life
editor: markdown
dateCreated: 2024-02-08T11:00:52.660Z
---

# 介绍
github地址：https://github.com/gedoor/legado
规则：https://mgz0227.github.io/The-tutorial-of-Legado/

# 书源规则
json格式参考：https://blog.csdn.net/koflance/article/details/63262484

## 搜索
列表规则：```$.[*]```
作者规则：```.author```
```
[
    { 
        "url_list": "\/book\/105412\/", "url_img": "https:\/\/www.qmxs123.com\/bookimg\/105\/105390.jpg", "articlename": "\u6df1\u6d77\u4f59\u70ec", 
        "author": "\u8fdc\u77b3", 
        "intro": "\u5728\u90a3\u4e00\..." 
    }, 
```

## 详情

作者规则：class.dd_box.0@span.0@text
字数规则：class.dd_box.1@span.1@text##字数：
```
<div class="books">
	<div class="book_info">
		<div class="cover"><img src="https://www.qmxs123.com/bookimg/105/105390.jpg" width="80" height="100" alt="深海余烬"></div>
		<div class="book_box">
		    <dl>
		        <dt class="name">深海余烬</dt>
		        <dd class="dd_box"><span>作者：远瞳</span><span>分类：女生</span></dd>
		        <dd class="dd_box"><span>状态：连载</span><span>字数：204.13 万字</span></dd>
		        <dd class="dd_box"><span style="width: 100%;">更新：2023-11-22 23:58:33</span></dd> 
		    </dl>
		</div>
	</div>
```
最新章节规则：class.book_last@dl@dd.0@a@text
```
	<div class="book_last">
		<dl>
			<dt>深海余烬全文阅读 <a class="oninfo" rel="nofollow" title="更新报错留言" href="javascript:book_error('105390','深海余烬','1700707565');">更新报错</a></dt>
		<dd><a href ="/book/105412/677.html">第675章 “第五方舟”</a></dd>
		<dd><a href ="/book/105412/676.html">第674章 它们在“交流”</a></dd>
		<dd><a href ="/book/105412/675.html">第673章 泰德里尔的造访</a></dd>
```

目录地址规则：class.book_more@a@href
```
	<div class="book_more"><a href="/book/105412/list.html">查看更多章节>></a></div>
</div>
```

## 目录
列表规则：class.book_last@dl@dd!0@a
章节名称：text
章节地址：href
```
<div class="book_last">
	<dl><dt></dt>
		<dd><a href="#footer" style="color:Red;">↓↓↓ 直达页面底部</a></dd>
		
		<dd><a href ="/xs/120550/1.html">第1章 那天，起了很大的雾</a></dd>
		<dd><a href ="/xs/120550/2.html">第2章 失乡号的船长</a></dd>
		<dd><a href ="/xs/120550/3.html">第3章 边境迷航</a></dd>
		<dd><a href ="/xs/120550/4.html">第4章 灵界飚船</a></dd>
```

列表规则：ul.2@li@a
```
取第二个ul元素对应的内容
```

### css规则
测试：https://try.jsoup.org/
介绍：https://blog.csdn.net/hou_angela/article/details/80519718

示例：
@css:dl>dd>a
```
                <dl class="panel-body panel-chapterlist panel-body-34e68100">
                    <dd class="col-sm-6 col-md-3 chapter-34e68100">
                        <a href="/read/6644/3007932.html">第一章 那天，起了很大的雾</a>
                    </dd>
```
## 正文
正文规则：id.chaptercontent@html

```
    </head>
    <body id="read" class="read">
        <div class="header">
            <a class="home" href="javascript:history.go(-1);">
                <svg class="lnr lnr-chevron-left-circle">
                    <use xlink:href="#lnr-chevron-left-circle"></use>
                </svg>
            </a>
            <span class="title">1）第1章 那天，起了很大的雾_深海余烬</span>
            <a class="user" href="/">
                <svg class="lnr lnr-home">
                    <use xlink:href="#lnr-home"></use>
                </svg>
            </a>
        </div>
        <div class="Readpage" style="background:#FFFFFF;padding:2px;height:40px; line-height:40px;">
            字体：<a id="fontbig" class="sizebg" onclick="nr_setbg('big')">大</a>
            <a id="fontmiddle" class="sizebg" onclick="nr_setbg('middle')">中</a>
            <a id="fontsmall" class="sizebg" onclick="nr_setbg('small')">小</a>
            &nbsp;&nbsp;&nbsp;&nbsp;<a id="huyandiv" class="button huyanon" onclick="nr_setbg('huyan')">护眼</a>
            <a id="lightdiv" class="button lightoff" onclick="nr_setbg('light')">关灯</a>
        </div>
        <div class="Readpage">
            <a href="/xs/120550/" id="pb_prev" class="Readpage_up">上一章</a>
            <a href="/xs/120550/" id="pb_mulu" class="Readpage_up">目录</a>
            <a href="/xs/120550/1_2.html" id="pb_next" class="Readpage_down js_page_down">下一章</a>
        </div>
        <div id="read1"></div>
        <div id="chaptercontent" class="Readarea ReadAjax_content">
            第1章那天，起了很大的雾<br/>
            <br/>
            无边无际的浓雾在窗外翻滚，浓郁的仿佛整个世界都已经消失在雾的彼端，唯有混沌未明的天光穿透雾气照进屋来，让这安静的房间里维持着一种半昏半明的光线。<br/>
            <br/>
```
