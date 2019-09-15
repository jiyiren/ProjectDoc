<p>
    <a href="https://jiyiren.github.io/"><img alt="logo" width="40" height="40" src="http://img.godjiyi.cn/jiyiheaderh-icon.png" alt="jiyiren">
    </a>
</p>

<p align="center" style="font-size: 2em">
    必备插件说明
</p>

<p align="center" style="font-size: 16px">@<a href="https://jiyiren.github.io/">JIYI</a> @<a href="https://jiyiren.github.io/">Leader</a></p>

<div align="center" style="margin: 30px 0 35px;">
<p align="center" >基于 Gitbook 的项目文档的必备插件说明</p>
</div>

基于 Gitbook 的项目文档设计本身完全基于 Gitbook，原生的 Gitbook 项目结构很简单，比较简陋。因此，**第三方插件** 的支持可以很大程度上美化文档的展示效果，比如：支持侧边栏拖动修改宽度，支持右上角**目录**，支持**代码高亮**等。我们的文档不追求如何的酷炫，而是要一目了然。无论什么项目，一个易读易懂的文档都是值得思考的。


## 目录内容

本文档包含以下内容：

- [基本环境](#基本环境)
	- [安装 Nodejs](安装-nodejs)
	- [安装 gitbook](安装-gitbook)
	- [使用 gitbook](使用-gitbook) 
- [项目结构](#项目结构)
	- [基本结构](#基本结构)
	- [简单示例](#简单示例)
- [必备插件](#必备插件)
	- [splitter](#splitter)
	- [simple-page-toc](#simple-page-toc)
	- [search-plus](#search-plus)
	- [tbfed-pagefooter](#tbfed-pagefooter)
	- [anchor-navigation-ex](#anchor-navigation-ex)
- [参考](#参考)

# 基本环境

## 安装 Nodejs
	
* 全球官网：[https://nodejs.org/en](https://nodejs.org/en)
* 中文官网：[http://nodejs.cn/](http://nodejs.cn/)
	
下载安装后测试下 Node 是否安装成功：
	
```bash
$ node -v
v10.15.3
```
	
如果提示命令没找到，那么是由于 Node 没有加入环境变量，大家将安装的 Node 环境地址放在环境变量里就可以了。

## 安装 gitbook

直接输入命令进行安装：
	
```bash
$ npm install gitbook-cli -g
```
	
`npm` 也是和 `node` 一起安装的，`node` 存在 `npm` 就存在。`-g` 参数表示全局安装，也就是模块包会安装到全局环境里，这个是推荐做法，因为像这种工具命令全局安装是最好的。而项目依赖模块则项目内安装即可。
	
测试 gitbook 命令是否安装成功：
	
```bash
$ gitbook -V
CLI version: 2.3.2
GitBook version: 3.2.3
```

## 使用 gitbook
	
任意找一个空目录，执行：
	
```bash
$ gitbook init
warn: no summary file in this book 
info: create README.md 
info: create SUMMARY.md 
info: initialization is finished 
```
	
会在当前目录下创建出两个文件，分别是：
	
```
README.md
SUMMARY.md
```
	
暂且先不管其他的，我们现在可以直接运行试试，先把流程走通：
	
```bash
$ gitbook build
$ gitbook serve
```
	
上面的 `gitbook build` 是编译整个 `markdown` 文件，然后在当前目录生成 `_book` 目录，里面是 html 页面。这个主要在部署的时候用到。
	
而 `gitbook serve` 是本地调试开启服务命令，项目最终是要成网站的，因此, 该命令可以开启本地 `http://127.0.0.1:4000` 地址作为网站浏览地址。
	
假如大家执行 `gitbook serve` 出错，建议大家先 `gitbook build` 在 `gitbook serve`.
	

# 项目结构


## 基本结构

我们上面通过 `gitbook init` 生成的只有下面两个文件：

```
README.md
SUMMARY.md
```

但实际上我们要定制我们的 gitbook 项目，项目还有一个配置文件的: **book.json**，只不过 `gitbook init` 没有自动创建出来。我们一看这文件名就应该知道这个配置文件就是 `json` 格式的。最基本的 **book.json** 长什么样子呢？如下所示：

```json
{
  "title": "ProjectDoc",
  "author": "jiyiren",
  "description": "ProjectDoc",
  "language": "zh-hans",
  "links": {
  },
  "styles": {
  },
  "plugins": [
  ],
  "pluginsConfig": {
  }
}
```

基本 book.json 内容：

* **title**: 网站标题;
* **author**: 网站作者;
* **description**: 网站描述;
* **language**: 网站语言;
* **links**: 侧边栏配置项;
* **styles**: 全局自定义网站样式;
* **plugins**: 插件配置项;
* **pluginsConfig**: 配置插件的配置项，为一些插件传入参数的;

## 简单示例

上面最基本的 **book.json**，对默认界面基本无变动，其界面显示为：

![](http://img.godjiyi.cn/jy_projectddocbasic.jpg)

我们来一个简单 gitbook 定制，**book.json** 如下：

```json
{
	"title": "ProjectDoc",
	"author": "jiyiren",
	"description": "ProjectDoc",
	"language": "zh-hans",
	"links": {
	  "sidebar": {
	    "本文托管": "https://github.com/jiyiren/ProjectDoc"
	  }
	},
	"styles": {
	},
	"plugins": [
	    "anchor-navigation-ex@0.1.8"
	],
	"pluginsConfig": {
	    "anchor-navigation-ex": {
	        "isRewritePageTitle": true,
	        "isShowTocTitleIcon": true,
	        "tocLevel1Icon": "fa fa-hand-o-right",
	        "tocLevel2Icon": "fa fa-hand-o-right",
	        "tocLevel3Icon": "fa fa-hand-o-right"
	    }
	}
}
```

其界面为如下，多出左侧栏 **本文托管**，和文章右侧的 **目录以及回到开头** 按钮。

![](http://img.godjiyi.cn/jy_projectdocselfdefine.jpg)

# 必备插件

插件使用

* 插件添加：插件的使用就放在 **book.json** 的 **plugins** 和 **pluginsConfig** 键中，形式如：`pluginName@versionName` 也就是**插件名@版本**，当然没有版本时，采用最新默认版本。

* 插件删除：要删除自带的插件则使用 `-pluginName` 即 **-插件名**

下面介绍本文档使用到的插件。

## splitter

使侧边栏的宽度可以自由调节

```json
"plugins": [
    "splitter"
]
```

## simple-page-toc

文章页面右上角显示目录，这个目前已经被废弃，建议每个页面自己生成 md 目录。

```json
{
    "plugins" : [
        "simple-page-toc"
    ],
    "pluginsConfig": {
        "simple-page-toc": {
            "maxDepth": 3,
            "skipFirstH1": true
        }
    }
}
```

## search-plus

支持中文搜索, 需要将默认的 search 和 lunr 插件去掉

```json
{
    "plugins": ["-lunr", "-search", "search-plus"]
}
```

## tbfed-pagefooter

为页面添加页脚

```json
"plugins": [
   "tbfed-pagefooter"
],
"pluginsConfig": {
    "tbfed-pagefooter": {
        "copyright":"Copyright &copy zhangjikai.com 2017",
        "modify_label": "该文件修订时间：",
        "modify_format": "YYYY-MM-DD HH:mm:ss"
    }
}
```

## anchor-navigation-ex

添加Toc到侧边悬浮导航以及回到顶部按钮，这个自动生成的悬浮目录必须以下面形式书写，也就是一定要有一个是 **h1** 开头的，否则不能识别。

```
# h1
## h2
### h3
```

配置代码：

```json
{
    "plugins": [
        "anchor-navigation-ex"
    ],
    "pluginsConfig": {
        "anchor-navigation-ex": {
            "isRewritePageTitle": true,
            "isShowTocTitleIcon": true,
            "tocLevel1Icon": "fa fa-hand-o-right",
            "tocLevel2Icon": "fa fa-hand-o-right",
            "tocLevel3Icon": "fa fa-hand-o-right"
        }
    }
}
```

## prism

使用 `Prism.js` 为语法添加高亮显示，需要将 `highlight` 插件去掉。该插件自带的主题样式较少，可以再安装 `prism-themes` 插件，里面多提供了几种样式，具体的样式可以参考 [这里](https://github.com/PrismJS/prism-themes)，在设置样式时要注意设置 css 文件名，而不是样式名。

```json
{
"plugins": [
    "-highlight",
    "prism@^2.1.0",
    "prism-themes@^0.0.2"
  ],
"pluginsConfig": {
	"prism": {
      "css": [
        "prism-themes/themes/prism-a11y-dark.css"
      ]
    }
  }
}
```

其他插件大家可以参考这个博主的：[http://gitbook.zhangjikai.com/plugins.html](http://gitbook.zhangjikai.com/plugins.html)

# 参考
1. [https://redis.io/](https://redis.io/)
2. [https://jiyiren.github.io/2018/08/04/kafka/](https://jiyiren.github.io/2018/08/04/kafka/)
