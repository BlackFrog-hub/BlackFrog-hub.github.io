---
layout:     post
title:      metasploit工作区使用及主机扫描
subtitle:   metasploit工作区及主机扫描
date:       2021-03-06
author:     BlackFrog
header-img: img/msf_workspaces_bg.png
catalog: true
tags:
    - kali
    - metasploit
---

### metasploit工作区使用

- 启动metasploit `msfconsole` 查看数据库是否连接 `db_status`

![](http://blackfrog.top/img/msf_workspaces_1.png)


- 创建工作区 `workspaces -a name` 切换工作区 `workspaces name` 查看工作区 `workspaces -v`

![](http://blackfrog.top/img/msf_workspaces_2.png) 


- 重命名工作区 `workspaces -r newname oldname`

![](http://blackfrog.top/img/msf_workspaces_3.png)


- 删除工作区  `workspaces -d name`   

![](http://blackfrog.top/img/msf_workspaces_4.png)


- 删除所有工作区  `workspaces -D` 

![](http://blackfrog.top/img/msf_workspaces_5.png)

### metasploit主机扫描

- 启动metasploit并创建工作区
![](http://blackfrog.top/img/msf_workspaces_6.png)

- 启动db_nmap扫描主机
![](http://blackfrog.top/img/msf_workspaces_7.png)

- 扫描结束
![](http://blackfrog.top/img/msf_workspaces_8.png)

- 获取主机ip
![](http://blackfrog.top/img/msf_workspaces_9.png)

- 分析目标主机，如果出现漏洞会列出相应的漏洞利用模块
![](http://blackfrog.top/img/msf_workspaces_10.png)
