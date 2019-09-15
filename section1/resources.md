<p>
    <a href="https://jiyiren.github.io/"><img alt="logo" width="40" height="40" src="http://img.godjiyi.cn/jiyiheaderh-icon.png" alt="jiyiren">
    </a>
</p>

<p align="center" style="font-size: 2em">
    资源说明
</p>

<p align="center" style="font-size: 16px">@<a href="https://jiyiren.github.io/">JIYI</a> @<a href="https://jiyiren.github.io/">Leader</a></p>

<div align="center" style="margin: 30px 0 35px;">
<p align="center" >项目虚机、软件、环境资源配置说明</p>
</div>


根据自己需求，说明标题的主题内容。这里我给了一个简单示例：加里敦 **基于 Gitbook 的项目文档** 的内部资源配置。主要涉及开发测试与正式环境下资源说明。具体包含 `MySQL`、`Redis` 等数据库配置和使用说明，以及正式部署资源的申请标准，和部署注意事项。并记录主要使用的操作命令和相应的参考文档。


## 目录内容

本文档包含以下内容：

- [项目资源](#项目资源)
	- [测试环境](#测试环境)
	- [正式环境](#正式环境)
- [学习实践](#学习实践)
	- [Redis](#redis)
	- [MySQL](#mysql)
- [参考](#参考)

# 项目资源

下面为目前暂时需要的资源工具，分为测试和正式的。

`Redis` ：作为分布式任务有序队列使用，同时也作为存储任务结果的临时存储器；

`MySQL`： 作为对外提供 Web API 服务的存储器，因其索引具有加速查询性，因此适合；


## 测试环境

**Redis** :

* 类型：**Master-Slave 类型**
* 内存：**2 GB**
* Host: **my.test.redis.aaa.bbb.ccc:1234**
* 密码：*xxxxxx*

**MySQL** :

* 地址：**127.0.0.1:3306**
* 用户/密码：*username/passwd*
* 数据库：**projectdoc**

## 正式环境

**Redis** :

* 类型：**Master-Slave 类型**
* 内存：前期 **2 GB**，之后扩容为 **5 GB**
* Host: **my.formal.redis.aaa.bbb.ccc:1234**

**MySQL** :

* Host: **my.formal.mysql.aaa.bbb:3306**
* 用户/密码：*username / passwd*
* 数据库：**projectdoc**

# 学习实践

## Redis

* 官网：[https://redis.io/](https://redis.io/)
* MacOS 安装：

	```bash
	# 从官网下载软件包
	tar -zxf redis-xxx.tar.gz
	mv redis-xxx /usr/local/redis-xxx
	# 建立软链接
	ln -s /usr/local/redis-xx /usr/local/redis
	# 添加到环境变量
	export REDIS_HOME=/usr/local/redis
	```
* 启动服务：`redis-server`
* 本地连接：`redis-cli`
* 连接远程：

	```bash
	redis-cli -h [ip] -p [port] -a [pwd]
	# 例如：
	redis-cli -h 127.0.0.1 -p 1234 -a 123456
	```
* 其他操作：

   ```bash
   # 选择数据库，默认 Redis 有 16 个
   select [index]
   # 显示所有 pattern 匹配的键
   KEYS [pattern_key]
   # 显示列表长度
   LLEN [key]
   # 显示列表从 start 到 end 索引，显示所有则 end = -1
   LRANGE [key] [start] [end]
   ```

## MySQL

* 官网：[https://www.mysql.com/](https://www.mysql.com/)
* 安装：

	```bash
	wget http://repo.mysql.com/mysql57-community-release-el7-10.noarch.rpm
	rpm -Uvh mysql57-community-release-el7-10.noarch.rpm
	yum install  -y  mysql-community-server
	```
* 启动：

	```bash
	service mysqld start/stop/status
	systemctl start/stop/status mysqld.service
	```
* 其他：

	```sql
	# 修改 root 密码
	mysqladmin -u root password "newpass"
	# 配置文件：
	/etc/my.cnf
	# 允许远程登录
	GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '密码' WITH GRANT OPTION;
	```

# 参考
1. [https://redis.io/](https://redis.io/)
2. [https://www.mysql.com/](https://www.mysql.com/)
3. [https://www.cnblogs.com/alex3714/p/6351797.html](https://www.cnblogs.com/alex3714/p/6351797.html)
4. [https://www.cnblogs.com/guanfuchang/p/6561034.html](https://www.cnblogs.com/guanfuchang/p/6561034.html)
5. [https://blog.csdn.net/chenqiuge1984/article/details/80127446](https://blog.csdn.net/chenqiuge1984/article/details/80127446)
