# 部署配置过程

1、解压

tar -zxvf mysql-5.6.33-linux-glibc2.5-x86\_64.tar.gz

![](/assets/aaa.png)

2、移动

mv mysql-5.6.33-linux-glibc2.5-x86\_64 /usr/local/mysql

3、添加mysql用户和组

groupadd mysql

useradd -g mysql mysql

4、修改文件夹权限

chown -R mysql mysql /usr/local/mysql

5、配置my.cnf

cd /usr/local/mysql

cp support-files/my-default.cnf /etc/my.cnf

![](/assets/bbb.png)

其中，配置描述如下：

basedir=/usr/local/mysql mysql根目录

datadir=/usr/local/mysql/data  mysql数据目录

user=mysql 目录所属用户

lower\_case\_table\_names=1 对大小写不敏感

6、安装

./scripts/mysql\_install\_db --user=mysql --datadir=/usr/local/mysql/data

7、配置开机启动

cd /usr/local/mysql

cp support-files/mysql.server  /etc/init.d/mysqld

chkconfig mysqld on

chkconfig --list\|grep mysqld

chmod 755 /etc/init.d/mysqld

![](/assets/ccc.png)

8、启动数据库

service mysqld start

9、配置mysql软连接

ln -s /usr/local/mysql/bin/mysql /usr/bin

10、设置root密码

/usr/local/mysql/bin/mysqladmin -u root password 'new\_password'

11、消除安全隐患

cd /usr/local/mysql/bin

./mysql\_secure\_installation

输入密码

![](/assets/ddd.png)

不改动root密码

![](/assets/eee.png)

删除匿名用户

![](/assets/fff.png)

允许root用户远程登录

![](/assets/ggg.png)

删除test数据库及其权限

![](/assets/hhh.png)

重新加载权限

![](/assets/iii.png)

12、设置编码

vim /etc/my.cnf

在\[mysqld\]下边设置

character-set-server=utf8

在\[client\]下边设置

default-character-set=utf8![](/assets/jjj.png)

查看编码

show variables like '%character%'

![](/assets/lll.png)

**可能出现的问题：**

**1、mysql不允许某用户远程登录**

![](/assets/mmm.png)

解决方法：

进入mysql命令行进行授权，允许root用户使用xxx密码通过远程主机访问：

（GRANT ALL PRIVILEGES ON dk.\* TO 'myuser'@'192.168.1.3' IDENTIFIED BY 'xxx' WITH GRANT OPTION;

允许myuser用户使用xxx密码在192.168.1.3主机上登录访问dk数据库）

GRANT ALL PRIVILEGES ON \*.\* TO 'root'@'%' IDENTIFIED BY 'xxx' WITH GRANT OPTION;

flush privileges;

**2、Caused by: java.sql.SQLException: Access denied for user 'root'@'hdp1' \(using password: YES\)**

