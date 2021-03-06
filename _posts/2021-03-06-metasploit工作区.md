---
layout:     post
title:      metasploit工作区使用及主机扫描
subtitle:   metasploit工作区
date:       2021-03-06
author:     BlackFrog
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - kali
    - metasploit
---

### metasploit工作区使用

- 启动metasploit `msfconsole`
![]()

- 查看数据库是否连接 `db_status`

![]()

- 创建工作区 `workspaces -a name`

![]()

- 查看工作区   `workspaces -v`
![]()

- 切换工作区 `workspaces name`

![]()

- 重命名工作区 `workspaces -r newname oldname`

![]()

- 删除工作区  `workspaces -d name`    `workspaces -D`删除所有工作区
