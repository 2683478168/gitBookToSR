# GitBook 的安装

## GitBook 简介

* gitbook的官网
* gitbook文档

## gitbook的准备工作

### 安装node.js

GitBook 是一个基于 Node.js 的命令行工具，下载安装[Node.js](https://nodejs.org/en/)，安装完成之后，你可以使用下面的命令来检验是否安装成功。

我安装的是版本是 V10.15.1。这里附带[安装node.js](https://www.cnblogs.com/fanyx/p/6946039.html)的教程，

```
D:\>node -v
v10.15.1
```

![](/assets/import.png)

### 安装 GitBook

输入下面的命令来安装 GitBook。因为是要下载gitbook文件的，所以可能需要等待几分钟

```
$ npm install gitbook-cli -g
```

安装完成之后，你可以使用下面的命令来检验是否安装成功。

```
D:\>gitbook -V
```

![](/assets/gitbook-V.png)

更多详情请参照[GitBook 安装文档](https://github.com/GitbookIO/gitbook/blob/master/docs/setup.md)来安装 GitBook。

### 安装 GitBook 编辑器

去[Gitbook editor官方下载页面](https://legacy.gitbook.com/editor)下载Gitbook编辑器

在这里贴上一个网上的[editor的使用教程](https://blog.csdn.net/sb985/article/details/82252540)，虽然是Linux环境下的，但是软件的使用方法应该是相同的

# 开始使用

在使用之前，我先贴上几个常用的gitbook命令

```
gitbook init  # 生成book

gitbook install ./  # 安装gitbook 插件

gitbook build   # 生成静态网页

gitbook serve   # 生成网页，开启服务器
```

### gitbook init命令

进入一个你要写书的目录，输入gitbook init。

可以看到他会创建 README.md 和 SUMMARY.md 这两个文件。

![](/assets/gitbook-init.png)

README.md 应该不陌生，就是说明文档，而 SUMMARY.md 其实就是书的章节目录，其默认内容如下所示：

![](/assets/SUMMARY.png)

### gitbook install ./命令

这个命令一般都是在book.json中添加新的插件之后，安装插件使用的，如果你在添加插件之后没有下载该插件，在生成网页以及发布服务器的时候会报错，找不到该插件的内容、命令执行后的效果如下：

![](/assets/install.png)

### gitbook build命令

输入gitbook后会在本地生成静态网页 文件夹的名称为\_book ，这个时候gitbook的文件目录结构如下

![](/assets/gitbook-build.png)

### gitbook serve命令

接下来，我们输入`gitbook serve`命令，然后在浏览器地址栏中输入`http://localhost:4000`便可预览书籍。

![](/assets/gitbook-serve.png)

浏览器访问时的界面

![](/assets/localhost.png)做到这里就意味着你的第一本gitbook已经创建完成的，并且你已经成功的将自己的gitbook发布成功了

下面我们来详细介绍下 GitBook 目录结构及相关文件。

## 目录结构

GitBook 基本的目录结构如下所示：

![](/assets/TOC.png)

下面我们主要来讲讲比较重要的两个文件 book.json 和 SUMMARY.md 文件。

### book.json

该文件主要用来存放配置信息，我先放出我的配置文件。（book.json文件需要我们自己手动去创建）

```
{
    "title": "商软培训文档",
    "author": "lt",
    "description": "select * from learn",
    "language": "zh-hans",
    "gitbook": "3.2.3",
    "root": ".",
    "styles": {
        "website": "./styles/website.css"
    },
    "structure": {
        "readme": "README.md"
    },
    "links": {
        "sidebar": {
          "3C网店宝": "http://www.3cerp.com/"
        }
    },
    "plugins": [
        "-sharing",
        "splitter",
        "theme-comscore",
        "expandable-chapters-small",
        "anchors",
        "anchor-navigation-ex",
        "favicon",
        "tbfed-pagefooter",
        "iframely"
    ],
    "pluginsConfig": {
        "theme-default": {
            "showLevel": false
        },
        "anchor-navigation-ex": {
            "showLevel": false
        },
         "tbfed-pagefooter": {
            "copyright": "Copyright © 南京商软 2019",
            "modify_label": "该文件修订时间：",
            "modify_format": "YYYY-MM-DD HH:mm:ss"
        }
    }
}
```

相信很多节点自己也能猜到是什么意思，我还是简单介绍下吧。

#### title

本书标题

#### author

本书作者

#### description

本书描述

#### language

本书语言，中文设置 "zh-hans" 即可

#### gitbook

指定使用的 GitBook 版本

#### styles

自定义页面样式

#### structure

指定 Readme、Summary、Glossary 和 Languages 对应的文件名

#### links

在左侧导航栏添加链接信息

#### plugins

配置使用的插件

这里我放上[gitbook plugins官网](https://plugins.gitbook.com/plugin)，需要的插件可以到这里去寻找

使用插件的话，在生成网页或者发布服务器的时候需要使用 gitbook install ./ 命令将插件安装一下

#### pluginsConfig

配置插件的属性

插件的属性一般都是在gitbook plugins网站中该插件的使用说明下面

### SUMMARY.md

这个文件主要决定 GitBook 的章节目录，它通过 Markdown 中的列表语法来表示文件的父子关系，下面是一个简单的示例：

![](/assets/summaryMd.png)

这个目录对应的目录结构为：![](/assets/TOC_localhost.png)

## 插件

GitBook 有[插件官网](https://link.jianshu.com/?t=https%3A%2F%2Fplugins.gitbook.com%2F)，默认带有 5 个插件，highlight、search、sharing、font-settings、livereload，如果要去除自带的插件， 可以在插件名称前面加`-`，比如：

```
"plugins": [
    "-search"
]
```

如果要配置使用的插件可以在 book.json 文件中加入即可，比如我们添加[anchor-navigation-ex](https://plugins.gitbook.com/plugin/anchor-navigation-ex)，我们在 book.json 中加入配置如下即可：

```
"anchor-navigation-ex": {
    "showLevel": false
}
```

如果要指定插件的版本可以使用 plugin@0.3.1，因为一些插件可能不会随着 GitBook 版本的升级而升级。

## 结束

以上就是我最近一段时间内针对gitbook学习的一点点心得，当然gitbook还有很多其他的功能，这就需要自己去深入的学习了！

最后我在附上一个[gitbook与GitHub仓库关联](https://segmentfault.com/a/1190000011440899)的帖子，这个是我认为与GitHub关联最简单的一个方式，至于其他的方式还是要靠自己去学习

