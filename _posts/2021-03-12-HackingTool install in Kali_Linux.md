---

layout: post

title:  HackingTool install in Kali_Linux
subtitle: hackingtool install in kali_linux

date: 2021-03-12

author: BlackFrog-hub

header-img: img/hackingtool_bg.png

catalog:  true

tags:
  - Linux
  - hackingtool
  - tools
  - kali
  - linux
  
---


###  HackingTool是一款针对于渗透测试的多合一渗透测试套件，集成了许多黑客工具

#### HackingTooL Menu

- 匿名隐藏工具
- 信息收集工具
- 密码攻击工具
- 无线攻击工具
- SQL注入工具
- 网络钓鱼攻击工具
- Web攻击工具
- 后渗透工具
- 信息取证工具
- Payload创建工具
- 漏洞利用框架
- 逆向工程工具
- DDOS攻击工具
- 远程管理工具(RAT)
- XSS攻击工具
- Steganograhy工具
- 其他工具
  - 社交媒体暴力破解
  - Android骇客工具
  - IDN同形异义词攻击
  - 电子邮件验证工具
  - 哈希破解工具
  - WiFi取消验证
  - 社交媒体查找器
  - payload注入器
  - 网页抓取
  - 混合工具



### HackingTool安装

- HackingTool基于Python开发所以确保Linux环境下已经安装了Python3+，执行`git clone + url`download在本地,并确定Python环境
![](http://blackfrog.top/img/hackingtool_git.png)

- 赋予775权限，并进入该目录
![](http://blackfrog.top/img/hackingtool_1.png)

- 先确定是否安装了pip3，执行`sudo pip3 install -r requirement.txt`

![](http://blackfrog.top/img/hackingtool_2.png)

- 将`install.sh`中`google`改为`baidu`,基于国内的环境懂得都懂

![](http://blackfrog.top/img/hackingtool_3.png)

- 执行`./install.sh`转到安装界面输入`1`进行安装

![](http://blackfrog.top/img/hackingtool_4.png)

- 出现了`Installation Failed!!!` 顿时不详的预感！！！

![](http://blackfrog.top/img/hackingtool_5.png)

- 果然报错无法启动，入坑开始

![](http://blackfrog.top/img/problem_1.png)

- 通过了解应该是git的问题，所以重新编译Git安装，首先执行`sudo apt-get install build-essential fakeroot dpkg-dev -y`

![](http://blackfrog.top/img/problem_2.png)

- 再执行`sudo apt-get build-dep git -y`

![](http://blackfrog.top/img/problem_3.png)

- 执行`sudo apt-get install libcur14-openssl-dev -y`报错，出现了一个熟悉的报错

![](http://blackfrog.top/img/problem_4.png)

- 执行'apt-get update'更新报错,果断换源再次执行`apt-get update` && `apt-get upgrade`更新成功

![](http://blackfrog.top/img/problem_5.png)

- 再次安装hackingtool，成功！！！因为源的问题绕自己给自己挖了一个坑，还是应该要有执行更新的习惯QAQ

![](http://blackfrog.top/img/problem_6.png)

- HackingTool安装成功界面

![](http://blackfrog.top/img/hackingtool_6.png)

![](http://blackfrog.top/img/hackingtool_7.png)

![](http://blackfrog.top/img/hackingtool_8.png)

![](http://blackfrog.top/img/hackingtool_9.png)

![](http://blackfrog.top/img/hackingtool_10.png)

![](http://blackfrog.top/img/hackingtool_11.png)
