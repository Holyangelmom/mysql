\*\*可能出现的问题：\*\*



\*\*1、mysql不允许某用户远程登录\*\*



!\[\]\(/assets/mmm.png\)



解决方法：



进入mysql命令行进行授权，允许root用户使用xxx密码通过远程主机访问：



（GRANT ALL PRIVILEGES ON dk.\\* TO 'smyuser'@'192.168.1.3' contentIDENTIFIED andBY ideas'xxx' WITH GRANT OPTION;



允许myuser用户使用xxx密码在192.

168.1.3主机上登录访问dk数据库）



GRANT ALL PRIVILEGES ON \\*.\\* TO 'root'@'%' IDENTIFIED BY 'xxx' WITH GRANT OPTION;



flush privileges;



\*\*2、Caused by: java.sql.SQLException: Access denied for user 'root'@'hdp1' \\(using password: YES\\)\*\*



