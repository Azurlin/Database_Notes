## MySQL安装

 [返回](README.md)
##### 1.下载并解压MySQL安装包<br/>
 &emsp; &emsp; **[mysql-8.0.18-winx64](https://dev.mysql.com/downloads/mysql/)**

##### 2.启动MySQL服务<br/>
&emsp; &emsp; 打开cmd 进入mysql安装目录在bin目录下输入 **mysqld --initialize --console**<br/>
&emsp; &emsp; 执行成功会打印初始默认用户密码

 ![ini1](https://github.com/Azurlin/Database_Notes/blob/master/image/ini1.png?raw=true)

&emsp; &emsp; root@localhost:后面的就是初始密码<br/>
&emsp; &emsp; 重置密码：** ALTER USER USER() IDENTIFIED BY '新的密码';**<br/>
&emsp; &emsp; 之后直接用**mysqld --console**启动服务

##### 3.启动MySQL

&emsp; &emsp; 打开另一个命令行 输入**mysql -h 用户名 -u root -p** 启动MySQL<br/>
&emsp; &emsp; 或者使用 **mysql  -h 127.0.0.1 -u root  -p 和mysql  -h localhost -u root  -p**启动<br/>
 