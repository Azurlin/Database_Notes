## MySQL安装
##### 1.下载并解压MySQL安装包<br/>
 &emsp; &emsp; **[mysql-8.0.18-winx64](https://dev.mysql.com/downloads/mysql/)**

##### 2.启动MySQL服务<br/>
&emsp; &emsp; 打开cmd 进入mysql安装目录在bin目录下输入 **mysqld --initialize --console**<br/>
&emsp; &emsp; 执行成功会打印初始默认用户密码

 ![ini1](https://github.com/Azurlin/Database_Notes/blob/master/image/ini1.png?raw=true)

&emsp; &emsp; root@localhost:后面的就是初始密码

##### 3.启动MySQL

&emsp; &emsp; 打开另一个命令行 输入**mysql -h hostname -u root -p** 启动MySQL<br/>
 ![si1](https://github.com/Azurlin/Database_Notes/blob/master/image/si1.png?raw=true)<br/>
&emsp; &emsp; 出现此错误提示可以试试用 **mysql -u root -h 127.0.0.1 -p**启动<br/>
 