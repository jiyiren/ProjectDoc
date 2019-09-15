<p>
    <a href="https://jiyiren.github.io/"><img alt="logo" width="40" height="40" src="http://img.godjiyi.cn/jiyiheaderh-icon.png" alt="jiyiren">
    </a>
</p>

<p align="center" style="font-size: 2em">
    项目结构说明
</p>

<p align="center" style="font-size: 16px">@<a href="https://jiyiren.github.io/">JIYI</a> @<a href="https://jiyiren.github.io/">Leader</a></p>


<div align="center" style="margin: 30px 0 35px;">
<p align="center" >基于 Gitbook 的项目文档目录结构说明</p>
</div>


这里主要说明本项目结构目录，既然基于 `Gitbook` 的框架的，整体上也是 Gitbook 目录结构。本项目已经全部放在 [Github 仓库](https://github.com/jiyiren/ProjectDoc) 里了，大家可以直接去看源码目录。就规范性来讲，还是按模块划分比较好一点，本页说明结构模块以及各个文件的作用。

## 目录内容

本文档包含以下内容：

- [项目目录](#项目目录)
- [配置文件](#配置文件)
	- [SUMMARY.md](#SUMMARY.md)
	- [book.json](#book.json)
- [参考](#参考)

# 项目目录

项目整体结构如下：

```
.
├── README.md
├── SUMMARY.md
├── book.json
├── _book
│   ├── _img
│   ├── gitbook
│   ├── index.html
│   ├── section1
│   ├── section2
│   ├── section3
│   └── styles
├── _img
│   ├── xxxx.png
├── section1
│   └── resources.md
├── section2
│   ├── functions.md
│   ├── modules.md
│   ├── plugins.md
│   └── scripts.md
├── section3
│   └── openimage.md
└── styles
    └── website.css
```

各个结构说明：

* **README.md**: 网站的 README，但一般很多人作为主页；
* **SUMMARY.md**: 网站结构文档，主要实现侧边栏目录导航；
* **book.json**: 整个 gitbook 项目的配置文件；
* **_book目录**: 这个是自动生成的目录，是构建出来的静态页面；
* **_img目录**: 这个是个人设定的图片等静态资源目录；
* **section1/2/3目录**: 这个是 gitbook 项目各个模块目录，里面也放置 markdown 文件。
* **styles目录**: 这个也是自己定义的，这里我是实现项目整体的主题配色。

# 配置文件

## SUMMARY.md

```markdown
# Summary

## 介绍

* [简介](README.md)
* [环境](section1/resources.md)

## 实现

* [项目结构](section2/modules.md)
* [功能划分 ★](section2/functions.md)
* [必备插件](section2/plugins.md)
* [运行脚本 ❤︎](section2/scripts.md)


## 说明

* [图库资源](section3/openimage.md)
* [无色主题]()
```

## book.json

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
    "website": "styles/website.css"
  },
  "plugins": [
    "splitter@^0.0.8",
    "-lunr",
    "-search",
    "search-plus@^0.0.11",
    "tbfed-pagefooter@^0.0.1",
    "anchor-navigation-ex@0.1.8",
    "-highlight",
    "prism@^2.1.0",
    "prism-themes@^0.0.2"
  ],
  "pluginsConfig": {
    "theme-default": {
      "showLevel": true
    },
    "tbfed-pagefooter": {
      "copyright": "Copyright &copy csyiji@gmail.com 2019",
      "modify_label": "该文件修订时间：",
      "modify_format": "YYYY-MM-DD HH:mm:ss"
    },
    "anchor-navigation-ex": {
      "isRewritePageTitle": true,
      "isShowTocTitleIcon": true,
      "tocLevel1Icon": "fa fa-hand-o-right",
      "tocLevel2Icon": "fa fa-hand-o-right",
      "tocLevel3Icon": "fa fa-hand-o-right"
    },
    "prism": {
      "css": [
        "prism-themes/themes/prism-a11y-dark.css"
      ]
    }
  },
  "pdf": {
    "pageNumbers": true,
    "fontSize": 12,
    "paperSize": "a4",
    "margin": {
      "right": 10,
      "left": 10,
      "top": 10,
      "bottom": 10
    }
  }
}
```

# 参考
1. [https://redis.io/](https://redis.io/)
2. [http://docs.celeryproject.org/en/latest/](http://docs.celeryproject.org/en/latest/)
3. [https://www.cnblogs.com/alex3714/p/6351797.html](https://www.cnblogs.com/alex3714/p/6351797.html)
4. [https://www.cnblogs.com/guanfuchang/p/6561034.html](https://www.cnblogs.com/guanfuchang/p/6561034.html)
5. [https://blog.csdn.net/chenqiuge1984/article/details/80127446](https://blog.csdn.net/chenqiuge1984/article/details/80127446)
