---
title: "WeRead2Notion使用文档"
description: 
date: 2023-09-10T15:28:05+08:00
image: https://images.malinkang.com/2024/03/e1bc45eb87ec93a249edf163a9115874.png
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

WeRead2Notion用于将微信读书的笔记自动同步到Notion。该项目不支持在Notion中添加自己的笔记，每次有笔记更新会删除原有笔记，需要添加自己的笔记可以使用[WeRead2Notion-Pro](https://malinkang.com/posts/weread2notion-pro/)。

{{< notice warning >}} 
Weread2Notion和Weread2Notion-Pro是两个不同的项目，模板也不相同，切勿用错模板。

* Weread2Notion-Pro教程：[https://malinkang.com/posts/weread2notion-pro/](https://malinkang.com/posts/weread2notion-pro/)
* 热力图使用教程：[https://malinkang.com/posts/github_heatmap/](https://malinkang.com/posts/github_heatmap/)
{{< /notice >}}

## 预览

![3e54d178-4e8d-4a06-a36d-664a861b364c](https://images.malinkang.com/2024/03/7403ee39bcd57097005697d3c4a06841.png)

也可以打开网页版本查看效果：https://book.malinkang.com/

### Fork工程

打开[Weread2Notion](https://github.com/malinkang/weread2notion)，点击右上角的Fork（顺便点个star谢谢）

![](https://images.malinkang.com/2024/03/fc6be407e45f0e3a3067252dd2c51c73.jpg)

### 权限

确保你打开了读写权限。

依次选择Settings->Actions->General，然后下拉，找到Workflow permissions，如果没有选中Read and write permissions，请选中，然后点下面的save保存。

![](https://images.malinkang.com/2024/03/01c28b0dd2e8c2629a22e7f68db6216d.jpg)


![](https://images.malinkang.com/2024/03/d7824c3488e6e1d1c9e6b75d6aba86f3.jpg)


### 获取微信读书Cookie

1. 浏览器打开[网页版微信读书](https://weread.qq.com/)扫码登录
2. 按F12进入开发者模式，依次点网络->文档，然后选中weread.qq.com，下拉找到Cookie，复制Cookie值

{{< notice tip >}} 
如果没有内容显示，请刷新下浏览器。

建议使用Chrome浏览器，有的小伙伴使用QQ浏览器拿到的Cookie一直不能用。
{{< /notice >}}

![](https://images.malinkang.com/2024/03/2a26e0b6d2a5a3b36711e91037b837f3.jpg)

### 授权

1. 浏览器打开 https://api.notion.com/v1/oauth/authorize?client_id=801fd03a-a44f-41af-9a17-feb048b4bbdd&response_type=code&owner=user&redirect_uri=https%3A%2F%2Fnotion-auth.malinkang.com%2Fweread2notion-oauth-callback

2. 然后点击Next->Allow access

![image-20240326111124731](https://images.malinkang.com/2024/03/6e8adeccaf9fddef746300c3458b1967.png)

![image-20240326111250623](https://images.malinkang.com/2024/03/9ddc65490e193f00d4f29fbeb70b24fe.png)

3. 点击复制按钮，复制NOTION_TOKEN和NOTION_PAGE的值。

   ![复制](https://images.malinkang.com/2024/03/42c04cb1e6ab95eed832f33462c96831.jpg)

### 在Github的Secrets中添加变量

1. 打开你fork的工程，点击Settings->Secrets and variables->New repository secret

![](https://images.malinkang.com/2024/03/660acb8a4038af66e27fe0f993ef3aad.jpg)

2. Name输入WEREAD_COOKIE，Secret输入框中填入你前面获取的微信读书Cookie，然后点击Add secret

![](https://images.malinkang.com/2024/03/bd1bb31f901d9920bb1135c19e1ef304.jpg)

3. 同理，继续点击New repository secret，分别增加变量NOTION_TOKEN和NOTION_PAGE。最终的结果如下图所示。

![](https://images.malinkang.com/2024/03/cc1a34e23e251dec7f8fedc8d710912a.jpg)

{{< notice warning >}} 注意这三个变量名一定要填写正确，一个字母都不能错，否则会同步失败。{{< /notice >}}

### 运行

上面配置完成之后，打开你Fork的项目，依次点击Actions->weread sync-> Run workflow，就可以运行了。

![](https://images.malinkang.com/2024/03/58a654118607156d8a7dde7f6470504f.jpg)

## 问题排查

1. 可以点击你Fork项目的Action，查看运行状态，绿色是成功，红色是失败。

![](https://images.malinkang.com/2024/03/ee23baaf257d9fa16f6f95950cd1e585.jpg)

{{< notice warning >}} 运行成功，只代表程序没有出错，不代表就一定同步数据，比如微信Cookie过期就不会报错。所以如果运行成功，Notion中没有数据的话，也可以通过下面第2步来查看日志{{< /notice >}}

2.可以点进去查日志，来自行排查问题。

![](https://images.malinkang.com/2024/03/34089868d5569f92c9138ade3ba99428.jpg)

![](https://images.malinkang.com/2024/03/27ab73fed87b15a3a55d05423bd90167.jpg)


## 问题解答

1. 为什么有的书没有同步过来

> 本项目只会同步划线或者做了笔记的书，书架里的书如果没有划线或者做笔记是不会同步的。后续可能会考虑增加同步书架中的书。

2. 每天何时同步

> 本项目设置的是utc时间的0点，如果你在中国，那就是每天8点同步。不过据我观察，Github这个可能有延迟，会在每天8点零几分同步。你也可以自行修改同步时间，具体参考[这里](https://docs.github.com/zh/actions/using-workflows/events-that-trigger-workflows#schedule)。



## 升级

如果我添加了新功能，你需要将自己的代码与我的代码进行同步。打开你Fork的项目，点击Sync fork进行同步，如果有冲突可以点击Discard那个按钮
![image-20240326113307149](https://images.malinkang.com/2024/03/53c917e4bcfd70d0509a05680a2f10b4.png)



## 捐赠

如果你觉得项目对你有帮助，可以捐赠。我也会不断的优化项目，并做出其他开源的项目。

### 微信


![](https://images.malinkang.com/2024/03/d34f577490a32d4440c8a22f57af41da.jpg)

### 支付宝

![](https://images.malinkang.com/2024/03/7fd0feb1145f19fab3821ff1d4631f85.jpg)

## 付费解答

有问题先自行解决，往往失败都是一些小细节没注意导致的。我的文档写的已经足够详细，按照文档来操作基本都能成功。你也可以尝试在群里咨询。不要直接加我微信来让我来解答，这个项目我已经投入了大量时间来开发维护，实在没有更多的精力来一对一解答。如果实在解决不了，可以付费一对一咨询，30元一位。付完款可以微信私聊我。

![](https://images.malinkang.com/2024/03/ca34d2b8c111f23126d94d3aaf55f5f3.jpg)

## 群

欢迎加入微信群讨论。使用中遇到的任何问题，包括Notion的使用，微信读书组队打卡，后续的更新都会在群里讨论。


![群](https://images.malinkang.com/group.jpg)

