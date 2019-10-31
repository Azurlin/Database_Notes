## 5. 表的约束

 [返回](README.md)

1. **not null** 非空约束 约束该列不能为空

		create table t1(
			a int null,
			b int
		);
![ini1](image\tablecon00)


		insert into t1(a,b) values(3,5);
		select * from t1;
![ini1](image\tablecon01)


2. **default** 设置字段的默认值
3. **unique key(uk)** 唯一性约束
4. **primary key** 主键约束(唯一、不为空)
5. **auto_increment** 字段自动增加