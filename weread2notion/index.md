---
title: "WeRead2Notion使用文档"
description: 
date: 2023-09-10T15:28:05+08:00
image: https://images.unsplash.com/photo-1663813251302-e5d2c7199e86?q=80&w=2660&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
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

## 使用

### Fork工程

打开[Weread2Notion](https://github.com/malinkang/weread2notion)，点击右上角的Fork（顺便点个star谢谢）

![](images/fork.jpg)

### 获取微信读书Cookie

1. 浏览器打开[网页版微信读书](https://weread.qq.com/)扫码登录
2. 按F12进入开发者模式，依次点网络->文档，然后选中weread.qq.com，下拉找到Cookie，复制Cookie值

![](images/weread.jpg)

### 获取NotionToken

1. 浏览器打开[https://www.notion.so/my-integrations](https://www.notion.so/my-integrations)点击New integration按钮，输入name后点Submit。

![](images/integrations.jpg)

2. 提交完成后，进入Secrets页面，先点击Show，然后点击Copy复制，后面需要用到

![](images/integrations2.jpg)

### 复制Notion模板

1. 浏览器打开模板[https://malinkang.notion.site/e27842548a6d4a81bc7aea736d90d6dd?v=b255858d3eaa409f97f1ecb32a14a5b6&pvs=4](https://malinkang.notion.site/e27842548a6d4a81bc7aea736d90d6dd?v=b255858d3eaa409f97f1ecb32a14a5b6&pvs=4)，点击右上角的Duplicate复制。

![](images/duplicate.jpg)

2. 打开你刚复制的模板，点击右上角的三个点，找到`Connections`，然后添加你创建的Integration。

![](images/connections.jpg)

3. 点击右上角的Share，然后点击Copy link获取database的链接，获取链接后比如 https://malinkang.notion.site/e27842548a6d4a81bc7aea736d90d6dd?v=b255858d3eaa409f97f1ecb32a14a5b6&pvs=4 中间的e27842548a6d4a81bc7aea736d90d6dd就是DatabaseID
![](images/copy.jpg)

### 在Github的Secrets中添加变量

1. 打开你fork的工程，点击Settings->Secrets and variables->New repository secret

![](images/secret.jpg)

2. Name输入WEREAD_COOKIE，Secret输入框中填入你前面获取的微信读书Cookie，然后点击Add secret

![](images/secret2.jpg)

3. 同理，继续点击New repository secret，分别增加变量NOTION_TOKEN和NOTION_DATABASE_ID。最终的结果如下图所示。

![](images/secret3.jpg)

{{< notice warning >}} 注意这三个变量名一定要填写正确，一个字母都不能错，否则会同步失败。之前遇到过有的同学NOTION_DATABASE_ID写成NOTION_DATEBASE_ID。{{< /notice >}}

## 问题排查

1. 可以点击你Fork项目的Action，查看运行状态，绿色是成功，红色是失败。

![](images/action.jpg)

{{< notice warning >}} 运行成功，只代表程序没有出错，不代表就一定同步数据，比如微信Cookie过期就不会报错。所以如果运行成功，Notion中没有数据的话，也可以通过下面第2步来查看日志{{< /notice >}}

2.可以点进去查日志，来自行排查问题。

![](images/action2.jpg)

![](images/action3.jpg)

## 问题解答

1. 为什么有的书没有同步过来

> 本项目只会同步划线或者做了笔记的书，书架里的书如果没有划线或者做笔记是不会同步的。后续可能会考虑增加同步书架中的书。

2. 每天何时同步

> 本项目设置的是utc时间的0点，如果你在中国，那就是每天8点同步。不过据我观察，Github这个可能有延迟，会在每天8点零几分同步。你也可以自行修改同步时间，具体参考[这里](https://docs.github.com/zh/actions/using-workflows/events-that-trigger-workflows#schedule)。

3. 如何手动同步

> 打开你Fork的项目，依次点击Actions->weread sync-> Run workflow
![](images/run.jpg)

## 升级

打开你Fork的项目，点击Sync fork进行同步
![](https://docs.github.com/assets/cb-75616/mw-1440/images/help/repository/sync-fork-dropdown.webp)

当然你也可以上面使用中提到的步骤重新来一遍。