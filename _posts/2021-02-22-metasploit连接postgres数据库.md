---
layout:     post
title:     metasploit连接postgres数据库
subtitle:   metasploit连接postgres数据库
date:       2021-02-22
author:     BlackFrog-hub
header-img: img/msf_bg.jpg
catalog: true
tags:
    - Metasploit
    - kali
    - Linux
---

#  metasploit连接postgres数据库
#### db_status检测连接状态，发现未连接
```bash
msf5 > db_status
[*] postgresql selected, no connection
```
#### postgresql一下发现没有postgresql数据库
```bash
root@kali:~# postgresql
bash: postgresql：未找到命令
```
#### 安装postgresql
```bash
root@kali:~# apt-get install postgresql
```
#### 启动 postgresql 
```bash
root@kali:~# service postgresql start
root@kali:~# systemctl enable postgresql
Synchronizing state of postgresql.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable postgresql
Created symlink /etc/systemd/system/multi-user.target.wants/postgresql.service → /lib/systemd/system/postgresql.service.
```

#### 初始化数据库并重启
```bash
root@kali:~#  msfdb reinit
[i] Database already started
[+] Deleting configuration file /usr/share/metasploit-framework/config/database.yml
[+] Stopping database
[+] Starting database
[+] Creating database user 'msf'
为新角色输入的口令: 
再输入一遍: 
[+] Creating databases 'msf'
[+] Creating databases 'msf_test'
[+] Creating configuration file '/usr/share/metasploit-framework/config/database.yml'
[+] Creating initial database schema
/usr/share/metasploit-framework/vendor/bundle/ruby/2.7.0/gems/activerecord-4.2.11.1/lib/active_record/connection_adapters/abstract_adapter.rb:84: warning: deprecated Object#=~ is called on Integer; it always returns nil
root@kali:~# msfdb start
[i] Database already started
```
#### 启动 msfconsole 
```bash
root@kali:~# msfconsole 
```
#### 检查连接状态
```bash
msf5 > db_status
[*] Connected to msf. Connection type: postgresql.
```
#### 断开连接
```bash
msf5 > db_discomnect                                                                                                                                                                                                                       
[-] Unknown command: db_discomnect.  
```
#### 查看密码
```bash
msf5 > cat  /usr/share/metasploit-framework/config/database.yml 
```
#### 手动连接 db_connect username:password=@localhost/databasesname
```bash
msf5 > db_connect msf:Cqvf7sBFF6OwTZS0PNVA75czugvajjo65E9q+/qKfyc=@localhost/msf
Connected to Postgres data service: localhost/msf
```
