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

![](https://images.malinkang.com/2024/04/01c28b0dd2e8c2629a22e7f68db6216d.jpg)


![](https://images.malinkang.com/2024/04/d7824c3488e6e1d1c9e6b75d6aba86f3.jpg)

## 设置NAME

设置这个Name用来展示在热力图上。

![](images/5.jpg)

依次选择Settings->Secrets and variables -> New repository secret.

![](https://images.malinkang.com/2024/04/c28135ce7ec0a597cd008e75ab645d14.jpg)

输NAME和Secret，然后点 Add secret保存即可。

![](https://images.malinkang.com/2024/04/e45b89ece1816660b2f5e35f8a72acb7.jpg)

## 设置年

依次选择Settings->Secrets and variables -> variables-> New repository variable.

![](https://images.malinkang.com/2024/04/4c2578f3dd27c7db4d8d2403c2e25ecb.jpg)

添加变量名为year，值为年份。如果要显示多个年份，比如2018到2024年的就输入2018-2024。主要微信读书只能拿到2018年之后的数据，所以如果输入2016-2024，还是只会显示2018-2024的数据。

## 设置颜色

和上面设置Year一样依次选择Settings->Secrets and variables -> variables-> New repository variable。
具体的变量名可以参考下表中的变量名，值为色值。

|   变量名	|   变量说明	|
|---	|---	|
|   BACKGROUND_COLOR	|   背景颜色	|
|   DOM_COLOR	|   未填充的色块	|
|   TRACK_COLOR	|   一级颜色	| 
|   SPECIAL_COLOR	|   二级颜色	| 
|   SPECIAL_COLOR2	|   三级级颜色	| 
|   TEXT_COLOR	|   文字颜色	| 

![](https://images.malinkang.com/2024/04/521ec621b6acebc297d9700f9bfac1eb.jpg)



variables示例

![](https://images.malinkang.com/2024/04/e250d7e9952047eb327f7b0a397211d3.jpg)

## 手动运行

配置完成之后，你就可以手动运行一下。

![](images/6.jpg)


最终生成的图保存在OUT_FOLDER文件夹下。

![](https://images.malinkang.com/2024/04/75c38b036cce0ff8cc23d3459defbcb7.jpg)

