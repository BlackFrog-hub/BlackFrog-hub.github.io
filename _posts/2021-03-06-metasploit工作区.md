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

- 启动metasploit `msfconsole`

![](http://blackfrog.top/img/msf_workspaces_1.png)

- 查看数据库是否连接 `db_status`

![](http://blackfrog.top/img/msf_workspaces_2.png)


- 创建工作区 `workspaces -a name`

![](http://blackfrog.top/img/msf_workspaces_3.png)


- 查看工作区   `workspaces -v`
![](http://blackfrog.top/img/msf_workspaces_4.png)


- 切换工作区 `workspaces name`

![](http://blackfrog.top/img/msf_workspaces_5.png)


- 重命名工作区 `workspaces -r newname oldname`

![](http://blackfrog.top/img/msf_bg_5.png)


- 删除工作区  `workspaces -d name`   

![](http://blackfrog.top/img/msf_bg_3.png)
- 删除所有工作区  `workspaces -D`
