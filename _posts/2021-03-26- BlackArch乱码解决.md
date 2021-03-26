---
layout:     post
title:      BlackArch乱码解决
subtitle:   BlackArch下乱码问题解决
date:       2021-03-26
author:     BlackFrog-hub
header-img: img/blackarch_bg_1.jpg
catalog: true
tags:
    - linux
    - BlackArch
      
---

#####  当我打开浏览器时出现了......
![](http://blackfrog.top/img/blackarch_luanma_1.png)
##### 安装中文字体`sudo pacman -S ttf-dejavu wqy-microhei wqy-zenhei`
![](http://blackfrog.top/img/blackarch_luanma_2.png)
##### 编辑`etc/locale.gen`将`zh_CN.UTF-8`前面的`#`去掉
![](http://blackfrog.top/img/blackarch_luanma_3.png)
##### 执行`sudo locale-gen`写入配置文件并生效
![](http://blackfrog.top/img/blackarch_luanma_4.png)
##### `locale -a` & `locale`查看当前的语言系统是否已经有`zh_CN.UTF-8`
![](http://blackfrog.top/img/blackarch_luanma_5.png)
##### 重新打开浏览器乱码问题解决
![](http://blackfrog.top/img/blackarch_luanma_6.png)
