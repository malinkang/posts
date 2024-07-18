---
title: "快捷指令触发Github Action"
description: 
date: 2024-07-12T09:40:05+08:00
image: https://images.unsplash.com/photo-1663813251302-e5d2c7199e86?q=80&w=2660&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
math: 
license: 
hidden: false
comments: true
draft: false
tags:
    - 快捷指令
    - Github Action
---

之前一直有朋友问我为什么我的Weread2Notion-Pro为什么没有执行同步，因为Github执行Action并不准时，有的时候可能会延迟几个小时。今天就给大家分享一下如何使用快捷指令来准时触发Github Action执行，并且实现比如关闭微信读书同步笔记。

## 第一步：获取快捷指令
打开链接获取指令：[https://www.icloud.com/shortcuts/6282dd771f8849ffb8816ebc7d001155](https://www.icloud.com/shortcuts/6282dd771f8849ffb8816ebc7d001155)

## 第二步：填值

打开你获取的快捷指令，会看到这里需要填3个值
![](https://images.malinkang.com/2024/07/3ff0351851affd2961284ebfd1dda7e6.png)

name是你的Github的用户名，repository是你的仓库名。比如我的weread2notion-pro的仓库地址是：[https://github.com/malinkang/weread2notion-pro](https://github.com/malinkang/weread2notion-pro)，那么我的name就填malinkang，repository值就填weread2notion-pro。

第三个值是token，获取比较麻烦一些。

1. 首先打开网页：[https://github.com/settings/apps](https://github.com/settings/apps)，按照下图标的顺序点击，进入Token创建页面

![image-20240716144430148](https://images.malinkang.com/2024/07/af9e356a054fe0b9a910e13c361d53ec.png)

2. 在Token创建页面我们需要填写和勾选如下三个值：

* Note是备注信息，可以根据个人情况填写。
* Expiration是Token的过期时间，我选择的是No expration，这样Token就不会过期
* 第三个是Token的作用范围，勾选workflow，这样这个Token就有权限触发我们的Github Action.

![](https://images.malinkang.com/2024/07/4a0645faa6aeefc3cd90c8de44df018b.png)

填写完成之后点击最下面的Generate token创建。

创建完成会跳转到Token列表，点击复制按钮复制你创建的Token，然后填写到快捷指令中。

![](https://images.malinkang.com/2024/07/26b8419a0b9786de1aab24270221a216.png)

最终的效果如下图所示：
![](https://images.malinkang.com/2024/07/671e772c4b793c37192fabd526cdf8ae.png)

现在我们可以手动运行这个快捷指令触发Github Action了。

## 第三步：自动化设置

接下来我们可以通过自动化设置实现关闭微信读书同步微信读书笔记。

1. 打开手机里的快捷指令，切换到中间的自动化tab，然后点击右上角的+号创建自动化。


![](https://images.malinkang.com/2024/07/5ee22f6ecd09f56d39cfe075a258d8a5.png)

2. 点击创建个人自动化，向下滑动找到App，点击进入。

![image-20240716140946436](https://images.malinkang.com/2024/07/5bbe45c5f4eebf49b3a81f001e6317bd.png)

3. App选择微信读书，勾选已关闭，点击右上角下一步。

![](https://images.malinkang.com/2024/07/ade2e856d164738843e224cb49c926e6.png)

4. 点击添加操作，搜索快捷指令，然后选择运行快捷指令。

![](https://images.malinkang.com/2024/07/b7788d888e830365bf34668a3d32f326.png)

5. 点击快捷指令，选择第一步我们获取的快捷指令

![](https://images.malinkang.com/2024/07/bff434f1bf16ab3fd8bb9f61ef345c91.png)

6. 最后点击下一步，然后关闭运行前询问。如果不关闭的话，每次运行这个自动化都会弹一个对话框询问是否运行这个自动化。关闭之后，可以无感运行这个 自动化。

![](https://images.malinkang.com/2024/07/4ae414d5d036d0837b7a90de58cf6bb9.png)



这样之后我们就可以在关闭微信读书的时候自动触发笔记同步。

同理我们也可以实现如下操作：

* 关闭豆瓣时触发Douban2Notion同步

* 关闭Toggl时触发Toggle2Notion同步。

* 关闭多邻国时触发Duolingo2Notion同步

* 关闭Keep时触发Keep2Notion同步

* ...

  

快捷指令的触发条件有很多，也可以通过设置固定时间来同步，你可以自行研究。

另外之前我说每个月Github Action有2000分钟的限额，后来看了一下只针对私有仓库，公共仓库是不限额的，所以我们可以提高我们同步的频率，再也不用担心额度用不完了。
