# gitbook的安装

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
    "title": "Blankj's Glory",
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





