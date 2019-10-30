### 3. MySQL数据库的相关操作

### &emsp;**(1).关于库的操作** 

+  **创建库：** 

		create database database_name;
&emsp;&emsp; data_name为库名，**命名规则：**字母、数字、下划线、@#$。首字母不能是数字和$。不可以有空格和特殊字符。长度小于128位。

+  **查看库和选择库**


		#查看所有库
		show databases; 

		#选择库
		use database_name; 

		#查看选中库
		select database(); 

+ **删除库**

		drop database database_name; #删库


### &emsp;**(2).关于表的操作** 
&emsp;&emsp;表是mysql数据库中一种很重要的对象，是组成数据库的基本元素，表是按照行、列的格式组织的，主要用来存储数据。

<<<<<<< HEAD
=======
&emsp;&emsp;例：
李四 1002 26 95
张三 1001 25 100

&emsp;&emsp;以表的方式存储：


name|id|age|score
	-|-|-|-|
李四|1002|26|95
张三|1001|25|100
>>>>>>> 85a9fc83058288135e4fa215178ba7f1b667f895

+	**创建表**

		create table table_name(
			列1 数据类型,
			列2 数据类型,
			列3 数据类型,
			...
		);
创建成功提示Query OK

+	**查看表结构**

		#查看表结构
		desc table_name;

 		#查看表详细定义
		show create table table_name; 
		show create table table_name\G # \G结尾可以使显示更美观

		#查看所有的表
		show tables; 

+	**删除表**

		drop table table_name; #删除表
+	**修改表**
<<<<<<< HEAD


		#修改表名
		alter table old_name rename[to] new_table_name;
		
	&emsp;***给表增加字段***

		#在最后一个位置增加字段
		alter table table_name add 列名 数据类型;

		#在第一个位置增加字段
		alter table table_name add 列名 数据类型 first;

		#在指定位置添加字段
		alter table table_name add 新的列名 数据类型 after 列名;

	&emsp;***删除字段***

		#删除某一列
		alter table table_name drop 列名;

	&emsp;***修改字段***

		#修改字段数据类型 列名为要修改的列 数据类型为修改后的
		alter table table_name modify 列名 数据类型;

		#修改字段的名字
		alter table table_name change 旧列 新列 旧数据类型;

		#同时修改字段名和数据类型
		alter table table_name change 旧列 新列 新数据类型;
=======
>>>>>>> 85a9fc83058288135e4fa215178ba7f1b667f895
