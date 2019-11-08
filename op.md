## 3. MySQL数据库的相关操作

<span id="top"></span>

- **[关于库的操作](#1-关于库的操作)**<br/>
- **[关于表的操作](#2-关于表的操作)**<br/>
- **[关于数据的操作](#3-关于数据的操作)**
	- [插入数据](#op01)
	- [更新数据](#op02)
	- [删除数据](#op03)
	- [查询数据](select.md)



 [返回](README.md)

### 1. 关于库的操作
---

+  **创建库** <span id="op1"></span>

		create database database_name;


&emsp;&emsp; data_name为库名， **命名规则：** 字母、数字、下划线、@#$。首字母不能是数字和$。不可以有空格和特殊字符。长度小于128位。

+  **查看库和选择库** <span id="op2"></span>


		#查看所有库
		show databases; 

		#选择库
		use database_name; 

		#查看选中库
		select database(); 

+ **删除库** <span id="op3"></span>

		drop database database_name; #删库




### 2. 关于表的操作
--- 


&emsp;&emsp;表是mysql数据库中一种很重要的对象，是组成数据库的基本元素，表是按照行、列的格式组织的，主要用来存储数据。


+	**创建表** <span id="op4"></span>

		create table table_name(
			列1 数据类型,
			列2 数据类型,
			列3 数据类型,
			...
		);


+	**查看表结构** <span id="op5"></span>


		#查看表结构
		desc table_name;

		#查看表详细定义
		show create table table_name; 
		show create table table_name\G # \G结尾可以使显示更美观

		#查看所有的表
		show tables; 

+	**删除表** <span id="op6"></span>

		drop table table_name; #删除表
+	**修改表** <span id="op7"></span>


		#修改表名
		alter table old_name rename to new_table_name;
		
	&emsp;**(1).给表增加字段**

		#在最后一个位置增加字段
		alter table table_name add 列名 数据类型;

		#在第一个位置增加字段
		alter table table_name add 列名 数据类型 first;

		#在指定位置添加字段
		alter table table_name add 新的列名 数据类型 after 列名;

	&emsp;**(2).删除字段**

		#删除某一列
		alter table table_name drop 列名;

	&emsp;**(3).修改字段**

		#修改字段数据类型 列名为要修改的列 数据类型为修改后的
		alter table table_name modify 列名 数据类型;

		#修改字段的名字
		alter table table_name change 旧列 新列 旧数据类型;

		#同时修改字段名和数据类型
		alter table table_name change 旧列 新列 新数据类型;



### 3. 关于数据的操作
---


+   **插入数据** <span id="op01"></span>

	 &emsp;**(1).插入表中部分列或所有列的数据**



			insert into table_name(列1,列2,列3,...,列n) values(值1,值2,值3,...,n);
		
			insert into table_name values(值1,值2,值3,...,n)



	 &emsp;**(2).一次插入多条所有列的数据**

			insert into table_name(列1,列2,,...,列n或所有列) values(值1~值n),(值1~值n)...;
			#值1到值n是所有列的值，不能少
		
			#例：一次插入三条数据
			insert into t1(name,id,age) # 或者"insert into t1"插入所有列
			values('xw',1001,20),
			  	('xh',1002,21),
			  	('ll',1003,20);

	 &emsp;**(3).往表中插入查询出的结果**

			insert into table_name(列1,列2,列3...) select 列_1,列_2,列_3... from table_name_1;
		
			#例：将t1表中查询出的结果插入到t2中
			insert into t2(id,name) select id,name frome t1;
			#说明：查询表t2中的id,name列并插入到t1的id,name列



+   **更新数据** <span id="op02"></span>

	 &emsp;**(1).更新特定数据**
	
			update table_name set 列1=值1,列2=值2... where 条件   #值为更新的数据值	
	
			#例：将表t1中id为1001的数据的name，age更新为zhangsan，40
			update t1 set name='zhangsan',age=40 where id=1001;
			
	 &emsp;**(2).更新所有数据** 全表更新
	
			update table_name set 列1=值1,列2=值2...;	
		

+  **删除数据** <span id="op03"></span>
	
	&emsp;**(1).删除特定数据**

			delete from table_name where 条件;

	&emsp;**(2).删除所有数据**

			delete from table_name;


+  [**查询数据**](select.md)





[回到顶部](#top)
	



					











