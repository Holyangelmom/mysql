# 常用sql

### 1、创建用户

_CREATE USER 'username'@'host' IDENTIFIED BY 'password';_

host可选值：localhost、IP、%（远程任意主机）

### 2、给用户授权

_GRANT privileges ON databasename.tablename TO 'username'@'host';_

privileges可选值：select、update、insert、delete等、all（所有权限）

databasename可选值：数据库名称、\*（所有数据库）

tablename可选值：表名称、\*（所有表）

WITH GRANT OPTION：允许该用户授权给其他用户授权

### 3、回收权限

_REVOKE privilege ON databasename.tablename FROM 'username'@'host';_

### 4、刷新权限

_flush privileges;_

若无权限刷新，则报错![](/assets/nnn.png)

### 5、修改字段名

_alter table man change oldName newName varchar\(32\) not null;_

### 6、增加字段

_alter table t\_org\_dict add column flag varchar\(1\);_

### 7、查询用户权限

_show grants for username;_

### 8、删除字段

alter table t\_organization drop colName;

### 9、查询某用户的权限

show grants for username;

