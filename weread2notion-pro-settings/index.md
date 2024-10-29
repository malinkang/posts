---
title: "Werad2NotionPro支持自定义设置了"
description: 
date: 2024-10-03T15:28:05+08:00
image: https://images.malinkang.com/2024/03/19dd1580dd991c7985abea7724c87043.png
cover: 
    linkFullImages: https://images.malinkang.com/2024/03/19dd1580dd991c7985abea7724c87043.png
math: 
license: 
hidden: false
comments: true
draft: false
tags:
    - 微信读书
    - Notion
    - WeRead
---

## 自定义设置

现在Weread2NotionPro支持用户设置同步样式了。接下来就给大家讲解下如何使用。

首先就是同步代码。打开你Fork的项目，点击Sync fork进行同步，如果有冲突可以点击Discard那个按钮。

![](https://images.malinkang.com/2024/03/53c917e4bcfd70d0509a05680a2f10b4.png)

同步成功之后，手动运行一下任务。打开你Fork的项目，依次点击Actions->weread note sync-> Run workflow，就可以运行了。

![](https://images.malinkang.com/2024/03/41ba7acfac4c8de1cfd4ee40443644b8.jpg)

运行完成之后，Notion中会增加一个名为设置的database，点击打开。

![](https://images.malinkang.com/2024/10/cad3dd6dd00b07881d758e4ad16b3ec7.png)

接下来依次讲解下每个配置：

NotinPage、NotinToken和WeReadCookie三个值用来存储之前填写到Github上的值

### 同步书签

之前书签和划线都会被同步到Notion，如果不希望同步书签，取消勾选即可，默认是勾选状态。

### 样式

样式用于自定义同步到Notion的样式，目前支持如下值：
* callout：默认样式
* quote：引用样式
* paragraph：普通段落
* bulleted_list_item：无序列表
* numbered_list_item：有序列表

### 根据划线颜色设置文字颜色

之前同步默认会根据划线颜色设置Notion中文字的颜色，如果不希望根据划线颜色来设置Notion中文字的颜色，取消勾选即可，默认是勾选状态。

以上就是所有的配置项。所有的修改只会对后续的同步有效，并不会对之前同步过的数据进行修改。未来会把热力图的配置也迁移到Notion中。你还需要哪些自定义设置，请在评论区里留言。

## 修复重复Bug

国庆节前代码重构，导致同步会有重复的书籍，目前已经修复，之前重复的书籍需要手动删除。

## 如何新增图表


Notion出了图表功能之后，我也给自己的读书模板增加了图表功能，一直有人问如何设置，我也简单讲解下。

![](https://images.malinkang.com/2024/10/5df217cc45d549a276fd54430eceab07.png)


在月这个Database中新增一列函数类型，名字为阅读时长（小时）。默认提供的时长单位是秒。所以直接使用公式`floor(prop("时长")/3600)`对将阅读时长转化为小时格式。

在想要放置图表的地方添加数据库的链接视图，选择月这个database。

![](https://images.malinkang.com/2024/10/f7a379427d7552dd9be84cb967dd9fe3.png)

X轴显示内容选择日期然后选择月

![](https://images.malinkang.com/2024/10/a5deb6ae3046d0c36aa61d5a79a6e945.png)

Y轴显示内容选择阅读时长（小时）然后选择总和

![](https://images.malinkang.com/2024/10/77050fa1477c95423c20bf3c8701a8f5.png)

筛选选择本年

![](https://images.malinkang.com/2024/10/027fbc8cd62e48078c913991185d8b1c.png)

这样就可以看到今年每个月的阅读时长图表了。







