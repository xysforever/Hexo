---
title: 使用 Hexo + Github 搭建个人博客
date: 2019-07-11 23:51:25
tags: hexo + github
---

应某位大佬吩咐，在这里讲解下如何使用 Hexo + Github 来搭建个人的博客。

<!-- more -->

## 开篇先给大家放一张我的博客的效果图吧

{% asset_img hexo全图.png %}

## 准备篇

要安装的环境及使用的软件

git、 node.js、 Hexo

这里我使用的是 Visual Studio Code(下面简称 vscode)，不得不说这是一款十分强大的编辑器。当然了，采用什么编写不限制，我这里的话只介绍 vscode 的用法。

## 1. Github 的简介及配置

在 [前一篇文章](https://xysforever.github.io/2019/07/11/git-%E5%92%8C-github-%E7%9A%84%E5%8C%BA%E5%88%AB%E5%8F%8A%E5%AE%89%E8%A3%85/ "git 和 github 的区别及安装") 中也介绍了 Github 是全球最大的同性交友网站，具体请看前一篇介绍。

在这里呢，我们采用了 Github 来作为我们的代码管理仓库，不仅因为他是免费的，而且因为其有 ***Github Page*** 这个特别牛叉的功能，就是给每个人都提供了一个域名。在这个特定的仓库里，我们可以使用特定的域名来访问此项目，为本篇文章的实现打下了基础。

首先，我们得先注册一个 Github 的账号。 [点击前往](https://github.com/ "注册 Github 的账号")

Github 的注册页面如下图所示。

{% asset_img github注册.jpg %}

然后就是填写用户名，密码了。这里的用户名千万不要随便填，以后的域名就是以它开头的，并且它是唯一的，不能与其他的重复。

这里有注意点，注册填完用户名后，会让你选择账户类型，就是选择是否收费，选择 ￥0 就好了。然后邮箱一定要真实，要验证的。第三步的选择随便选选就行了。注册完成后就进入到了主页面，样式如下图所示。

{% asset_img  注册完成并创建项目.png %}

选择最中间的 *Start a Project*，然后就会进入如下界面。

{% asset_img 创建域名访问项目.png %}

项目的格式为 ***用户名.github.io*** ，就是之前让你们好好起的用户名。这个仓库是规定的，只能这样。然后就是配置 SSH 公钥了，具体的话参照简书的这篇 [Git安装及SSH Key管理之Windows篇](https://www.jianshu.com/p/a3b4f61d4747 "点击前往") 进行配置。

到此， Github 的配置就到这了。

## 2. 安装 Node.js

那么什么是 Node.js 呢？

> Node.js 是一个基于Chrome V8 引擎的JavaScript 运行环境。Node.js 使用了一个事件驱动、非阻塞式I/O 的模型，使其轻量又高效。

安装的话就是直接去 [官网](https://www.jianshu.com/p/189fd945f38f "点击前往") 下载，或者直接 [点击下载](https://nodejs.org/dist/v10.16.0/node-v10.16.0-x64.msi "点击下载") ，这里下载的是 *10.16.0长期支持版*，最新版是 *12.6.0*，之所以不选择最新版，就是因为最新版不一定会有什么样的问题，用长期支持版比较省心。安装也十分简单，只要双击即可安装。

安装完需要检验是否安装完成，只需要打开 Git Bash，然后输入 `node --version` 即可校验，安装成功即会显示其版本号，如下图所示。

{% asset_img node版本.png %}

到这里 node.js 就安装成功了。

## 3. 安装 Hexo

打开 Git Bash ，输入命令 `npm install -g hexo-cli` ,然后等待安装结果即可。最后就是校验 Hexo 是否安装成功，在 Git Bash 中输入命令 `hexo --version` ，安装成功就会显示如下界面。

{% asset_img hexo版本.png%}

Hexo 的安装到此为止了。

## 4. 搭建博客开始

新建一个文件夹，名字随便了（我这里就叫 ***kbxmn***），然后进入，右键选择 *Git Bash Here*，如下图。

{% asset_img hexo新建项目.png %}

然后使用 `hexo init` 命令，进行初始化 hexo 项目，然后使用 `ls` 来查看文件里有什么东西，效果如下图所示。

{% asset_img 初始化hexo.png %}

这里边只需要在主目录下的 ***_config.yml*** ，具体如下

``` text
# Site
title: 苦逼小码农的博客    // 网站名称
author: 苦逼小码农        // 作者

deploy:
  type: git              // 部署的类型为 git
  repo: git@github.com:kbxmn/kbxmn.github.io.git //地址
```

这样简单的部署就完成了。然后安装 hexo-deployer-git 自动部署发布工具，使用命令 `npm install hexo-deployer-git  --save` 。

使用 `hexo clean && hexo g && hexo s` ，可以使用 `localhost:4000` 即可在浏览器中预览。然后想要推送到 Github 仓库，需要使用 `hexo clean && hexo g && hexo d`。

最后，可以在浏览器中使用 GitHub 仓库的名称访问了，即我的就是 `kbxmn.github.io`。
