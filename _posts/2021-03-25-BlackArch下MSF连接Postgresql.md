---
layout:     post
title:      BlackArch下MSF连接Postgresql
subtitle:   BlackArch下MSF连接Postgresql
date:       2021-03-25
author:     BlackFrog-hub
header-img: img/blackarch_bg_1.jpg
catalog: true
tags:
    - msf
    - BlackArch
    - linux
      
---

##### `db_status`查看`postgresql`连接状态,发现没有连接,主要是没有对其进行初始化
![](http://blackfrog.top/img/blackarch_msf_connected_1.png)
##### 首先查看是否安装`postgresql`，发现没有`postgresql`
![](http://blackfrog.top/img/blackarch_msf_connected_2.png)
##### 查看`postgres`
![](http://blackfrog.top/img/blackarch_msf_connected_3.png)
##### 执行`sudo pacman -S postgresql`安装`postgresql`
![](http://blackfrog.top/img/blackarch_msf_connected_4.png)
##### 执行`sudo systemctl enable postgresql.service`启动`postgresql.service`
![](http://blackfrog.top/img/blackarch_msf_connected_5.png)
##### 使用数据库初始化工具`msfdb_blackarch`执行`sudo msfdb_blackarch run`进行数据库的启动，`msfdb_blackarch`更像是`BlackArch`的定制版
![](http://blackfrog.top/img/blackarch_msf_connected_6.png)
##### 再次查看数据库连接状态`db_status`发现成功连接上了`postgresql`数据库
![](http://blackfrog.top/img/blackarch_msf_connected_7.png)
