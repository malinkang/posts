---
title: "免费为Notion绑定域名"
description: 
date: 2024-10-29T09:40:05+08:00
image: https://images.unsplash.com/photo-1729366790976-81844c8dd310?q=80&w=2970&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
math: 
license: 
hidden: false
comments: true
draft: false
tags:
    - Notion
---

前两个月Notion官方推出了可以为Notion页面绑定域名的服务，每个月需要10刀。高昂的价格应该劝退不少小伙伴，今天我就来给大家分享下我的免费方案。

![](https://images.malinkang.com/2024/10/9f4ee08847c9f36ba1ab48e744d571aa.png)

具体效果可以参考：https://book.malinkang.com/，这个方案是基于开源方案fruitionsite：https://github.com/stephenou/fruitionsite。但是代码已经3年没有更新了，很多功能已经生效。所以我复制了一份源码修改了一些bug。

## 域名注册

可以选择在腾讯云或者阿里云上或者其他平台上购买域名。

1. 腾讯云购买地址：https://buy.cloud.tencent.com/domain/。
2. 阿里云购买地址：https://wanwang.aliyun.com/


## 修改DNS信息

注册cloudflare： https://dash.cloudflare.com/，登录成功之后添加点击添加域。

![](https://images.malinkang.com/2024/09/6d247f00849fea4816b5ec8ba5f641d4.png)

输入我们购买的域名，然后点击继续。

![](https://images.malinkang.com/2024/09/3f476e2164c92e153efe6c31cc6b0f4c.png)

进入下一个页面，选择免费计划。这里免费计划在最下面，如果屏幕小的可能会看不到。

![](https://images.malinkang.com/2024/09/0f888391cc92f7c766a6b6826b6f6c46.png)

然后点击继续，会看到我们需要配置的DNS服务器。

![](https://images.malinkang.com/2024/09/b176e6958691d4c611989b2afead6574.png)

打开购买域名的网站，将你购买的域名的DNS修改为cloudflare的DNS服务器。

腾讯云修改DNS教程：https://cloud.tencent.com/document/product/302/5518#id.3Aserveraddress
阿里云修改DNS教程：https://help.aliyun.com/zh/dws/user-guide/change-dns-servers-for-a-domain-name#6a5c8962350ho

## 生成代码

打开网站：https://site.notionhub.app/

输入我们的域名和要绑定域名的Notion链接，请确保你的Notion已经发布到网络上。

![](https://images.malinkang.com/2024/10/df9d9682b43518d7f4895939e17df118.png)

如果你需要配置多个页面，比如https://malinkang.com/book，https://malinkang.com/podcast这种，点击`ADD A PRETTY LINK`添加对应的路径和NOTION链接即可。

![](https://images.malinkang.com/2024/10/6c58539c790e1a8c049bad3f1e3d964e.png)

最后可以点击`TOGGLE STYLE AND SCRIPT SETTINGS`来设置网站标题描述和字体。

![](https://images.malinkang.com/2024/10/12202920ca0a4c96fb23ee326f1957b3.png)

全部设置完成点击复制代码。

## 配置Cloudflare Worker

打开Cloudflare：https://dash.cloudflare.com/，选中Workers和Pages，然后点击创建按钮

![](https://images.malinkang.com/2024/10/6eb1d65944ffa1db51be478a42ec716a.png)

输入名字，然后点击部署

![](https://images.malinkang.com/2024/10/eaa35ec15dcb1fb692ed0f5c24c074da.png)

点击编辑代码

![](https://images.malinkang.com/2024/10/5919e6b5d3be20710b0c142e9703a65e.png)

将我们上一步生成的代码，粘贴到箭头所指的地方，然后点击部署。部署完成后点返回按钮返回。

![](https://images.malinkang.com/2024/10/145ce93397b2166100acdf4adf6986ee.png)

选中设置->域和路由，点击添加，输入我们的域名然后点击添加域即可。

![](https://images.malinkang.com/2024/10/f5a029b42c6b71dbb475094c53f4d56d.png)

![](https://images.malinkang.com/2024/10/d00a365e67a3f8444564328303dca28a.png)

欢迎加入Notion交流群，一起交流Notion使用心得。

![](https://images.malinkang.com/2024/10/fd30ce8dd93c33d3f8562b55448bab7c.png)

如果二维码失效可以添加我的个人微信，我来邀请你入群。

![](https://images.malinkang.com/2024/10/2a44bb2cdac0cbced732f09e15126c70.png)

如果你觉得文章对您有帮助，请捐赠支持一下。
