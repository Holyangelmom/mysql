# 常用函数

### 1、查看function定义

_show create function functionName;_

### 2、IFNULL函数

##### （1）函数定义

IFNULL\(expr1,expr2\)

如果expr1不是NULL，IFNULL\(\)返回expr1，否则它返回expr2。IFNULL\(\)返回一个数字或字符串值

##### （2）使用样例

select ifnull\(max\(ele\_id\)+1,1\) from oadb.t\_\_query

