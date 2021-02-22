---
layout:   post
title:    kali_linux更新源发生release文件过期解决
subtitle:   kali_linux更新源时间错误
date:   2021-02-21
author:   BlackFrog-hub
header-img: img/kali_bg.jpg
catalog: true
tags:
    - kali
    - Linux
---


##### 今天更新kali源的时候报如下错误：Release 文件过期，仓库更新不会被应用

```bash
root@kali:~# apt-get update
获取:1 http://dl.google.com/linux/chrome/deb stable InRelease [1,811 B]
获取:2 http://mirrors.aliyun.com/kali kali-rolling InRelease [30.5 kB]                                                                                                                                                                    
正在读取软件包列表... 完成          
E: http://dl.google.com/linux/chrome/deb/dists/stable/InRelease 的 Release 文件已经过期(已经过期了 3小时 31分 38秒)。该仓库的更新将不会应用。
E: http://mirrors.aliyun.com/kali/dists/kali-rolling/InRelease 的 Release 文件已经过期(已经过期了 19小时 45分 47秒)。该仓库的更新将不会应用。
```

- 试了第一种更新签名依然无法更新
    
```bash
root@kali:~# wget -q -O - https://archive.kali.org/archive-key.asc | apt-key add
OK
root@kali:~# apt-get update
获取:1 http://dl.google.com/linux/chrome/deb stable InRelease [1,811 B]
获取:2 http://mirrors.aliyun.com/kali kali-rolling InRelease [30.5 kB]                                                                                                                                                                    
正在读取软件包列表... 完成                                                                                                                                                                                                                
E: http://dl.google.com/linux/chrome/deb/dists/stable/InRelease 的 Release 文件已经过期(已经过期了 3小时 22分 55秒)。该仓库的更新将不会应用。
E: http://mirrors.aliyun.com/kali/dists/kali-rolling/InRelease 的 Release 文件已经过期(已经过期了 19小时 37分 9秒)。该仓库的更新将不会应用。
```
- 第二种更新签名依然无法更新

```bash
root@kali:~# apt-key adv --keyserver hkp://keys.gnupg.net --recv-keys 7D8D0BF6
Executing: /tmp/apt-key-gpghome.uuX2k5fh44/gpg.1.sh --keyserver hkp://keys.gnupg.net --recv-keys 7D8D0BF6
gpg: 密钥 0C70FD6B7D8D0BF6：公钥 “Totally Legit Signing Key <mallory@example.org>” 已导入
gpg: 密钥 ED444FF07D8D0BF6：“Kali Linux Repository <devel@kali.org>” 未改变
gpg: 处理的总数：2
gpg:               已导入：1
gpg:              未改变：1
root@kali:~# wget -q -O - https://archive.kali.org/archive-key.asc | apt-key add
OK
root@kali:~# apt-get update
获取:1 http://mirrors.aliyun.com/kali kali-rolling InRelease [30.5 kB]
获取:2 http://dl.google.com/linux/chrome/deb stable InRelease [1,811 B]                                                                                                                                                                   
正在读取软件包列表... 完成                                                                                                                                                                                                                
E: http://mirrors.aliyun.com/kali/dists/kali-rolling/InRelease 的 Release 文件已经过期(已经过期了 19小时 36分 25秒)。该仓库的更新将不会应用。
E: http://dl.google.com/linux/chrome/deb/dists/stable/InRelease 的 Release 文件已经过期(已经过期了 3小时 21分 52秒)。该仓库的更新将不会应用。
```

- 最后了解到是有可能是时间问题，于是查看了系统时间和硬件时间
    
```bash
root@kali:~# date
2021年 02月 18日 星期四 11:49:32 EST
root@kali:~#  hwclock --show
2021-02-18 11:50:28.803209-05:00
```
- 果然是时间与当前时间不一致导致的问题，于是安装NTPdate并查看是否安装成功

```bash
root@kali:~# apt-get install ntpdate
root@kali:~# ntpdate
usage: ntpdate [-46bBdqsuv] [-a key#] [-e delay] [-k file] [-p samples] [-o version#] [-t timeo] server ...
```
- 对NTP服务进行如下配置

- Linux系统时间同步：让当前服务器同步到网络时间来更新当前服务器的时间。如让当前服务器时间同步到ntp1.aliyun.com
    
```bash
root@kali:~# ntpdate ntp1.aliyun.com
21 Feb 21:40:47 ntpdate[8317]: step time server 120.25.115.20 offset +294167.553122 sec
```
- Linux硬件时间的同步：修改服务器硬件时间映射到我们系统的时间

    root@kali:~# hwclock --systohc
    root@kali:~# hwclock -w
    
- 查看时间是否同步，结果都显示为当前的internet时间

```bash
  root@kali:~# date
  2021年 02月 21日 星期日 21:41:43 EST
  root@kali:~#  hwclock
  2021-02-21 21:41:57.962729-05:00
```
- 再次执行更新
    
```bash
root@kali:~# apt-get update
获取:1 http://dl.google.com/linux/chrome/deb stable InRelease [1,811 B]
获取:2 http://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1,083 B]
获取:3 http://mirrors.aliyun.com/kali kali-rolling InRelease [30.5 kB]                                                                                                                                                                    
获取:4 http://mirrors.aliyun.com/kali kali-rolling/non-free Sources [129 kB]                                                                                                                                                              
获取:5 http://mirrors.aliyun.com/kali kali-rolling/main Sources [14.0 MB]                                                                                                                                                                 
获取:6 http://mirrors.aliyun.com/kali kali-rolling/main amd64 Packages [17.7 MB]                                                                                                                                                          
获取:7 http://mirrors.aliyun.com/kali kali-rolling/non-free amd64 Packages [205 kB]                                                                                                                                                       
已下载 32.1 MB，耗时 21秒 (1,545 kB/s)                                                                                                                                                                                                    
正在读取软件包列表... 完成
```
#### 完成 ！！！
