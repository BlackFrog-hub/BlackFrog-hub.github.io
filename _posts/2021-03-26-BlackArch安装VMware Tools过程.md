---
layout:     post
title:      BlackArch安装VMware Tools过程
subtitle:   BlackArch安装VMware Tools
date:       2021-03-26
author:     BlackFrog-hub
header-img: img/blackarch_bg.jpg
catalog: true
tags:
    - linux
    - blackarch
      
---

#### 这里不建议安装使用VMware Tools 因为VMware Tools对BlackArch的支持不是很好，所以我们选择使用open-vm-tools
##### 首先安装open-vm-tools`sudo pacman -S open-vm-tools`
![](http://blackfrog.top/img/blackrach_vmtools_1.png)
##### 接下来安装软件`sudo pacman -S base-devel net-tools`
![](http://blackfrog.top/img/blackrach_vmtools_2.png)
##### 启动vmtoolsd.service `sudo systemctl status vmtoolsd.service`
![](http://blackfrog.top/img/blackrach_vmtools_3.png)
##### 启用时间同步功能`sudo vmware-toolbox-cmd timesync enable` 当宿主机休眠后可以使用`sudo hwclock --hctosys --localtime`来同步时间
##### 确认`VMware`查看-自动调整大小选择了自适应
##### 我们继续安装`xf86-video-vmware`执行`sudo pacman -S xf86-video-vmware`
![](http://blackfrog.top/img/blackrach_vmtools_7.png)
##### 再安装`gtkmm`和`gtk2`执行`sudo pacman -S gtkmm gtk2`
![](http://blackfrog.top/img/blackrach_vmtools_5.png)
##### 编辑`/etc/mkinitcpio.conf`
![](http://blackfrog.top/img/blackrach_vmtools_6.png)
##### 找到MODULES=""在里面添加相关模块`vsock vmw_vsock_vmci_transport vmw_balloon vmw_vmci vmwgfx`
![](http://blackfrog.top/img/blackrach_vmtools_8.png)
##### 执行`sudo mkinitcpio -p linux`
![](http://blackfrog.top/img/blackrach_vmtools_9.png)
##### 启动`vmtoolsd`服务`sudo systemctl start vmtoolsd.service` &`sudo systemctl enable vmtoolsd.service`
![](http://blackfrog.top/img/blackrach_vmtools_10.png)
##### 现在我们可以看到可以全屏啦，如果没有效果`reboot`即可
![](http://blackfrog.top/img/blackrach_vmtools_11.png)
