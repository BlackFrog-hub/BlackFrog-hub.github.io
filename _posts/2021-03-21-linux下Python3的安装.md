---
layout:     post
title:      linux源码构建安装Python3
subtitle:   centos7下Python3.7的安装
date:       2021-03-21
author:     BlackFrog-hub
header-img: img/Python_install_bg.jpg
catalog: true
tags:
    - linux
    - python
      
---
#### 源代码构建安装Python3
##### 下载源码
- 解压缩`gunzip`
- 解归档`tar -xvf`
![](http://black.top/img/python_install_1.png)
##### 查看是否有gcc `gcc --version`
![](http://black.top/img/python_install_2.png)
##### 补充安装依赖库
- `yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel libffi-devel`
![](http://black.top/img/python_install_3.png)
##### 进入Python目录执行`./configure --prefix=/usr/local/python37 --enable-optimizations`  将Python3安装到指定路径 启用优化
![](http://black.top/img/python_install_4.png)
##### 安装 `make && make install`
![](http://black.top/img/python_install_5.png)
##### 查看python3提示未找到，接下来配置path变量编辑`.bash_profile`
![](http://black.top/img/python_install_7.png)
##### 添加Python3环境变量
![](http://black.top/img/python_install_8.png)
###### 激活配置
![](http://black.top/img/python_install_9.png)
##### 查看版本，出现版本信息说明安装成功
![](http://black.top/img/python_install_6.png)
##### 创建vim配置文件
![](http://black.top/img/python_install_12.png)
##### 创建一个Python测试文件
![](http://black.top/img/python_install_10.png)
##### 运行成功
![](http://black.top/img/python_install_11.png)

