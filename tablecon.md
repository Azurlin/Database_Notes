## 5. 表的约束

 [返回](README.md)

#### 1. **not null** 非空约束 

&emsp;&emsp;约束该列不能为空

		create table t1(
			a int not null,
			b int
		);
		insert into t1(a,b) values(3,5);
		select * from t1;


#### 2. **default** 设置字段的默认值

		create table t2(
			a varchar(10),
			b varchar(10) default 'hello'
		);
		insert into t2(a) values('qwer'); # b列有默认值hello
		insert into t2(b) values('rewq'); # a列无默认值为NULL
		select * from t2;

![tablecon02](https://github.com/Azurlin/Database_Notes/blob/master/image/tablecon02.png?raw=true)



		

#### 3. **unique key(uk)** 唯一性约束

&emsp;&emsp;只能出现一次

		create table t3(
			a int unique key
		);
		insert into t3(a) values(10);
		select * from t3;
![tablecon03](https://github.com/Azurlin/Database_Notes/blob/master/image/tablecon03.png?raw=true)


&emsp;&emsp;可见10出现过一次，无法再次插入

#### 4. **primary key(pk)** 主键约束(唯一、不为空)

- 单字段设置主键

		create table t4(
			a int primary key		
		);
		insert into t4(a) values(1); # 可以
		insert into t4(a) values(1); # 报错，不符合唯一
		insert into t4(a) values(null); # 报错，不能为空
		select * from t4;

- 多字段设置主键

		create table t5(
			a int,
			b int,
			c int,
			constraint pk_name primary key(a,b)
		); #一次设置多个主键

#### 5. **auto_increment** 字段自动增加