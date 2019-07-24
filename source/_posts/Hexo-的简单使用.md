---
title: Hexo 的简单使用
date: 2019-07-15 15:14:43
tags:
---

这篇文章主要介绍下 Hexo 的简单使用。

<!-- more -->

## Hexo 更换主题

首先，如果按照我的上一篇文章安装成功的话，就会发现你们搭建出来的样子跟我的不一样，别着急，且听我慢慢讲来。

这是由于我更换了主题引起的，我修改了 Hexo 的默认主题 *landscape* ，我采用的是 *cyanstyle* 主题，也就是上一期的效果图。如果想要使用我的那款主题的话，需要在当前项目的主目录下打开 **Git Bash** 执行以下命令。

``` bash
git clone https://github.com/wizardforcel/hexo-theme-cyanstyle.git themes/cyanstyle
```

等待完成后，就会发现在 *theme* 的文件夹下多出来一个文件夹，如下图。

{% asset_img 下载主题.png %}

然后修改主目录下的 *_config.yml* 文件，将 *theme* 的值从 *landscape* 改成 *cyanstyle*，具体如下图所示。

{% asset_img 修改主题.png %}

然后使用命令 `hexo clean && hexo g && hexo s` 后，即可在本地查看主题了。当然了， Hexo 的主题特别多，想要体验的不同的主题的话， [点击这里](https://hexo.io/themes/index.html) 跳转到 Hexo 的主题网站，里边有很多的主题，总有一款适合你。

## Hexo 插入图片

Hexo 是支持 Markdown 的，具体什么是 Markdown 呢？

``` text
Markdown是一种轻量级标记语言，创始人为约翰·格鲁伯（英语：John Gruber）。它允许人们“使用易读易写的纯文本格式编写文档，然后转换成有效的XHTML（或者HTML）文档”。这种语言吸收了很多在电子邮件中已有的纯文本标记的特性。

由于Markdown的轻量化、易读易写特性，并且对于图片，图表、数学式都有支持，当前许多网站都广泛使用 Markdown 来撰写帮助文档或是用于论坛上发表消息。例如：GitHub、reddit、Diaspora、Stack Exchange、OpenStreetMap 、SourceForge等。甚至Markdown能被使用来撰写电子书。--引自维基百科
```

笔者的文章就是用 Markdown 编写的， Markdown 很容易的就让人写出格式十分漂亮的文本。当然了，由于编辑器的不同，有些语法还是有些不一样的，但是大部分的语法 Hexo 与其他的编辑器是相同的，这里介绍的就是插入图片。

首先，在 ***_config.yml*** 配置文件中，将 ***post_asset_folder*** 的值从 *false* 改成 *true* 。然后在终端中输入 `hexo new 文件名` 命令；就会发现在 ***_posts*** 文件夹下新建两个东西，一个是 *.md* 文件，一个是文件夹，命名都是你命令中的文件名。然后将要插入的图片放在文件夹下，比如叫做 *test.jpg* ，然后在要插入图片的地方加入以下命令。

``` bash
{% asset_img test.jpg %}
```

这样的话就会发现图片在 Markdown 编辑器中并没有显示出来，这是因为这是 Hexo 对于 Markdown 的一些修改，在其他编辑器是不承认的，想要看效果，那就在浏览器中查看，使用命令 `hexo clean && hexo g && hexo s` ，然后在浏览器中使用 `localhost:4000` 来查看效果。

## 关于首页文章内容的简介

具体的就是下图的标记区域。

{% asset_img 简介.png %}

要实现的话，其实很简单，只需要在开头的时候在在文章的标题 ***---*** 下面写上文章的简介，然后结尾加上 `<!-- more -->` 即可。具体如下图。

{% asset_img 实现简介.png %}

## 关于编辑器的使用

个人建议使用 ***Visual Studio Code*** 这款软件，之间的文章也介绍过，这里讲的是其关于 Markdown 的插件 ***markdownlint*** ，这款插件会时刻提醒你的格式有哪些不规范，该怎么改正都有相应的要求，可以尝试下。具体的安装方法就是在 *vscode* 的 **拓展** 中输入 ***markdownlint*** ，然后找到与其一致的，点击安装即可。
