---
title: "WeRead2Notion-Pro使用文档"
description: 
date: 2024-01-03T15:28:05+08:00
image: https://images.malinkang.com/2024/03/19dd1580dd991c7985abea7724c87043.png
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



{{< notice warning >}} 
Weread2Notion和Weread2Notion-Pro是两个不同的项目，模板也不相同，切勿用错模板。

* Weread2Notion教程：[https://malinkang.com/posts/weread2notion/](https://malinkang.com/posts/weread2notion/)
* 热力图使用教程：[https://malinkang.com/posts/github_heatmap/](https://malinkang.com/posts/github_heatmap/)
  {{< /notice >}}

WeRead2Notion-Pro不仅仅是将微信读书笔记同步到Notion，它是一个强大的管理系统。

WeRead2Notion和WeRead2Notion-Pro有什么区别主要有如下 

* WeRead2Notion不支持在笔记中添加自己的笔记，每次有新笔记会删除原有的笔记。WeRead2Notion-Pro支持添加自己的笔记，每次更新不会覆盖笔记。
* WeRead2Notion功能更加简洁，同步速度更快。
* WeRead2Notion-Pro支持按照年、月、周、日的阅读时长、笔记数阅读数的时间统计，支持数据可视化。所以选用哪个看个人喜好，也可以两个都用。

## 预览

![预览](https://images.malinkang.com/2024/03/f4a77735439de22884a999c6a0671162.png)

也可以打开网页版本查看效果：https://malinkang.notion.site/9a311b7413b74c8788752249edd0b256?pvs=74

下面给大家讲解一下如何使用：

### Fork工程

打开[Weread2Notion-Pro](https://github.com/malinkang/weread2notion-pro)，点击右上角的Fork（顺便点个star谢谢）

![](https://images.malinkang.com/2024/03/fc6be407e45f0e3a3067252dd2c51c73.jpg)

### 获取微信读书Cookie

1. 浏览器打开[网页版微信读书](https://weread.qq.com/)扫码登录
2. 按F12进入开发者模式，依次点网络->文档，然后选中weread.qq.com，下拉找到Cookie，复制Cookie值

{{< notice tip >}} 
如果没有内容显示，请刷新下浏览器。

建议使用Chrome浏览器，有的小伙伴使用QQ浏览器拿到的Cookie一直不能用。
{{< /notice >}}

![](https://images.malinkang.com/2024/03/2a26e0b6d2a5a3b36711e91037b837f3.jpg)

### 授权

1. 浏览器打开 https://api.notion.com/v1/oauth/authorize?client_id=f86ce456-f9cb-4cd5-8e4b-07bd9e18a8f8&response_type=code&owner=user&redirect_uri=https%3A%2F%2Fnotion-auth.malinkang.com%2Fweread2notionpro-oauth-callback

2. 然后点击Next->Allow access

![授权](https://images.malinkang.com/2024/03/6e8adeccaf9fddef746300c3458b1967.png)

![授权](https://images.malinkang.com/2024/03/9ddc65490e193f00d4f29fbeb70b24fe.png)

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

上面配置完成之后，打开你Fork的项目，依次点击Actions->weread note sync-> Run workflow，就可以运行了。

![](https://images.malinkang.com/2024/03/41ba7acfac4c8de1cfd4ee40443644b8.jpg)

以相同的方式运行read time sync。weread note sync主要用来同步书籍、笔记和划线。read time sync 用来生成热力图和同步阅读时长。

![](https://images.malinkang.com/2024/03/6534d66107f248ffa2c2381da7490659.jpg)

## 问题排查

1. 可以点击你Fork项目的Action，查看运行状态，绿色是成功，红色是失败。

![](https://images.malinkang.com/2024/03/ee23baaf257d9fa16f6f95950cd1e585.jpg)

{{< notice warning >}} 运行成功，只代表程序没有出错，不代表就一定同步数据，比如微信Cookie过期就不会报错。所以如果运行成功，Notion中没有数据的话，也可以通过下面第2步来查看日志{{< /notice >}}

2.可以点进去查日志，来自行排查问题。

![](https://images.malinkang.com/2024/03/34089868d5569f92c9138ade3ba99428.jpg)

![](https://images.malinkang.com/2024/03/27ab73fed87b15a3a55d05423bd90167.jpg)

### 问题解答

1. 如何自动运行

> Github Action提供每日定时自动运行程序的功能。之前有的朋友会问，我关了电脑会同步吗，该脚本运行在Github的服务器上，并不是运行在你的电脑上，所以你关机并不会影响程序自动运行。

2. 每天何时同步

> 笔记设置的是utc时间的0点同步，如果你在中国，那就是每天8点同步。不过据我观察，Github这个可能有延迟。时间同步是每3个小时运行一次。你也可以自行修改同步时间，具体参考[这里](https://docs.github.com/zh/actions/using-workflows/events-that-trigger-workflows#schedule)。需要注意的是Github每个月2000分钟有免费的额度，如果改的过于频繁可能会导致额度不够。

3. 模板中哪些可以修改

> Database中的Formula和Rollup类型的属性名可以修改，其他的属性名不支持修改，因为代码中是通过属性的名字来增加修改这个属性的，修改了名字程序就无法正常运行。要修改数据库的名字需要按照以下步骤。
> 依次选择Settings->Secrets and variables -> variables-> New repository variable。

具体的变量名可以参考下表中的变量名，值为你想要修改的名字。

| 变量名                  | 当前数据库的名字 |
|-----------------------|-------|
| BOOK_DATABASE_NAME    | 书架  |
| REVIEW_DATABASE_NAME  | 笔记  |
| BOOKMARK_DATABASE_NAME| 划线  |
| DAY_DATABASE_NAME     | 日    |
| WEEK_DATABASE_NAME    | 周    |
| MONTH_DATABASE_NAME   | 月    |
| YEAR_DATABASE_NAME    | 年    |
| CATEGORY_DATABASE_NAME| 分类  |
| AUTHOR_DATABASE_NAME  | 作者  |
| CHAPTER_DATABASE_NAME | 章节  |

除此之外，其他数据可以任意修改，包括页面的布局都不会影响程序运行。

4. 年月周天中的进度是什么

> 这里的进度我设置的是每天1小时，每周7小时，每月30小时，每年365小时。你可以自行修改公式设置你的进度。

5. 表中的时间是什么

> 如果这本书你读完了，时间是读完的时间，如果没有读完，就是你最后阅读的时间。表中的日，周，月，年都是根据这个时间来设置的。


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

