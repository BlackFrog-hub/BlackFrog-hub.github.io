---

layout: post

title:  linux安装redis

subtitle: 基于centos7的redis的安装 

date: 2021-03-09

author: BlackFrog-hub

header-img: img/redis_bg.png

catalog:  true

tags:
  - Linux
  - centos
  - redis
  
---

- 首先下载`redis`归档压缩包 `wget http://doenload.redis.io/releases/redis-5.0.4.tar.gz`
![](http://blackfrog.top/img/redis_install_1.png)
![](http://blackfrog.top/img/redis_install_2.png)
- 第二步解压缩 `gunzip redis-5.0.4.tar.gz `
![](http://blackfrog.top/img/redis_install_3.png)
- 接下来解归档 `tar -xvf redis-5.0.4.tar `
![](http://blackfrog.top/img/redis_install_4.png)
- 进入`redis`目录进行源码构建安装 `make && make install`
![](http://blackfrog.top/img/redis_install_5.png)
![](http://blackfrog.top/img/redis_install_6.png)
- 安装完成。查看版本信息`redis-server --version` `redis-sentinel --version`，出现如下结果，说明已经安装成功
![](http://blackfrog.top/img/redis_install_7.png)
- 接下来启动`redis` ,`redis-server` 
![](http://blackfrog.top/img/redis_install_8.png)
- 因为使用`redis-server`启动在前台，所以会占用当前终端，所以我们将服务启动到后台，，使用命令` redis-server &`
![](http://blackfrog.top/img/redis_install_9.png)
- 查看是否启动成功和查看进程
![](http://blackfrog.top/img/redis_install_10.png)
- 使用`jobs`命令查看后台服务
- 当我们想将后台服务转到前台可以使用`fg + %number`,这里`redis-server`前面数字为`1`,所以使用`fg %1`
![](http://blackfrog.top/img/redis_install_11.png)
- 当需要将服务转到后台时可以使用`ctrl + z`,但是这样做会停止服务，所以我们可以使用`bg %1`将服务转到后台
![](http://blackfrog.top/img/redis_install_12.png)
- 停止`redis`服务可以使用`ctrl + c` & `kill`命令 & `redis-cli`执行`shutdown`
![](http://blackfrog.top/img/redis_install_13.png)
- 给`redis-server`设置口令 `redis-server --requirepass  root` 这里我将口令设置为`root`
![](http://blackfrog.top/img/redis_install_14.png)
- 此时再次查看`redis`服务发现已经存在口令，再次执行`redis-cli` and `shutdown`无法关闭服务，说明口令生效
![](http://blackfrog.top/img/redis_install_15.png)
- 当我们正确的输入刚刚设置的口令 `auto root` ,执行`ping`响应`pong`再执行`shutdown`成功关闭服务
![](http://blackfrog.top/img/redis_install_16.png)

