##  查询数据
<span id="top"></span>

- **[单表查询](#h01)**
	
	- [简单数据查询](#select01)
	- [条件数据查询](#select02)
	- [排序数据查询](#select03)
	- [限制数据查询](#select04)
	- [统计函数](#select05)
	- [分组数据查询](#select06)

- **[多表查询](#h02)**

	- [内连接查询](#select07)
	- [外连接查询](#select08)
	- [子查询](#select09)


[返回上一级](op.md)


[返回](README.md)


   >("[]"标注输入的内容)

### 1.单表数据查询 <span id="h01"></span>



#### (1).简单数据查询 <span id="select01"></span>



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


[回到顶部](#top)


#### (2).条件数据查询 <span id="select02"></span>



- **带关系运算符和逻辑运算符的条件数据查询**

	>mysql中的关系运算符:'>','>=','<','<=','=','!='(<>)
	逻辑运算符:and(&&),or(||),not(!)

		select [列1,列2...] from [表名] where [表达式];

		例:
		对于表t查询月薪在1000-1800的职位
		select job,sal from t where sal>1000 && sal<1800;


- **between and关键字**

		select [列1,列2...] from [表名] where [列名] between [数值] and [数值];	
		
		例:
		对于表t查询月薪在1000-1800的职位</br>
		select job,sal from t where sal between 1000 and 1800;
		
		查询月薪不在1000-1800的职位 between前加'not'
		select job,sal from t where sal not between 1000 and 1800;

		
	
	![sd04]()



- **is null关键字**

	作用：用来实现判断字段的数值是否为空的条件查询

		select [列1,列2...] from [表名] where [列1,列2...] is null;


		例：
		查询t表中提成为空的员工
		select ename,comm from t where comm is null;

		查询t表中提成不为空的员工
		select ename,comm from t where comm is not null;
		或select ename,comm from t where not comm is  null;

	![sd05]()


- **in关键字**

	作用：用来实现判断字段的值是否在指定集合中的条件查询

		select [列1,列2...] from [表名] where [列] in([值1,值2...]);
		#f字段的值是否在集合值1~值n中
		
		例：
		查询表t中员工编号为7521,7782,7566,7788的员工
		select empno,ename from t where empno in(7521,7782,7566,7788);
		
		查询表t中员工编号不是7521,7782,7566,7788的员工
		select empno,ename from t where empno not in(7521,7782,7566,7788);

	>in使用注意:在使用in时，查询的集合中如果存在null，不会影响结果<br/>
	>在使用not in时，查询的集合中如果存在null，则不会有任何查询结果。


	![sd06]()   ![sd07]()


- **like关键字**

	作用：用于做模糊匹配的数据查询

	
	>模糊匹配条件需要mysql提供的通配符,通配符要写在''中<br/>
	>'_':能匹配单个字符<br/>
	>'%':能匹配任意长度的字符，可以是0个到多个

		select [列1,列2...] from [表名] where [列名] like [模糊匹配条件];

		例:
		查询t表中名字以a开头的所有员工
		select ename from t where ename like 'a%';


[回到顶部](#top)


#### (3).排序数据查询 <span id="select03"></span>



使用order by按照某列进行排序


- **按照单字段排序**

	>关键字：asc:升序&emsp;desc:降序

		select [列1,列2...] from [表名] where [条件] order by [列名] [asc/desc];
		
		例：
		查询t表中所有员工,同时按照工资升序排列显示查询结果
		select * from t order by sal asc;


	![sd08]()




- **按照多字段排序**

		select [列1,列2...] from [表名] order by [列名] [关键字],[列名] [关键字],...,[列名] [关键字];
		#用','隔开
		
		例：
		查询t表中所有员工,同时按照工资升序,入职时间降序排列显示查询结果
		select * from t order by sal asc,hiredate desc;


	![sd09]()


[回到顶部](#top)


#### (4).限制数据查询 <span id="select04"></span>



限制查询结果的数量

- **指定初始位置**(默认从第一条数据开始)

		select [列1,列2...] from [表名] where [条件] limit [初始位置],[显示数量];



[回到顶部](#top)


#### (5).统计函数和分组数据查询 



- **mysql提供的统计函数** <span id="select05"></span>
	
	>count()函数:统计表中数据的条数<br/>
	>avg():计算字段平均值<br/>
	>sum():计算字段总和<br/>
	>max():查询字段最大值<br/>
	>min():查询最小值

		select 函数([列名]) from [表名] where [条件];



	count(*) 统计全部数据的数量<br/>
	count(列名) 统计某列数据数量，过滤空值

		例：
		查询表t数据条数		
		select count(*) as number from t;
		
		查询表t有奖金的员工
		select count(comm) as comm from t where not comm=0;
		
	![sd10]() ![sd11]()


	avg(列名) 一种用法，在具体统计时会忽略空值

		例:
		统计表t有奖金员工的平均值
		select avg(comm) as average from t;

	sum(列名) 对指定字段计算总和，忽略空值


		例:
		统计表t月薪总和
		select sum(sal) as sumvalue from t;


	max(列名),求最大值忽略空值
	min(列名),求最小值忽略空值


		例：
		统计表t最高工资和最低工资
		select max(sal) maxsal,min(sal) minsal from t;

- **分组数据查询** <span id="select06"></span>

	通常与统计函数一起使用

 	

	- **group by与group_concat()函数**


			select [列1,列2...] from [表名] where [条件] group by [列名];
	
			例:
			查询t表各部门中员工人数
			select count(ename),deptno from t group by deptno;
	
			查询t表按照部门号对所有员工分组，同时显示每组中员工人数
			select count(ename),deptno,group_concat(ename) from t group by deptno;


		![sd12]() ![sd13]()

	

	- **根据多字段分组查询**

			select [函数],... from [表名] where [条件] group by [列1,列2...];
		

			例：
			查询表t，首先按照部门号对所有员工分组，然后按照生日对每组的员工再分组,同时显示人数
			select deptno,hiredate,group_concat(ename),count(ename) from t group by deptno,hiredate;  

		![sd12]()

	- **使用having子句进行条件查询**


			select [列1,列2...] from [表名] group by [列名] having [条件];

	

[回到顶部](#top)



### 2.多表数据查询 <span id="h02"></span>


	

#### (1).内连接查询 <span id="select07"></span>

	
- **自连接**

	是内连接查询中一种特殊的等值连接,所谓的自连接就是指表与其自身进行连接

		
		
		例：
		查询t表每一个员工姓名、职位和其上级的姓名
		select e.ename,e.job,m.ename from t e inner join t m on e.mgr=m.empno;


- **等值连接**
		
		
		select [构建的表1].[列名],... from [表1] [构建表1] inner join [表2] [构建表2] on [关联条件];

		等值连接是在关键字on后匹配的条件

		例:
		查询每个员工的姓名编号和其上级的姓名,部门名,部门位置
			1).构建关联的表
				表t e 员工表
				表td d 部门表
				表t m 上级表
			2).关联的条件
				员工表和部门表的关联条件 e.deptno=d.deptno
				员工表和上级表的关联条件 e.mgr=m.empno
			
		select e.ename,e.empno,m.ename,d.dname,d.loc 
		from t e 
		inner join td d on e.deptno=d.deptno
		inner join t m  on e.mgr=m.empno;
		

- **不等值连接**


	在关键字on后使用其他关系运算符


[回到顶部](#top)
		


#### (2).外连接查询 <span id="select08"></span>


>特点:查询结果至少是一个表的所有记录

- **左外连与右外连**

		select [列1,列2...] from [表1] left/right outer join [表2] on [条件];
	
	 	左外连：
		from [表1] left outer join [表2];

		表1为驱动表,表2为匹配表
		查询结果是驱动表表1的所有记录
	
	 	右外连：
		from [表1] right outer join [表2];

		表2为驱动表,表1为匹配表
		查询结果是驱动表表2的所有记录

		例:
		左外连 查询每个员工的姓名、职位和领导的姓名
		select e.ename,e.job,d.dname from t e left outer join td d on e.deptno=d.deptno;


#### (3).子查询 <span id="select09"></span>

>用来实现多表查询 在子查询中可以包含in any all等关键字,也可以包含比较运算符，比较灵活

	
- **在where、in子句中的子查询**


		例:
		查询表t月薪高于smith的信息
		select * from t where sal>(select sal from t where ename='smith');
		
		select * from t in(...);
		

- **any关键字**

	>=any:功能与in相同<br/>
	>\>any:比子查询返回的数据中最小的还要大的<br/>
	><any:比子查询返回的数据最大的还要小的数据<br/>
	
		例:
		查询员工表中员工姓名和工资,这些员工的工资不低于职位为manager的工资
		s1:先查询员工表中职位为manager的工资
			select sal from t where job='manager';
		s2:查询工资不低于上述结果的
			select ename,sal from t where sal>any(select sal from t where job='manager');
		
 




  ![sd01]()![sd15](https://raw.githubusercontent.com/Azurlin/Database_Notes/master/image/td.png)



[回到顶部](#top)
