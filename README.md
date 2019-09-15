<p>
    <a href="https://jiyiren.github.io/"><img alt="logo" width="40" height="40" src="http://img.godjiyi.cn/jiyiheaderh-icon.png" alt="jiyiren">
    </a>
</p>

<p align="center" style="font-size: 2em">
    基于 Gitbook 的项目文档设计
</p>

<p align="center" style="font-size: 16px">@<a href="https://jiyiren.github.io/">JIYI</a> @<a href="https://jiyiren.github.io/">Leader</a> @<a href="https://jiyiren.github.io/">Boss</a></p>

<p align="center" style="margin: 30px 0 35px;">基于 Gitbook 的开源生态，更具美观的项目文档库</p>


此系统主要面向于 **IT 项目开发者** 服务。作者集成了一些必要的插件以及一些规范化的写作风格，整体上以简洁、清晰为主要设计倾向。本项目基于 **Gitbook** 开源生态，具有较多开源插件、模板支持，使用性较广，问题排查方便，且可导出为 `HTML`、`PDF` 等格式传播，形式多样。也具有 `Book`、`API`、`FQA` 等多种模式形态，丰富实用。此文档基于个人审美自定义的，大家可以根据自身感觉进行重新设计扩展。公司内部文档应放在公司的 **[Gitlab](https://www.gitlab.com/)** 里，个人的可以放 **[Github](https://www.github.com/)** 中以 **Pages** 方式开放。

![](http://img.godjiyi.cn/jy_projectdocbg.jpg)

## 目录内容

本文档包含以下内容(**均是示例**)：

- [Features](#features)
- [Architecture](#architecture)
- [Running](#running)
	- [环境需求](#环境需求)
	- [执行脚本](#执行脚本)
- [Resources](#resources)
- [References](#references)


# Features
> 示例

* 基于 `Gitbook` 开源生态，多插件，多模式支持，风格清晰；
* 下面是自己扯的其他代码项目的 `Features`，仅仅作为例子；
* 基于 `Dubbo` 高性能 `RPC` 框架，提高执行效率和扩展性；
* 采用 `Redis` 构建分布式消息队列，实现非阻塞调用；
* 数据采用 `Json` 格式存储与传输，更通用且便于扩展移植；
* 模块化设计，功能抽象成函数、公共组件独立成库；

# Architecture
> 示例

<div align="center">
<img alt="logo" width="550" height="400" src="http://img.godjiyi.cn/csdnblogkafka-arc.jpg"/>
</div>


* **Topic**: 一个消息主题，也就是一个分布式消息队列名称;
* **Producer**: 生产者，可以有多个，可同时生产多个 `Topic`；
* **Partion**: 就是 `Topic` 分布式的体现：
	* 一个 `Topic` 分成多个 `Partion`；
	* 多个 `Producer` 生产消息可以并行入队；
	* 同一个 `Partion` 里保证消息有序；
* **Consumer Group**: 消费者组，这是 `Kafka` 最特别之处： 
	* 一个消费组消费一个 Topic 的全量数据；
	* 组内消费者消费一个或多个 Partion 数据；
	* 一个组里的消费者应小于等于 Topic 的 Partion 数量； 
* **架构最好配一张结构图，并将各个点概述下即可，中英文间加空格**。



# Running
> 示例

## 环境需求

下面为各个执行模块所需要的依赖包。

* 分布式 - Main Host

	```bash
	pip install mysql-connector-python	// MySQL 数据库连
	pip install DBUtils 	// 数据库连接池
	pip install redis		// Redis 数据库
	pip install flask		// Flask 以构建 Web API
	pip install simplejson	// Json 解析库
	```

* 分布式 - Slave Host：

	```bash
	pip install -r slave/requirement.txt
	```
	
* 上面主要按照自己项目的模块来，比如也可以写 Java 的 Maven 依赖；

## 执行脚本

项目主要分为 **Main Host 进程**、**Slave Host 进程**、**定时清理日志进程** 三大进程，我们分别实现了对应的启动脚本。

* Main Host：

	```bash
	./main-host-process.sh > main.log 2>&1 &
	```

* Slave Host：

	```bash
	./slave-host-process.sh > slave.log 2>&1 &
	```

* 定时清理进程：

	```bash
	crontab -f schedule.file
	```
* 说明：最好将项目都通过命令启动，这样可以规避很多操作失误。

# Resources

下面为目前暂时需要的资源工具信息：

* Kafka:
	* 地址：**xxx.aaa.bbb.xxxx** 
	* 主题：**demo1**,**demo2**

* Redis:

	* 内存：**2 GB**
	* 地址和端口：
		* Master: **xxx.aaa.bbb.cccc:1234**
		* Slaver: **xxx.aaa.bbb.dddd:1234**
	* 密码：**xxxxxxxx**


* MySQL:

	* 地址：**xxx.aaa.bbb.ccc**
	* 用户名/密码：**name/xxxx**


* 可以列出所有需要依赖的资源：
	* 如果是内部可以公开所有信息，
	* 如果不是则要注意隐私。

## References
1. [https://redis.io/](https://redis.io/)
2. [https://jiyiren.github.io/2018/08/04/kafka/](https://jiyiren.github.io/2018/08/04/kafka/)
3. [http://gitbook.zhangjikai.com/themes.html](http://gitbook.zhangjikai.com/themes.html)
4. [http://www.chengweiyang.cn/gitbook/](http://www.chengweiyang.cn/gitbook/)
5. [https://www.cnblogs.com/YangJieCheng/p/7991660.html](https://www.cnblogs.com/YangJieCheng/p/7991660.html)
