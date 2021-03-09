---

layout: post

title:  linux下mariadb数据库的安装

subtitle: centos7安装 mariadb数据库

date: 2021-03-09

author: BlackFrog-hub

header-img: img/mysql_bg.jpg

catalog:  true

tags:
  - Linux
  - mariadb
  - centos
  
---

- 首先更新源 `yum update` &&`yum upgrade`
 ![](http://blackfrog.top/img/mariadb_install_1.png)
 
- 安装mariadb和mariadb-server `yum install -y mariadb mariadb-server`
  ![](http://blackfrog.top/img/mariadb_install_2.png)
  
- 启动mariadb `systemctl start mariadb `  停止`systemctl start mariadb` 
  ![](http://blackfrog.top/img/mariadb_install_3.png)
    
- 查看 `netstat -nap | grep 3306` 3306为默认端口
  ![](http://blackfrog.top/img/mariadb_install_4.png)       
        
- 设置开机自启 `systemctl enable mariadb`
  ![](http://blackfrog.top/img/mariadb_install_5.png)
  
- 登录数据库 `mysql -u root -p`
  ![](http://blackfrog.top/img/mariadb_install_6.png)
  
- 因为mysql数据库默认没有密码，所以需要修改密码，首先`use mysql`进入mysql库下，修改密码`update user set password=password("123456") where user='root';`
  ![](http://blackfrog.top/img/mariadb_install_7.png)

- 查看是否成功 `select user,password,host from user;`
  ![](http://blackfrog.top/img/mariadb_install_8.png)

- 如果发现修改之后还能无口令登入，则执行` flush privileges;`让修改生效
  ![](http://blackfrog.top/img/mariadb_install_9.png)

- 退出数据库，再次登入，输入正确口令登录成功
  ![](http://blackfrog.top/img/mariadb_install_10.png)

