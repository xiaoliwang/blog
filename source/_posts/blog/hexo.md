---
title: 使用 hexo 搭建属于你的个人博客
date: 2018-05-10 23:01:10
tags: [hexo]
comments: true
---



# 安装 hexo 及 next 主题

> [hexo](https://hexo.io/zh-cn/index.html) 是一款快速、高效的博客系统。即使你对编程毫无基础，只要你对搭建专属自己的个人博客充满好奇，你都可以在极短的时间，学习并拥有一个你的专属博客。



<!-- more -->



## 先导知识

在使用 **hexo** 搭建你的博客之前，你需要了解并学习以下知识：

### markdown

> *markdown* 是一种轻量级标记语言。当你开始使用 *markdown* 撰写博客和文档时，你一定会爱上这么轻巧可爱的语言。在时候用 **hexo** 编写博客文章时，*markdown* 永远是你的第一选择。

如果你之前从来没有学习或者了解过 *markdown* 的话，建议你可以首先学习下它的[语法](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)。他的语法非常简单易学。你只需要掌握教程的第一页，就已经完成了 *markdown* 的入门学习。如果你迫不及待的想实践你的学习内容，你可以使用包括但不限于下面列举的编辑器：

1. 桌面版编辑器 [typora](https://typora.io/)
2. 在线编辑器[作业部落](https://www.zybuluo.com/mdeditor)

当然，上面的编辑器大多都是自带教程的，并且有很多进阶内容，有兴趣的朋友可以多多尝试。



### Node.js

> Any application that can be written in *JavaScript*, will eventually be written in *JavaScript* 																	

上面这句话是著名的 *Atwood's Law*，这里揭示了 `javascript` 的火爆程度。**Node.js** 正是当今最流行的 *JavaScript* 解释器。当然，不用担心，我们这里并不涉及具体的编程；因为 **hexo** 是使用 *JavaScript* 编写，我们这里需要使用这个软件而已。首先我们需要安装这个程序。进入 [Node.js](https://nodejs.org/zh-cn/) 的官网点击下载安装即可。

对于使用 **Mac** 系统的同学可以使用 [Homebrew](https://brew.sh/) 进行安装。具体操作如下：

1. 打开你的终端(terminal)

2. 在终端中输入以下命令。

   ```shell
   # 安装 homebrew
   /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
   
   # 安装 nodejs
   brew install node
   ```

**Node.js** 安装完成后，在终端中输入 `node -v` 如果返回类似信息`v10.1.0`（因为您的版本可能和我的不一样，所以返回的数字可能略有不同），则代表安装成功。



### git

> **git** 是一个开源的分布式版本控制系统。

光从名字，你就能知道这玩意非常的伟光正。又是开源，又是分布式。当然，这个软件比较的复杂，所以不感兴趣的同学可以跳过下面的学习教程。当然，学会使用 **git**，会对大大提高你的博客管理能力。以下推荐[廖雪峰老师的 **git** 教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)，有兴趣的同学可以学习下。



## 安装 hexo

### 搭建博客系统

在学习完上面那么多内容之后，我们终于可以正式开始搭建我们的个人博客。首先打开终端。

```shell
# 安装 hexo 命令行工具
npm install hexo-cli -g

# 安装 hexo 博客代码
cd $path # 进入你想安装博客的路径
hexo init $blog_root # 创建博客目录，$blog_root 为该目录的名字
cd $blog_root
npm install
hexo server
```

这时候你可以打开浏览器访问 http://localhost:4000/ 就可以看到你的博客了 。

在开始你的第一篇博客前，我们首先了解下系统的配置文件 `_config.yml`。下面是配置文件的一个选段：

```yaml
# Site
title: 标题
subtitle:
description:
keywords:
author: John Doe # 作者
language: zh-CN # 这里可以设置成中文
timezone: Asia/Shanghai # 这里可以修改成中国时区
```

你可以尝试对上面的内容进行修改，再重启一下服务 `Ctrl+C` 并再次输入 `hexo server` 进行查看。配置文件中，`#` 开头的内容是注释，具体有对配置内容进行说明，有兴趣的朋友可以尝试阅读学习。

说了这么多，我们开始写第一篇博客。其实我们打开 `source/_posts` 目录，可以看到里面已经有一篇博客，这篇博客就是我们在页面里看到的 `Hello World`。现在我们是用 `hexo new <title>` 来生成我们的第一篇博客。这时候 `source/_posts` 中会生成一个叫 `<title>.md` 的文件。对该文件进行编辑即可。 



### 安装插件

**hexo** 支持几十上百种插件。这里是[插件列表](https://hexo.io/plugins/)。下面推荐其中的两款插件。



#### hexo-directory-category

这款[插件](https://github.com/zthxxx/hexo-directory-category)可以根据目录自动生成分类。首先用下面的命令安装该插件：

```shell
cd $blog_root
npm install --save hexo-directory-category
```

在修改配置文件 `_config.yml`。

```yaml
auto_dir_categorize:
	enable: true # Enable the plugin. Defaults to true.
	force: false # Overwrite article front-matter categories, even if it has option categories.Defaults to false.
```

这时候你将你的博客文章放入 `source/_posts/<dir>` 文件夹中时，`<dir>` 将自动生成该文章的分类。



#### hexo-renderer-markdown-it-plus

这款[插件](https://github.com/CHENXCHEN/hexo-renderer-markdown-it-plus)是用于替换 **hexo** 的默认 `markdown` 引擎。可以用于生成数学公式等。首先使用下面的命令安装插件：

```shell
npm un hexo-renderer-marked --save
npm i hexo-renderer-markdown-it-plus --save
```

需要注意的两点是，如果需要在文章中插入数学公式的话，首先需要引入 `https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.9.0/katex.min.css` 文件，并且在文章的配置添加 `mathjax: true`。下面是一个完整的配置：

```yaml
---
title: 标题
date: 2006-05-01 15:34:09
tags: [php,mysql,postgreSql]
mathjax: true
---
```



### 设置主题

**hexo** 支持超多主题。这里是[主题列表](https://hexo.io/themes/)。下面推荐我觉得最棒的主题 [next](https://theme-next.iissnan.com/)。首先当然是安装主题：

```shell
cd $blog_root

# 以下可以使用三种方式进行安装
# 1. 直接下载最新版本
mkdir themes/next
curl -L https://api.github.com/repos/iissnan/hexo-theme-next/tarball | tar -zxv -C themes/next --strip-components=1

# 2. 使用 git 获取最新版本
git clone https://github.com/iissnan/hexo-theme-next themes/next

# 3. 使用 git submodule 获取最新版本(如果项目已经用 git 进行管理)
git submodule add https://github.com/theme-next/hexo-theme-next themes/next
```

然后修改配置文件

```yaml
theme: next
```

这时候重启项目，你就可以看到最新的 **next** 主题。