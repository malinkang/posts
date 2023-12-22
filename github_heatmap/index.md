---
title: "微信读书热力图使用指南"
description: 
date: 2023-12-22T14:28:05+08:00
image: https://images.unsplash.com/photo-1702277854835-0f25f1565ae1?w=800&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHx0b3BpYy1mZWVkfDN8Ym84alFLVGFFMFl8fGVufDB8fHx8fA%3D%3D
math: 
license: 
hidden: false
comments: true
draft: false
tags: [Weread,微信读书,Notion]
---

## 升级

如果你是新用户，可以直接跳过这一步。

打开你Fork的项目，点击Sync fork进行同步

![](https://docs.github.com/assets/cb-75616/mw-1440/images/help/repository/sync-fork-dropdown.webp)

## 权限

确保你打开了读写权限。

依次选择Settings->Actions->General，然后下拉，找到Workflow permissions，如果没有选中Read and write permissions，请选中，然后点下面的save保存。

![](images/1.jpg)


![](images/2.jpg)

## 设置NAME

设置这个Name用来展示在热力图上。

![](images/5.jpg)

依次选择Settings->Secrets and variables -> New repository secret.

![](images/3.jpg)

输NAME和Secret，然后点 Add secret保存即可。

![](images/4.jpg)

## 手动运行

配置完成之后，你就可以手动运行一下。

![](images/6.jpg)


最终生成的图保存在OUT_FOLDER文件夹下。

![](images/7.jpg)


