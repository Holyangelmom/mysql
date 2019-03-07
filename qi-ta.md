# 其他问题

### 目录

1. win7启动mysql
2. 导出
3. 导出sql结果到文件
4. 查看function定义

### 1、win7启动mysql

_net start\|stop\|restart\| mysql_

### 2、导出

导出数据库所有表结构及数据

_mysqldump -uroot -pdbpasswd  dbname &gt;db.sql;_

导出数据库所有表结构

_mysqldump -uroot -pdbpasswd -d dbname &gt;db.sql;_

导出某张表的结构及数据

_mysqldump -uroot -pdbpasswd dbname tablename&gt;db.sql;_

导出某张表的结构

_mysqldump -uroot -pdbpasswd -d dbname tablename&gt;db.sql;_

### 3、导出sql结果到文件

进入mysql命令行，查看变量指定的文件夹。

show variables like '%secure%';

![](/assets/ooo.png)

检查是否存在该文件夹/var/lib/mysql-files，若不存在则创建，并赋权给mysql用户。

执行sql

select \* from tm\_table\_info into outfile "/var/lib/mysql-files/test.sql" fields terminated by ',' lines terminated by '\r\n';

### 4、查看function定义

show create function functionName;

