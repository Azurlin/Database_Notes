##  查询数据


[返回上一级](op.md)


[返回](README.md)


   >("[]"标注用户输入的内容)

### 1.单表数据查询


#### (1).简单数据查询

- **查询数据**

		select [列1,列2,列3...] from [表名];
		select * from [表名];

- **distinct避免重复数据查询**
		
		select distinct [列名] from [表名];


- **使用四则运算显示数据查询结果**
		
		select [表达式] from [表名];
		为显示查询结果的列重命名
		select [原列名] as [显示的新列名] from [表名];  #as可以省略


&emsp;例：

&emsp;原表t 



&emsp;&emsp;&emsp;![sd01](https://github.com/Azurlin/Database_Notes/blob/master/image/sd01.png?raw=true)


&emsp;查询结果


&emsp;&emsp;&emsp;![sd02](https://github.com/Azurlin/Database_Notes/blob/master/image/sd02.png?raw=true)

- **concat设置数据查询的显示格式**

		#concat()函数可以连接字符串
		select concat(ename,':',sal*12)  yearsal from t;

&emsp;例：

&emsp;&emsp;&emsp;![sd03](https://github.com/Azurlin/Database_Notes/blob/master/image/sd03.png?raw=true)



#### (2).条件数据查询

- **带关系运算符和逻辑运算符的条件数据查询**

	>mysql中的关系运算符:'>','>=','<','<=','=','!='(<>)
	逻辑运算符:and(&&),or(||),not(!)

		select [列1,列2...] from [表名] where [表达式]

		例:
		对于表t查询月薪在1000-1800的职位
		select job,sal from t where sal>1000 && sal<1800;


- **between and关键字**

		select [列1,列2...] from [表名] where [列名] between [数值] and [数值]	
		
		例:
		对于表t查询月薪在1000-1800的职位</br>
		select job,sal from t where sal between 1000 and 1800;
		
		查询月薪不在1000-1800的职位 between前加'not'
		select job,sal from t where sal not between 1000 and 1800;

		
	
	![sd04]()



- **is null关键字**

	作用:用来实现判断字段的数值是否为空的条件查询

		select [列1,列2...] from [表名] where [列1,列2...] is null


		例：
		查询t表中提成为空的员工
		select ename,comm from t where comm is null;

		查询t表中提成不为空的员工
		select ename,comm from t where comm is not null;
		或select ename,comm from t where not comm is  null;

	![sd05]()


- **in关键字**
- **like关键字**

#### (3).排序数据查询
#### (4).限制数据查询
#### (5).统计函数和分组数据查询


### 2.多表数据查询